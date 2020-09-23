# OAuth 2.0 Client with Spring Boot and WSO2 Identity Server

This repository contains an example implementation that demonstrate how to use Spring Boot and Spring Security to create an OAuth 2.0 Client that authenticates users through the WSO2 Identity Server.

There are only two things to consider when configuring the client in the WSO2 Identity Server:
The redirect uri is the path of the application where the WSO2 Identity Server will redirect to after the user was authenticated. In this case we assume that this example will be hosted on `localhost`. 

## Configure application.yml
Update the client registration and provider to fit your settings.

```yaml
spring:
  security:
    oauth2:
      client:
        registration:
          wso2:
            client-name: Login with the WSO2 Identity Server
            client-id: RVHiJhY6ux2s77lTf14VKrsUd3oa
            client-secret: X0cLbAG4Q3ftz9HbGUYQ7O_MKx0a
            authorization-grant-type: authorization_code
            redirect-uri: "{baseUrl}/login/oauth2/code/{registrationId}"
            scope: openid, profile
        provider:
          wso2:
            issuer-uri: https://localhost:9443/oauth2/token
```

## Run the application
To start the application run 

```bash
./gradlew bootRun
```

Open `https://localhost:8443` in your browser. Click on the link to login and fetch an access and ID token from the WSO2 Identity Server.

## More Information
More information about OAuth 2.0, OpenID Connect and the WSO2 Identity Server can be found here:

* [WSO2 Identity Server](https://wso2.com/identity-and-access-management/)
* [OAuth 2.0](https://tools.ietf.org/html/rfc6749)
* [OpenID Connect](https://openid.net/)
