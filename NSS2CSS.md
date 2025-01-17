**`Migration shall occur on the week-end of January 2025 Saturday 25 to Sunday 26`**


# Migration from NSS to CSS
**`CHECK TO FIND YOUR POD, AND TEST IT WITH the default SolidOS, and solid apps`**

**`REPORT ISSUES`**

**`AND IF YOU DON'T FIND YOUR POD, READ NEXT LINES AND ASK FOR RECOVERY/INTEGRATION`**


1. **What does the migration do** https://github.com/nodeSolidServer/NSS2CSS/blob/solidcommunity.net/README.md
  - keep the same domain
  - move your pod as is to the new server (subdomain and data)
  - keep your password
  - new login process based on email address.
    On migration a fake email is created NSS pod `username` --> `username@users.css.pod` 

2. **pre-migration** a test server is available on https://solidcommunity.net:8443
  - some 17000/65000 accounts have been migrated from a weekly backup of https://solidcommunity.net
    - https://solidcommunity.net has kept pod's from inception from all NSS versions including IdP breaking changes, Solid specification changes, broken data (broken WebID's, no WebID document, external WebId's, ...)
    - a small amount of Pod's are incompatible with CSS IdP that uses an email address (characters not allowed (`@`, ` `, uppercase letters)).
  - some data links have been migrated in turtle files (.ttl, .meta., .acl) to not break existing internal links
    These changes will not happen in the final migration where we keep the domain:PORT
  - the only change in data relates to the oidcIssuer in WebID that must endsWith a `/` in CSS
3. **What do not change ?**
  - `your data`, thanks to the fact that the domain is unchanged `https://solidcommunity.net` all link relations are kept
  - A flavor of `CSS with mashlib` called `PIVOT` https://github.com/solid-contrib/pivot has been prepared to reflect has much as possible the actual user experience with the SolidOS front-end
    For example : - 
    - in the front-end a folder URL without a `/` will find a folder
    - `hpps://yourPod/browse.html` opens the SolidOS webApp
    - creating a new POD installs the same default containers/resources structure including ACL's
4. **What are the changes ?**
  - none with your data
  - NSS trustedApp functionality based on subdomain do not exist in CSS
  - the IdP login process
  - password recovery after migation


## PIVOT login process
## CSS account management and howTo add a recovery email to the migarted account
## Thanks and some reasons for the move
- for the solid community server the move from NSS to CSS has been supported by the Solid Community members since 2 years
  The idea was to replace NSS that dates a bit by recently developped and better supported CSS, this does not mean that NSS is abandonned
  Some use experience where considered to be improved and CSS PIVOT flavour was made for that. Thanks to @michieldejong and testers
- A migration package was proposed by @ruben and served as bases for the solidcommunity.net migration @bourgeoa

