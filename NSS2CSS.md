# Migration from NSS to CSS
**`IF YOU DON'T FIND YOUR POD, READ NEXT LINES AND ASK FOR RECOVERY/INTEGRATION`**

Migration shall occur on the week-end of January 2025 Saturday 25 to Sunday 26
- pre-migration a test server is available on https://solidcommunity.net:8443
  - some 17000/65000 accounts have been migrated from a weekly backup of https://solidcommunity.net
    - https://solidcommunity.net has kept pod's from inception with all NSS versions including IdP breaking changes, broken WebID's, no WebID document, external WebId's, ...
    - a small amount of Pod's are incompatible with CSS IdP that uses an email address (characters not allowed(`@`, ` `, uppercase letters)
  - some data links have been migrated in turtle files (.ttl, .meta., .acl) to not break existing internal links
    These changes will not happen in the final migration where we keep the domain:PORT
  - the only change in data relates to the oidcIssuer in WebID that must endsWith a `/` in CSS
- What do not change ?
  - `your data`, thanks to the fact that the domain is unchanged `https://solidcommunity.net` all link relations are kept
  - A flavor of `CSS with mashlib` called `PIVOT` has been prepared to reflect has much as possible the actual user experience with the SolidOS front-end
    For example : - 
    - in the front-end a folder URL without a `/` will find a folder
    - `hpps://yourPod/browse.html` opens the SolidOS webApp
    - creating a new POD installs the same default containers/resources structure including ACL's
- What are the changes ?
  - none with your data
  - the IdP login process
  - NSS trustedApp functionality based on subdomain do not exist in CSS

 ## PIVOT login process
