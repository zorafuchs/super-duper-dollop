# super-duper-dollop

git checkout develop
git flow feature start navigation

## GIT

Create a feature branch with `git flow`

```sh
git flow feature start feature-name
```

Push branch to GitHub first time
```sh
git push -u origin feature/feature-name
```

After you make changes on some files `commit` them


```sh
git add . 
git commit -m "Tell what you have been doing in this commit and what you have changed"
```

Now you `push` changes to GitHub

```sh
git push
```

If you finished a feature and want to merge it into the develop branch, go to your project on GitHub, navigate to 'Pull request' and add a new Pullrequest from your feature branch to the develop branch. Now you can assign it to a person, which can look through your changes and recommand changes. When everone (or you as the admin) is happy with the changes, you can merge the pull request with the button on the bottom of the page.

And so you finally changed the project :tada:

## CSS

```css
text: text-decoration (none; underline), font-size (vw-height: percent, px, inherit)

```

## OAUTH

```mermaid
sequenceDiagram
    participant User
    participant Client
    participant AuthorizationServer
    participant ResourceServer

    User->>Client: Initiates login
    Client->>AuthorizationServer: Redirect to login page
    AuthorizationServer->>User: Prompt for credentials
    User->>AuthorizationServer: Submits credentials
    AuthorizationServer->>User: Consent screen
    User->>AuthorizationServer: Grants consent
    AuthorizationServer->>Client: Redirect with authorization code
    Client->>AuthorizationServer: Exchange code for access token
    AuthorizationServer->>Client: Return access token
    Client->>ResourceServer: Request resource with access token
    ResourceServer->>Client: Return requested resource
    Client->>User: Display resource
```

## OICD

Authorization Code Flow

```mermaid
sequenceDiagram
    participant User
    participant Client
    participant AuthorizationServer
    participant ResourceServer

    User->>Client: Access protected resource
    Client->>AuthorizationServer: Redirect to /authorize endpoint
    AuthorizationServer->>User: Prompt for credentials
    User->>AuthorizationServer: Submit credentials
    AuthorizationServer->>User: Consent screen
    User->>AuthorizationServer: Grant consent
    AuthorizationServer->>Client: Redirect with authorization code
    Client->>AuthorizationServer: POST /token endpoint (code exchange)
    AuthorizationServer->>Client: Return ID token, access token, (refresh token)
    Client->>AuthorizationServer: Validate ID token
    Client->>ResourceServer: Request resource with access token
    ResourceServer->>Client: Return resource
    Client->>User: Display resource
```

Implicit flow

```mermaid
sequenceDiagram
    participant User
    participant Client
    participant AuthorizationServer

    User->>Client: Access protected resource
    Client->>AuthorizationServer: Redirect to /authorize endpoint (response_type=id_token or id_token token)
    AuthorizationServer->>User: Prompt for credentials
    User->>AuthorizationServer: Submit credentials
    AuthorizationServer->>User: Consent screen
    User->>AuthorizationServer: Grant consent
    AuthorizationServer->>Client: Redirect with ID token (and access token)
    Client->>User: Display resource (tokens are in URL fragment)
```


Hybrid Flow

```mermaid
sequenceDiagram
    participant User
    participant Client
    participant AuthorizationServer
    participant ResourceServer

    User->>Client: Access protected resource
    Client->>AuthorizationServer: Redirect to /authorize endpoint (response_type=code id_token or code token id_token)
    AuthorizationServer->>User: Prompt for credentials
    User->>AuthorizationServer: Submit credentials
    AuthorizationServer->>User: Consent screen
    User->>AuthorizationServer: Grant consent
    AuthorizationServer->>Client: Redirect with authorization code and ID token (and access token)
    Client->>AuthorizationServer: POST /token endpoint (code exchange for access token, refresh token)
    AuthorizationServer->>Client: Return access token, refresh token
    Client->>AuthorizationServer: Validate ID token
    Client->>ResourceServer: Request resource with access token
    ResourceServer->>Client: Return resource
    Client->>User: Display resource
```


## Kerberos

```mermaid
sequenceDiagram
    participant User
    participant Client
    participant AS
    participant TGS
    participant Service

    Note over Client,AS: Teil 1: TGT & Session Key
    User->>Client: Initiate authentication
    Client->>AS: AS-REQ (Authentication Service Request)
    AS->>Client: AS-REP (Authentication Service Reply) with TGT and session key
    Note over Client,TGS: Teil 2: Service Ticket
    Client->>TGS: TGS-REQ (Ticket Granting Service Request) with TGT
    TGS->>Client: TGS-REP (Ticket Granting Service Reply) with service ticket and session key
    Note over Client,Service: Teil 3: Mutual Authentication
    Client->>Service: AP-REQ (Application Request) with service ticket and authenticator
    Service->>Client: AP-REP (Application Reply) with authenticator
    Service->>Client: Access granted
```


