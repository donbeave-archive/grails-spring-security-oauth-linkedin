grails-spring-security-oauth-linkedin [![Build Status](https://api.travis-ci.org/donbeave/grails-spring-security-oauth-linkedin.png?branch=master)](https://travis-ci.org/donbeave/grails-spring-security-oauth-linkedin)
====================================

LinkedIn extension for [Grails Spring Security OAuth][spring-security-oauth-plugin] plugin

Installation
------------

Add the following plugin definition to your BuildConfig:
```groovy
// ...
plugins {
  // ...
  compile ':spring-security-oauth:2.0.2'
  compile ':spring-security-oauth-linkedin:0.1'
  // ...
}
```

Usage
-----

Add to your Config:
```groovy
oauth {
  // ...
  providers {
    // ...
    linkedin {
      api = org.scribe.builder.api.LinkedInApi
      key = 'oauth_linkedin_key'
      secret = 'oauth_linkedin_secret'
      successUri = '/oauth/linkedin/success'
      failureUri = '/oauth/linkedin/error'
      callback = "${baseURL}/oauth/linkedin/callback"
    }
    // ...
  }
}
```

In your view you can use the taglib exposed from this plugin and from OAuth plugin to create links and to know if the user is authenticated with a given provider:
```xml
<oauth:connect provider="linkedin" id="linkedin-connect-link">Linkedin</oauth:connect>

Logged with linkedin?
<s2o:ifLoggedInWith provider="linkedin">yes</s2o:ifLoggedInWith>
<s2o:ifNotLoggedInWith provider="linkedin">no</s2o:ifNotLoggedInWith>
```

[spring-security-oauth-plugin]: https://github.com/enr/grails-spring-security-oauth
