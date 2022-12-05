[NPLN](NPLN-Servers) > Auth Service
---

Full name: `nn.npln.auth.v1.Auth`

* [Overview](#overview)
* [Methods](#methods)
* [Source code](https://github.com/kinnay/NPLN-Protocols/blob/master/latest/proto/auth/v1/auth.proto)

# Overview
The auth service manages user accounts on an NPLN tenant. Before using another service, one must first obtain an access token from the auth service.

#### External Ids
Most methods of the auth service require you to provide an **external id token**. The id token can be obtained by logging in on the [BaaS server](BAAS-Server) and identifies a specific user on your Switch. It also proves that you own a specific title.

![](https://www.dropbox.com/s/wrzz0wkawmoo09b/baas_id_token.png?raw=1&x=3)

#### Accounts

The first time you provide an id token to NPLN, the server automatically creates an **account** that is tied to your **external id**. The account is shared across all tenants.

#### Users
NPLN allows you to create an arbitrary number of **users** on a tenant. Every user that is created belongs to a specific account and only exists under the given tenant. There are two ways to create a user on a tenant:
* A new user can be created manually with CreateUser. After creating a user manually, an access token can be obtained with IssueToken.
* Every tenant provides 16 prearranged users per account. An access token for a prearranged user can be obtained with IssuePrearrangedUserToken.

Every tenant also provides an anonymous user. This user is special because it does not belong to a specific account. Most services deny requests that are made by an anonymous user.

# Methods
* CreateUser
* IssueToken
* RefreshToken
* IssuePrearrangedUserToken
* IssueAnonymousUserToken
* RefreshAnonymousUserToken
* ListUsers
* DeleteUser

## CreateUser
This method creates a user on the given tenant.

Example request:
```json
{
    "parent": "tenants/current",
    "external_id_token": {
        "nsa_id_token": "eyJqa3UiOiJodHRwczovL2UwZDY3YzUwOWZiMjAzODU4ZWJjYjJmZTNmODhjMmFhLmJhYXMubmludGVuZG8uY29tLzEuMC4wL2NlcnRpZmljYXRlcyIsImFsZyI6IlJTMjU2Iiwia2lkIjoiNTc0Zjc0MjctN2M1NC00ODUwLTg2ZjAtNzk0Yjg5NjU1ZTJiIn0.eyJhdWQiOiJlZDllMmYwNWQyODZmN2I4Iiwic3ViIjoiOGNhOGQ3ODQyZjg2NWIyZiIsIm5pbnRlbmRvIjp7ImF0IjoxNjcwMjc2MjU2LCJhdiI6IjAwMDEiLCJobSI6dHJ1ZSwicGgiOiJHQU1FX1NFUlZFUiIsImFpIjoiMDEwMDhmNjAwOGM1ZTAwMCIsImVkaSI6ImYxZjlkNzMyMGQ5YmEwZGVkMWFkZmQ2OTgxZWNmMWY0Iiwib3BwIjoiTUVNQkVSU0hJUF9SRVFVSVJFRCJ9LCJpc3MiOiJodHRwczovL2UwZDY3YzUwOWZiMjAzODU4ZWJjYjJmZTNmODhjMmFhLmJhYXMubmludGVuZG8uY29tIiwidHlwIjoiaWRfdG9rZW4iLCJleHAiOjE2NzAyODcwNTYsImlhdCI6MTY3MDI3NjI1NiwiYnM6ZGlkIjoiNTgxZWE3ODZhOTFmMTY4OSIsImp0aSI6IjY3NDNmMDllLWQ4OTEtNGY3YS05MDgzLTMwNzlkOTgxZTk0YiJ9.6DfNTQbTmkuA3bUPwMi3oQa06Tic2D8WB5vv-45zNFxa2l_0YbhpMarbNoxsTH2v7493GaUA520mh2f_HISN1yrjCA3C3YIGGr7NWoDd_Ew97JU1uV2b26klUom4XHADUnzHOoPCu5QwoB_8Dwa3ls25oSwy5hkcNiRnsfB_d2U14bCVwdnKjzbUAXgL7k2oTP2lV2j4aD8Pu5PhKeFuZdUo8gj-5_0sP2O3w1HyywdysIGDON7GYJ1mrc36sF7kB_MfHmYr65rSoFtqN_mHVYuxSGv1C3SwtZA2K_YFjahy2mjXubu68N7eatoFoP8xe2xbevf7Q5wfujHk5yJOqw"
    }
}
```
