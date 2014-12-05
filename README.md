Rollbar Logback
=============

[![Build Status](https://travis-ci.org/tapstream/rollbar-logback.svg?branch=master)](https://travis-ci.org/tapstream/rollbar-logback)

This is a fork of Tapstream's rollbar-logback fork, which seems to have some official blessing by virtue of being
linked to from Rollbar's website. Unfortunately it hasn't been pushed into Maven Central, thus this fork. There are
no code changes in this fork, only pom.xml changes to the groupId and version. The original java package structure
(com.tapstream) has been preserved, even though it differs from the new groupId (com.voodoodyne.rollbar-logback). If Tapstream ever
publishes their artifact, use it instead.

-----

This is a fork of the ahaid's [Rollbar Logback Appender](https://github.com/ahaid/rollbar-logback) created on
July 27th, 2014 for use with the error aggregation service [Rollbar](https://rollbar.com/). You will need a Rollbar
account: sign up for an account [here](https://rollbar.com/signup/).


Logback
------------

	<appender name="ROLLBAR" class="com.tapstream.rollbar.logback.RollbarAppender">
        <apiKey>[YOUR APIKEY HERE]</apiKey>
        <environment>local</environment>
    </appender>

	<root level="debug">
		<appender-ref ref="ROLLBAR"/>
	</root>

Appender parameters:

* url: The Rollbar API url. Default: https://api.rollbar.com/api/1/item/
* apiKey: The rollbar API key. Mandatory.
* environment: Environment. i.e. production, test, development. Mandatory.


Custom MDC parameters
----------------------

Any MDC values with keys that do not start with `RollbarFilter.REQUEST_PREFIX` will be added as custom parameters to
the Rollbar item request.


Servlet Filter
---------------

Located at `com.tapstream.rollbar.logback.RollbarFilter` is a J2EE servlet filter that will populate the `request`
portion of the Rollbar item from a ServletRequest. The filter will include:

* Remote IP address
* User agent
* Method
* URL
* Query String
* Headers
* Parameters


Acknowledgements
--------------

This library has been inspired by:

* [rollbar-java](https://github.com/rafael-munoz/rollbar-java)
* [rollbar-logback](https://github.com/ahaid/rollbar-logback)

