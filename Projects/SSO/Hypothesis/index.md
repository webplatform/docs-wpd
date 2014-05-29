= Hypothes.is =

Taking notes

== TODO ==

=== Adjust h.ini ===
<syntaxhighlight>
commit 09c8dce49ed6a9dcb1378a0e7ffb38787e2f8716
Author: Randall Leeds <tilgovi@hypothes.is>
Date:   Wed Apr 30 17:44:38 2014 -0700

    Swith to AuthTktAuthenticationPolicy
    
    Switching back from SessionAuthenticationPolicy to decouple sessions
    and authentication; increase deployment interoperability; and provide
    the groundwork for multiple signin.

diff --git a/production.ini b/production.ini
index 3f5dd26..fc31f6f 100644
--- a/production.ini
+++ b/production.ini
@@ -1,6 +1,13 @@
 [app:main]
 use: egg:h
 
+# Authentication
+#
+# If authentications must be shared across servers or persisted across server
+# reloads then this value should be set to a random 64-character string.
+# Keep this value secure!
+#auth.secret=
+
 # API configuration
 #
 # Customize the key or leave it as the default. If the key is present without

commit 5174d1684a785e2d99a53281bbf5e8e641327d5e
Author: Randall Leeds <tilgovi@hypothes.is>
Date:   Fri Apr 25 13:28:41 2014 -0700

    Refactor dependencies at startup
    
    Avoid explicit `config.commit()` calls by refactoring the way we load
    horus and our own dependencies.
    
    - Lift all horus overrides to be explicit in the h package include.
    - Have h.views take care of more core imports to get the rendering
      system running. The idea is to make it easier for scripting and
      integrating only our views.
    - Only use deform_bootstrap for template paths so it doesn't pollute the
      widget resource registry with the new load ordering.

diff --git a/production.ini b/production.ini
index 34c4cad..3f5dd26 100644
--- a/production.ini
+++ b/production.ini
@@ -50,12 +50,13 @@ mail.default_sender: "Annotation Daemon" <no-reply@localhost>
 
 # Include any deployment-specific pyramid add-ons here
 pyramid.includes:
-   deform_bootstrap
-   pyramid_deform
-   pyramid_mailer
+    pyramid_deform
+    pyramid_mailer
 
 # Change or append to override templates
-pyramid_deform.template_search_path: h:templates/deform
+pyramid_deform.template_search_path:
+    h:templates/deform
+    deform_bootstrap:templates
 
 # SQLAlchemy configuration -- See SQLAlchemy documentation
 sqlalchemy.url: sqlite:///h.db
</syntaxhighlight>

=== Migrate ES data ===

Python script to move data from an elasticsearch node to another

<syntaxhighlight>
from elasticsearch import Elasticsearch, helpers

old = Elasticsearch(['old.server:9200'])
new = Elasticsearch(['new.server:9200'])

helpers.reindex(old, 'annotator', 'annotator', new)
</syntaxhighlight>