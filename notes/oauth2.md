## What is OAuth 2.0

OAuth 2.0, which stands for "open authorization", is a standard designed to allow a website or application to access resources hosted by other web apps on behalf of a user. It replaced OAuth 1.0 in 2012 and is now the de facto industry standard for online authorization. OAuth 2.0 provides consented access and restricts actions of what the client app can perform on resources on behalf of the user, without ever sharing the user's credentials.

Although the web is the main platform for OAuth 2, the specification also describes how to handle this kind of delegated access to other client types (browser-based applications, server-side web applications, native/mobile apps, connected devices, etc.)

## Principles of OAuth 2.0

OAuth 2.0 is an **authorization** protocol and not an authentication protocol. As such, it is designed primarily as means of granting access to a set of resources, for example, remote APIs or user data.

OAuth 2.0 uses access tokens. An **access token** is a piece of data that represents the authorization to access resources on behalf of the end-user. OAuth 2.0 doesn't define a specific format for access tokens. However, in some contexts, the JSON web token (JWT) format is often used. This enables token issuers to include data in the token itself. Also, for security reasons, access tokens may have an expiration date.

## OAuth 2.0 roles

The idea of roles is part of the core specification of the OAuth 2.0 authorization framework. These define the essential components of an OAuth 2.0 system, and are as follows:

- **Resource owner**: The user or system that owns the protected resources and can grant access to them.

- **Client**: The client is the system that requires access to the protected resources. To access resources, the client must hold the appropriate access token.

- **Authorization server**: This server receives requests from the client for access tokens and issues them upon successful authentication and consent by the resource owner. The authorization server exposes two endpoints: the authorization endpoint, which handles the interactive authentication and consent of the user, and the token endpoint, which is involved in a machine to machine interaction.

- **Resource server**: A server that protects the user's resources and receives access requests from the client. It accepts and validates an access token from the client and returns the appropriate resources to it.

## OAuth 2.0 scopes

Scopes are an important concept in OAuth 2.0. They are used to specify exactly the reason for which access to resources may be granted. Acceptable scope values, and which resources they relate to, are dependent on the resource server.

## OAuth 2.0 access tokens and authorization code

The OAuth 2 authorization server may not directly return an access token after the resource owner has authorized access. Instead, and for better security, and **authorization code** may be returned, which is then exchanged for an access token. In addition, the authorization server may also issue a refresh token with the access token. Unlike access tokens, refresh tokens normally have long expiry times and maybe exchanged for new access tokens when the latter expires. Because refresh tokens have these properties, they have to be stored securely by clients.

## How does OAuth 2.0 work

At the most basic level, before OAuth 2.0 can be used, the client must acquire its own credentials, a *client id* and *client secret*, from the authorization server in order to identify and authenticate itself when requesting an access token.

Using OAuth 2.0, access requests are initiated by the client, e.g, a mobile app, website, smart TV app, desktop application, etc. The token request, exchange and response follow this general flow:

1. The client requests authorization (authorization request) from the authorization server, supplying the client id and secret to as identification; It also provides the scopes and an endpoint URI (redirect URI) to send the access token or the authorization code to.

2. The authorization server authenticates the client and verifies that the requested scopes are permitted.

3. The resource owner interacts with the authorization server to grant access.

4. The authorization server redirects back to the client with either an authorization code or access token, depending on the grand type, as it will be explained in the next section. A refresh token may also be returned. 

5. With the access token, the client requests access to the resource from the resource server.

## Grant types in OAuth 2.0

In OAuh 2.0, grants are the set of steps a client has to perform to get resource access authorization. The authorization framework provides several grant types to address different scenarios:

- **Authorization code** grant: The authorization server returns a single-use authorization code to the client, which is then exchanged for an access token. This is the best option for traditional web apps where the exchange can securely happen on the server side. The authorization code flow might be used by single page apps (SPA) and mobile/native apps. However, here, the client cannot be stored securely, and so authentication, during the exchange, is limited to the use of *client id* alone. A better alternative is the authorization code with PKCE grant, below.

- **Authorization code grant with proof key for code exchange (PKCE)**: This authorization flow is similar to the authorization code grant, but with additional steps that make it more secure for mobile/native apps and SPAs.

- **Implicit** grant: A simplified flow where the access token is returned directly to the client. In the implicit flow, the authorization server may return the access token as a parameter in the callback URI or as a response to a form post. The first option is now deprecated due to potential token leakage.

- **Resource owner credentials grant type**: This grant requires the client first to acquire the resource owner's credentials, which are passed to the authorization server. It is, therefore, limited to clients that are completely trusted. It has the advantage that no redirect to the authorization server is involved, so it is applicable in the use cases where a redirect is infeasible.

- **Client credentials grant type**: Used for non-interactive applications e.g, automated processes, microservices, etc. In this case, the application is authenticated per se by using its client id and secret.

- **Device authorization flow**: A grant that enables use by apps on input-constrained devices, such as smart TVs.

- **Refresh token grant**: The flow that involves the exchange of a refresh token for a new access token.