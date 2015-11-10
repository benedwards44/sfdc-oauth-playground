Project home moved to [github](https://github.com/jesperfj/sfdc-oauth-playground).

This project provides a basic oauth consumer implementation in Apex. It defines objects for storing keys and secrets for multiple services and users. It also comes with an API "playground" where you can try out API calls to your Oauth services.

[Install beta 1.0 as a managed package in your developer or sandbox org](https://login.salesforce.com/?startURL=%2Fpackaging%2FinstallPackage.apexp%3Fp0%3D04tA0000000D8Zk)

# About this project #

The main purpose of this project was to show how to write OAuth signed requests in Apex, but it expanded beyond that to a more full fledged OAuth consumer playground. It comes with a set of custom objects for storing OAuth service configuration and OAuth tokens on behalf of users in the org.

IMPORT SECURITY NOTE: When you authorize access to a remote service, your personal and very private access token and secret are stored in a custom object. Do not use this app in an org where you do not trust users who may access this object (OAuth\_Tokenc). At the very least, administrators will have access to the data.

The project also comes with functionality for authorizing access, including authorization redirects and callbacks.

Finally, the project includes an API Tester that you can use to make API requests to services that have been authorized for access.

The code has been tested with the following services:

  * Google (Contacts, Calendar, Portable Contacts)
  * LinkedIn (can't get status API to work, but the OAuth part works fine)
  * Twitter
  * TripIt
  * Salesforce (works except that redirects can get confused if on same instance)

Yahoo couldn't be tested because it wasn't possible to have a Yahoo application verified. Yahoo requires you to host an HTML page on your root path (/) with a certain code in it. This is currently not possibe with Force.com sites. Google has a similar verification mechanism but they give you the option to include the code in a meta tag on any page on your site which works better.

## Apex Classes ##

### OAuth.cls ###

The OAuth class is the meat of the project. It relies on the OAuth\_Servicec and OAuth\_Tokenc for storage and retrieval of tokens and service configuration, but it can easily be rewritten as a stand-alone class that can be used for a more specific application.

### AuthController.cls ###

Visual Force Controller for authorization flow

### TestController.cls ###

VF Controller for the API Test page. This page includes a feature that allows you to save URLs (API endpoints), including post data for later use.