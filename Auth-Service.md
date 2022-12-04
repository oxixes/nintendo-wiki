[NPLN](NPLN-Servers) > Auth Service
---

Full name: `nn.npln.auth.v1.Auth`

* [Overview](#overview)
* [Methods](#methods)
* [Source code](https://github.com/kinnay/NPLN-Protocols/blob/master/latest/proto/auth/v1/auth.proto)

## Overview
The auth service manages user accounts on an NPLN tenant. Before using another service, one must first obtain an access token from the auth service.

The first time you go online in a game, it creates a new user on the tenant. After creating a user, an access token can be obtained with IssueToken.

Every tenant also provides 16 prearranged users and one anonymous user. A prearranged user acts like a normal user but with some limitations (for example, it cannot be deleted). The anonymous user has a special username (`u-anonymous`) and cannot be used for most services.

Creating a user or issuing a token requires an external id token, which can be obtained by logging in on the [BaaS server](BAAS-Server).

## Methods
* CreateUser
* IssueToken
* RefreshToken
* IssuePrearrangedUserToken
* IssueAnonymousUserToken
* RefreshAnonymousUserToken
* ListUsers
* DeleteUser