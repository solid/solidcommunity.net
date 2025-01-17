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
     - creating a new POD installs the same NSS default containers/resources structure including ACL's
     - your pod can be used as a login end point (https://yourPod.solidcommunity.net, and not only hhtps://solidcommunity.net in CSS)
4. **What are the changes ?**
   - none with your data
   - NSS trustedApp functionality based on subdomain do not exist in CSS
   - the IdP login process
   - password recovery after migation
5. **And now on**
   - some missing things : Hopefully not many. And surely some regression : for example no pod delete function
   - improvements what CSS as added like implementing many notifications types.
   - Fill free to propose and help implement your ideas.

## PIVOT login
Actual users of CSS will not see much changes, just some adaptation to migration
- login
  - login to the migrated account can be done with just the podUsername (no need to type podUsername@users.css.pod)
    All other accounts shall use the full email
  - password : your NSS password
- login redirects to the user account, where you can add/delete email addresses.
  - these addresses if true ones can be used to recover lost password
  - `We encourage you to add a real email address and remove the fake migration one`
## CSS user account management
Some clarification may help.
- In NSS a pod and a user account have a one to one relation. The recovery email was located in the pod root ACL
- In PIVOT (CSS) a user account can contain :
  - many login email's, many pods, many webId's
    - and at least one of each. You cannot delete a POD from an account
    - you can add external WebId's
  - These WebID's can have the property to access all pod ACL's (owner in NSS)
- This is where you can create `Credential Tokens`
## Thanks and some reasons for the move
- for the solid community server the move from NSS to CSS has been supported by the Solid Community members since 2 years
  The idea was to replace NSS that dates a bit, by recently developped and better supported CSS, this does not mean that NSS is deprecated
- On CSS some user experiences where considered to be a regression and CSS PIVOT flavour was made for that. Thanks to @michieldejong and testers
- A migration script was proposed by @rubenVerborgh and served as basis for the solidcommunity.net migration @bourgeoa

