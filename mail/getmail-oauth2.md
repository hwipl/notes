# Getmail OAuth2 Authorization

See getmailrc examples at
https://github.com/getmail6/getmail6/blob/master/docs/getmailrc-examples:

## Gmail

```
# Example 12: Gmail xoauth2 example
#
# A client_id and client_secret identify a web app or a desktop app.
# getmail-gmail-xoauth-tokens
# creates a local server with loopback redirect (127.0.0.1) to get the authorization.
# https://developers.google.com/identity/protocols/oauth2/native-app#redirect-uri_loopback
#
# To initialize do:
#
# Step1: Create a new OAuth 2.0 Client-ID
#
# - project create:
#   https://console.cloud.google.com/projectcreate
# - consent screen:
#   https://console.cloud.google.com/apis/credentials/consent
#   only external available for non-workspace users.
#   [ADD OR REMOVE SCOPE] https://mail.google.com/
#   Test User: Add all your emails you want to use with getmail.
# - credential:
#   https://console.cloud.google.com/apis/credentials
#   [Create Credentials/Oauth client ID] Desktop App / getmail
#   DOWNLOAD JSON
#
# Step 2: for each email you mentioned as test user above,
# create a file <email>.json according the below template.
#
# - Edit the email in each json file
# - copy two lines from the downloaded json into each json file
#   client_id
#   client_secret
#
# {"scope": "https://mail.google.com/",
#  "user": "your-gmail-user@gmail.com",
#  "client_id": "the new client id",
#  "client_secret": "the new secret",
#  "token_uri": "https://accounts.google.com/o/oauth2/token",
#  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
#  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs"}
#
# Step 3: init step, execute for each json file
#
#    getmail-gmail-xoauth-tokens --init /path-to-your-users-getmail-directory/<email>.json
#
# It will ask you to visit a http url.
# On the browser:
# - There will be a warning "Google hasn't verified this app": continue.
# - Then there will be the consent screen: continue.
#
# getmail-gmail-xoauth-tokens will update the <email>.json file.
#
# Unfortunately this Step 3 needs to be repeated regularly.
# Therefore on should better opt for an google generated "app password".
#
# Step 4: Update the `[retriever]` section of the rc file as below.
# use_xoauth2 must be True, else [AUTHENTICATIONFAILED].
#

[retriever]
type = SimpleIMAPSSLRetriever
use_xoauth2 = True
server = imap.gmail.com
username = your-gmail-user@gmail.com
password_command = ("getmail-gmail-xoauth-tokens", "/path/to/your/users/getmail/directory/<email>.json")
```

## Microsoft 365 

```
# Example 13: Microsoft Office 365 IMAP4 xoauth2 example
#
# To initialize do:
#
# Step1: Create App Registration in Azure
#
# In a browser, open https://portal.azure.com
# Select "Microsoft Entra ID" (use the search if needed)
# Select "App Registrations"
# Select "New Registration"
# Enter a project name, eg "getmail".
# Select "Accounts in this organizational directory only (Single tenant)" from "Supported account types"
# Select type "Web" and enter "http://localhost" for "Redirect URI"
# Select "Register"
#
# Now, from the new App's details page, make a note of:
# * client_id
# * tenant_id
# (These are in the "Essentials" section.)
#
# Next create a secret by selecting "Certificates and secrets"
# Select "New client secret"
# * Description: password
# * Expires: select preferred expiry date
# Make a note of:
# * client_secret
# It is available by selecting "Value".
#
# Next add permissions:
#
# Select "API permissions", then "Add a permission".
# Select "Microsoft Graph"
# Select "Delegated permissions"
# Search and select the following permissions:
# * IMAP.AccessAsUser.All
# * offline_access
# Select "Add permissions"

# Step 2: Add the new credentials to the microsoft.json template
#
# {"scope": "https://outlook.office.com/IMAP.AccessAsUser.All offline_access",
#  "user": "firstname.lastname@example.com",
#  "client_id": "<client_id>",
#  "client_secret": "<secret>",
#  "token_uri": "https://login.microsoftonline.com/<tenant_id>/oauth2/v2.0/token",
#  "auth_uri": "https://login.microsoftonline.com/<tenant_id>/oauth2/v2.0/authorize"}
#
# Step 3: execute:
#
#    getmail-gmail-xoauth-tokens --init /path-to-your-users-getmail-directory/microsoft.json
#
# This will give you a URL you need to open in a browser.
# Opening this URL will generate a HTTP-redirect that connects back and updates the json file.
# Note: The script starts a local HTTP-server listening on http://localhost:8083.
# If you connect from a remote machine, you will need to forward that port to your local
# machine, so that the server can be reached via localhost:8083 on the machine running the browser.
# (You only need to do this once.)
#
# getmail-gmail-xoauth-tokens is waiting for the reconnect with the URL that contains the verification code.
# Once it received the callback
#
# getmail-gmail-xoauth-tokens will update the microsoft.json file. The json file
# will now contain the required tokens.
#
# Step 4: Update the `[retriever] `section of the rc file.

[retriever]
type = SimpleIMAPSSLRetriever
use_xoauth2 = True
server = outlook.office365.com
username = firstname.lastname@example.com
password_command = ("getmail-gmail-xoauth-tokens", "/path-to-your-users-getmail-directory/microsoft.json")
```

## Microsoft Personal Accounts

```
# Example 14: Personal Microsoft accounts (Outlook.com, Hotmail, Live, or MSN)
# IMAP4 xoauth2 example
#
# To initialize do:
#
# Step1: Create App Registration in Azure
#        (You need a Microsoft Azure tenant)
#
# In a browser, open https://portal.azure.com
# Select "Microsoft Entra ID" (use the search if needed)
# Select "App Registrations"
# Select "New Registration"
# Enter a project name, eg "getmail".
# Select "Personal Microsoft accounts only" from "Supported account types"
# Select type "Web" and enter "http://localhost" for "Redirect URI"
# Select "Register"
#
# Now, from the new App's details page, make a note of:
# * client_id
# * tenant_id
# (These are in the "Essentials" section.)
#
# Next create a secret by selecting "Certificates and secrets"
# Select "New client secret"
# * Description: password
# * Expires: select preferred expiry date
# Make a note of:
# * client_secret
# It is available by selecting "Value".
#
# Next add permissions:
#
# Select "API permissions", then "Add a permission".
# Select "Microsoft Graph"
# Select "Delegated permissions"
# Search and select the following permissions:
# * IMAP.AccessAsUser.All
# * offline_access
# Select "Add permissions"

# Step 2: Add the new credentials to the microsoft.json template
#
# {"scope": "https://outlook.office.com/IMAP.AccessAsUser.All offline_access",
#  "user": "firstname.lastname@example.com",
#  "client_id": "<client_id>",
#  "client_secret": "<secret>",
#  "token_uri": "https://login.microsoftonline.com/consumers/oauth2/v2.0/token",
#  "auth_uri": "https://login.microsoftonline.com/consumers/oauth2/v2.0/authorize"}
#
# Step 3: execute:
#
#    getmail-gmail-xoauth-tokens --init /path-to-your-users-getmail-directory/microsoft.json
#
# This will give you a URL you need to open in a browser.
# Opening this URL will generate a HTTP-redirect that connects back and updates the json file.
# Note: The script starts a local HTTP-server listening on http://localhost:8083.
# If you connect from a remote machine, you will need to forward that port to your local
# machine, so that the server can be reached via localhost:8083 on the machine running the browser.
# (You only need to do this once.)
#
# getmail-gmail-xoauth-tokens is waiting for the reconnect with the URL that contains the verification code.
# Once it received the callback
#
# getmail-gmail-xoauth-tokens will update the microsoft.json file. The json file
# will now contain the required tokens.
#
# Step 4: Update the `[retriever] `section of the rc file.

[retriever]
type = SimpleIMAPSSLRetriever
use_xoauth2 = True
server = outlook.office365.com
username = firstname.lastname@example.com
password_command = ("getmail-gmail-xoauth-tokens", "/path-to-your-users-getmail-directory/microsoft.json")
```
