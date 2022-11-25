[Switch](Server-List#switch) > Friend Invitations
---

URL: https://app.lp1.five.nintendo.net

| Method | URL |
| --- | --- |
| PATCH | `/v1/invitations` |
| POST | `/v1/invitation_groups` |
| GET | `/v1/invitation_groups/<id>` |
| GET | `/v1/users/<id>/invitations/inbox` |
| PATCH | `/v1/users/<id>/invitations/mark_as_read` |

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
