# BTCjam-OAuth2-PHP
> A simple PHP implementation of the OAuth 2.0 protocol that uses the BTCjam Authenticated API.

### About
This is a working example that does not include the full functions of the BTCjam API, rather it is more of just a demonstration of the OAuth2 protocol flow necessary to extract data from the API endpoint.

There didn't seem to be any really super-slim OAuth2 libraries in PHP.  For example, Google's implementation contains dozens of files and is very difficult to tweak, should your quirky API ask for it.

This repo contains a library that is a simpler sub-set implementation of the [RFC 6749](http://tools.ietf.org/id/draft-ietf-oauth-v2-22.html).  (Not all features added, since we don't need them for most.)

### What is BTCjam?

[BTCjam.com](https://btcjam.com/?r=b4724761-bfdc-4bb5-90f9-f8c34bc8c7de&utm_medium=direct&utm_source=referral_url&utm_campaign=undefined) is the world's largest bitcoin peer-to-peer lending marketplace. Where borrowers get great rates and Investors get great returns.  It has been around for years and is very reliable.


### What is the OAuth protocol?
RFC 6749: "The OAuth 2.0 authorization framework enables a third-party application to obtain limited access to an HTTP service, either on behalf of a resource owner by orchestrating an approval interaction between the resource owner and the HTTP service, or by allowing the third-party application to obtain access on its own behalf." (October 2012)

The uses cases covered by the framework are:
* Web-server applications
* Browser-based applications
* Mobile apps
* Username and password access
* Application access

In all these uses cases, the goal of the OAuth2 protocol is to exchange a token string between the Client and the Resource Server. This token is used to authenticate all the API calls using the Authorization HTTP header. Below is reported an example of the Bearer token (RFC 7650), the most used token type of OAuth2:

> Authorization: Bearer RsT5OjbzRn430zqMLgV3Ia


### Why should I not use an OAuth API PHP SDK or Library (like Google's)?

Some issues include:
+ Interoperability prohibits just creating great products
+ Must make many modifications to static references
+ The authentication protocol must be customized 
+ There are too many class files, making modification can be complex.
+ Requires composer to install the package of classes
+ You do not need most of the functions available

# Getting Started...

### Creating your web application credentials
All web applications that use OAuth2 must have credentials that identify the application to the OAuth2 server. 

To obtain web application credentials for your project, complete these steps:

   1. Visit the web site of the API provider and open the [BTCjam API Settings page](https://btcjam.com/oauth/applications).
   2. Enter a name for this endpoint.
   3. Enter a Redirect URI, which handles responses from the OAuth2 server.
 
### Using $_SESSION to store 'access_token'...
The standard expiration timeout of the Session state is not long lived.
In order to retain permission to access the API, or to use it outside a web browser interface, we save the token to local file (/tmp/php_session_btcjam.txt).  
When the Session expires, the access_token is normally lost and the application redirects to the authorization endpoint again.  By caching the 'access_token' we can avoid this and have a long session!



### History
+ Jan-03-2016: v1.01 - added SESSION caching to file.
+ Dec-21-2015: v1.00 released. 
+ Dec-15-2015: init repo. 


### BTCjam API Protocol References

+ [BTCjam.com](https://btcjam.com/?r=b4724761-bfdc-4bb5-90f9-f8c34bc8c7de&utm_medium=direct&utm_source=referral_url&utm_campaign=undefined)
+ [BTCjam API FAQ](https://btcjam.com/faq/api)


### OAuth 2.0 Coding References

+ Brent Shaffer's [OAuth 2.0 Server Cookbook](https://bshaffer.github.io/oauth2-server-php-docs/cookbook/)
+ Knp University: [OAuth2 in 8 Steps](https://knpuniversity.com/screencast/oauth/)
+ Google Developers: [OAuth2 Protocol](https://developers.google.com/identity/protocols/OAuth2)
+ MSDN: [Implementing an OAuth-Enabled Application in PHP](https://msdn.microsoft.com/en-us/library/dn632721.aspx#Anchor_1)

### OAuth 2.0 Protocol References

+ [RFC 6749](https://datatracker.ietf.org/doc/rfc6749/) - "The OAuth 2.0 Authorization Framework"
+ [The OAuth 2.0 Authorization Protocol (draft-ietf-oauth-v2-22)](http://tools.ietf.org/id/draft-ietf-oauth-v2-22.html)
+ Search the [latest updated OAuth RFCs](https://datatracker.ietf.org/doc/search/?name=oauth&activeDrafts=on&rfcs=on) from IETF
+ [oauth3.net](http://oauth.net)
