[NPLN](NPLN-Servers) > Auth Service
---

Full name: `nn.npln.auth.v1.Auth`

* [Overview](#overview)
* [Methods](#methods)
* [Source code](https://github.com/kinnay/NPLN-Protocols/blob/master/latest/proto/auth/v1/auth.proto)

## Overview
The auth service manages user accounts on an NPLN tenant. Before using another service, one must first obtain an access token from the auth service.

Most methods of the auth service require you to provide an **external id token**. The id token can be obtained by logging in on the [BaaS server](BAAS-Server) and identifies a specific user on your Switch. It also proves that you own a specific title.

![](https://www.dropbox.com/s/wrzz0wkawmoo09b/baas_id_token.png?raw=1&x=3)

The first time you provide an id token to NPLN, the server automatically creates an **account** that is tied to your **external id**. An account is valid across all tenants.

NPLN allows you to create an arbitrary number of **users** per tenant. Every user that is created belongs to a specific account and only exists under the given tenant. There are two ways to create a user on a tenant:
* A new user can be created manually with CreateUser. After creating a user manually, an access token can be obtained with IssueToken.
* Every tenant provides 16 prearranged users per account. An access token for a prearranged user can be obtained with IssuePrearrangedUserToken.

Every tenant also provides an anonymous user. This user is special because it does not belong to a specific account. Most services deny all requests that are made by an anonymous user.

## Methods
* CreateUser
* IssueToken
* RefreshToken
* IssuePrearrangedUserToken
* IssueAnonymousUserToken
* RefreshAnonymousUserToken
* ListUsers
* DeleteUser
