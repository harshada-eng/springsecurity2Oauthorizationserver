##README .md

Used default configuration & explicitly added the configuration needed additionally for 
"AuthorizationServerConfig". Configured "userDetailsService" to manage the users
We need to have "userDetailsService" to have some users to login maybe have some authorities 
based on configuration by overriding configure method of "WebSecurityConfigurerAdapter"
We need password encoder that have hash word password leaving password as plain text

In "AuthorizationServerConfig" we need to specify which are the clients, which are the 
applications that are allowed to connect to authorization server so that they can use the 
privilege of using managed users
method "public void configure(ClientDetailsServiceConfigurer clients)"

For example "Github's sso", First we add an application on Github 
& we receive back clientId & secret. This clientId & secret we use against Github 
to authorize & to tell Github that we are allowed by you to use your users. 
So at least one clientId & secret is needed

Spring Boot application linking "authenticationManager" object to the authorization server 
& need to expose it as a Bean in the method "public AuthenticationManager authenticationManagerBean()".
In this method, we are taking "authenticationManager" from "WebSecurityConfigurerAdapter" 
by calling the method from "WebSecurityConfigurerAdapter" called "authenticationManagerBean()" 
& exposing it as a Bean in the context for injecting it in "AuthorizationServerConfig" & setting it 
in authorization endpoints configurer.

-------------------------------------------------------------------------------------------------------
Get the User's details from angular application(Login Functionality)
--For user
user = "harsh"  
password =  "12345"

--For Client Configure
Client = "clientId"
secret = "abcde"

For that user, temporary token is gained back which can be used as temporary key to access 
some or all the endpoints depending upon the configuration

We do the login angular application, we get the user's name & password from user
& then we call the authorization server & we can have back temporary token from 
the authorization server

When token expires, use refresh tokens to get another access token automatically