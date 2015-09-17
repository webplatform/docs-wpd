---
title: 'Create a public download archive repository stored directly in DreamObjects'
uri: 'WPD:Infrastructure/procedures/Create a public download archive repository stored directly in DreamObjects'

---
**Status: INCOMPLETE**, *WebPlatform GitHub operations issue tracker*, at **[webplatform/ops\#121](https://github.com/webplatform/ops/issues/121)**

The purpose is twofold:

1.  Allow download of packages in a public repository so that anybody could download archives the infrastructure generates for its maintenance
2.  Leverage our provider infrastructure so we do not move around archives but fetch them from a common location

This would be ideal since we already use a Swift endpoint to store our backups, we could also have it store our web application and Debian (.deb) packages too.

## SCRATCHPAD

It assumes:

1.  You have a Swift compatible Object storage
2.  You have a Varnish frontend and can add your own VCL settings

### Create a bucket

Make sure the bucket has defaults to public. In this example we’ll call the bucket "apt", along with a Swift key of the name "wpd-assets:wpd-assets-user" installed.

Also, the bucket will have an alias to be called as "apt.webplatform.org" in DreamObjects, but our DNS won’t point to it directly.

Instead, it’ll use Varnish as a frontend to Proxy the requests for us and keep a cache for us in case the DreamObjects becomes unavailable.

### Install your bucket credentials in your shell environment

Generally in \`/etc/profile.d/\*.sh\`

     cat /etc/profile.d/swift.sh
     # WebPlatform.org uses DreamHosts and their cloud services DreamObjects,
     # here’s how their config looks like.
     export ST_AUTH="https://objects.dreamhost.com:443/auth"
     export ST_USER="wpd-assets:wpd-assets-user"
     export ST_KEY="..."

### Configure from the Swift API to allow the public to read your bucket

This requires python-swift client and your shell environment variables installed. If you havent´t restarted a shell session, you can source the shell environment variables yourself like so:

     source /etc/profile.d/swift.sh

Send the following commands:

     swift post -r '.r:*' apt

Technically the [OpenStack Swift documentation](http://docs.openstack.org/user-guide/content/managing-openstack-object-storage-with-swift-cli.html), at "Create static website" asks to do the following, but we´ll make Varnish do it for us.

     swift post -m 'web-index: index.html' apt
     swift post -m 'web-listings: true' apt

### Configure your Varnish frontend

In the case of WebPlatform, we are using Fastly as a Varnish frontend server.

All you need to do on the DNS side is to have a CNAME point to Fastly’s edges servers like so:

     ; In webplatform.org bind9 zone file
     apt.webplatform.org IN CNAME webplatform.map.fastly.net.

In Fastly, create a service with the following details:

-   Host: apt.objects.dreamhost.com
-   Port: 443

Once created, adjust the service configuration, with the following:

Note that its in YAML here by habit of the author and isn’t copy-pasateable, the VCL will be below:

     Domains:
       - apt.webplatform.org
     Hosts:
       Backends:
         - Address: apt.objects.dreamhost.com
           Port: 443
           Shielding: (anything goes here)
       Settings:
         Default Settings:
           Default Host: apt.objects.dreamhost.com
         Request Settings:
           - Default host: apt.objects.dreamhost.com
           - X-Forwarded-For: Append
           - Max stale age: 3600
           - Force SSL: Yes
         Content:
           Headers:
             - Type/Action: Request Set
               Destination: url
               Source: "/index.html"
               Request Conditions:
                 - Apply If: req.request ~ "GET" && req.url ~ "^/$"
            - Type/Action: Request Delete
              Destination: http.cookie
              Ignore If Set: Yes


 ... should generate a similar VCL configuration:

```
  sub vcl_recv {
  #FASTLY recv

     if (!req.http.Fastly-SSL) {
       error 801 "Force SSL";
     }

     if (!req.http.Fastly-FF) {
       if (req.http.X-Forwarded-For) {
         set req.http.Fastly-Temp-XFF = req.http.X-Forwarded-For ", " client.ip;
       } else {
         set req.http.Fastly-Temp-XFF = client.ip;
       }
     } else {
       set req.http.Fastly-Temp-XFF = req.http.X-Forwarded-For;
     }

     set req.grace = 3600s;
     set req.http.host = "apt.objects.dreamhost.com";

     # Remove ANY cookies, we dont need them at all!
     remove req.http.Cookie;
     # Request Condition: If no file requested, make DirectoryIndex ish Prio: 10
     if( req.request ~ "GET" && req.url ~ "^/$" ) {
        # Header rewrite to get our own hardcoded directory index file.
        # ... anyway we change directory contents very rarely.
        set req.url = "/index.html";
     }
  }

  sub vcl_error {
  #FASTLY error

    if (obj.status == 801) {
       set obj.status = 301;
       set obj.response = "Moved Permanently";
       set obj.http.Location = "https://" req.http.host req.url;
       synthetic {""};
       return (deliver);
    }
  }
```
