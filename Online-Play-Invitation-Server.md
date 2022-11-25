[Switch](Server-List#switch) > Online Play Invitations
---

This server manages online play invitations.

URL: https://app.lp1.five.nintendo.net

## Methods

| Method | URL |
| --- | --- |
| PATCH | `/v1/invitations` |
| POST | `/v1/invitation_groups` |
| GET | `/v1/invitation_groups/<id>` |
| GET | [`/v1/users/<id>/invitations/inbox`](#get-v1usersidinvitationsinbox) |
| PATCH | `/v1/users/<id>/invitations/mark_as_read` |

### GET /v1/users/&lt;id&gt;/invitations/inbox
This method returns incoming invitations. It takes two query parameters:

| Param | Description |
| --- | --- |
| fields | Comma-separated list of fields that should be returned by the server |
| read | Specifies whether the server should return only unread invitation (`false`) or all invitations (`true`) |

Response on success:

| Field | Description |
| --- | --- |
| count | Total number of invitations |
| items | Invitation list |

The friends sysmodule currently either provides no parameters or `fields=count&read=false`.

## Errors
On error, the server sends the following response:

| Field | Description |
| --- | --- |
| error | Error information |

The error information is encoded like this:

| Field | Description |
| --- | --- |
| code | Error code (string with 4 digits) |
| message | Error message |

### Known Errors
| Code | Status | Message |
| --- | --- | --- |
| 0001 | ? | ? |
| 0002 | 400 | Invalid parameter. |
| 0003 | 404 | Invalid request URI. |
| 0004 | ? | ? |
| 0005 | ? | ? |
| 0006 | 401 | Unauthorized. |
| 0007 | ? | ? |
| 0008 | ? | ? |
| 0009 | ? | ? |
| 0010 | ? | ? |
