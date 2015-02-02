There are several special pages that Stewards should know about:
* [[Special:ArticleFeedback|The Article Feedback dashboard]], listing pages with highest and lowest ratings, as well as recent lows 
* [[Special:AdminLinks]], which functions like a dashboard, with helpful links. This is handy for create templates. 
* [[Special:Version|The Mediawiki version page]], including all information about our current installation, such as extensions
* [[Meta:Deployment|Mediawiki Deployment Instructions]], for installing extensions, adding software to the site, etc.
* [[WPD:Site_Map|Site Map]], including site architecture and software requirements
* '''?uselang=qqx''' appended to any page give you special information about that page

==Site Metrics==
* [[WPD:Admin/Site_Metrics|Site Metrics]]
* [[Special:Statistics]]
* [https://meta.wikimedia.org/wiki/Research:Community_portal_redesign WikiMedia discussion on a useful community portal for Wikipedia editors]

==Account Creation==
Currently, only registered account holders can view pages on the wiki.
* [[Special:UserLogin|UserLogin]] allows ''bureaucrats'' to create accounts
* [[Special:RequestAccount|Request Account]] allows users to ask for an account
* [[Special:ConfirmAccounts|Confirm Accounts]] allows ''bureaucrats'' to approve requested accounts
* [[WPD:Admin/Autoconfirm|Autoconfirm]] allows Admins to override spam controls for known users

==Content Management==
* [[Special:ReplaceText]] allows admins to search and replace across multiple pages on the wiki using regular expressions. See [http://www.mediawiki.org/wiki/Extension:Replace_Text#Usage usage instructions] for more details.
* [[Special:Nuke|Nuke]] allows admins to mass delete all edits by a particular user, IP address, etc.
** [[Special:Log/delete|Log/delete]] shows all pages which have been deleted

==Miscellaneous==

===Debugging===
You can bypass fastly completely by curling directly to an app server and passing the host header; so rather than just seeing a 500, you can see an actual exception:
 curl 'http://15.185.108.248/w/api.php' -H 'Host: docs.webplatform.org'