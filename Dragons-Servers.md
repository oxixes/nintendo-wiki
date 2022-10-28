[Switch Server](Server-List#switch) > eLicenses
---

These servers take JSON-encoded requests and respond with JSON-encoding.

https://dragons.hac.lp1.dragons.nintendo.net:

| URL |
| --- |
| `/quickTEST` |
| `/v1/contents_authorization_token/issue` |
| [`/v1/contents_authorization_token_for_aauth/issue`](#post-v1contents_authorization_token_for_aauthissue) |
| `/v1/elicense_archives/publish` |
| `/v1/elicense_archives/<id>/report` |
| `/v1/elicenses/eticket_token` |
| `/v1/elicenses/exercise` |
| `/v1/elicenses/extend` |
| `/v1/elicenses/report` |
| `/v1/elicenses/revoke` |
| `/v1/elicenses/revoke_all` |
| `/v1/elicenses/inactivated_reason` |
| `/v1/notification_token` |
| `/v1/rights/available_elicenses` |
| `/v1/rights/publish_device_linked_elicenses` |
| `/v1/rights/publish_elicenses` |

https://tigers.hac.lp1.dragons.nintendo.net:

| URL |
| --- |
| `/quickTEST` |
| `/v1/etickets/publish` |

https://dragonst.hac.lp1.dragons.nintendo.net:

| URL |
| --- |
| `/quickTEST` |
| `/v1/debug/edge_token/issue` |
| `/v1/edge_token/issuable_titles` |
| `/v1/edge_token/issue` |

## POST /v1/contents_authorization_token_for_aauth/issue
| Field | Format | Description |
| --- | --- | --- |
| elicense_id | `\p{XDigit}{32}` | E-license id |
| na_id | `\p{XDigit}{16}` | Nintendo account id |

Response on success:

| Field | Description |
| --- | --- |
| contents_authorization_token | The token |

## Errors
On error, the server sends the following response:

| Field | Description |
| --- | --- |
| type | `https://problems.dragons.nintendo.net/errors/v1/<status>/<code>` |
| title | Error title |
| detail | Error details |
| number | HTTP status code |

If the error code is `invalid_parameter`, the response may contain more details under the `invalid-params` key, for example:

* `'invalid-params': [{'name': 'naId', 'reason': 'must not be null'}]`
* `'invalid-params': [{'name': 'naId.accountId', 'reason': 'must match "\\p{XDigit}{16}"'}]`

### Known Errors
| Status | Code | Title | Detail |
| --- | --- | --- | --- |
| 400 | `duplicate_rights_id` | | |
| 400 | `invalid_device_certificate` | | |
| 400 | `invalid_eticket_template` | | |
| 400 | `invalid_parameter` | Parameter is invalid | |
| 401 | `account_id_required` | | |
| 401 | `authentication_required` | | |
| 403 | `edge_token_not_grantable` | | |
| 403 | `invalid_token` | Token is invalid | |
| 403 | `license_archive_not_allowed` | | |
| 403 | `license_inactive` | | |
| 403 | `license_not_grantable` | | |
| 403 | `rights_policy_not_allowed` | | |
| 403 | `system_update_required` | | |
| 404 | `license_archive_not_found` | | |
| 404 | `license_not_found` | | |
| 404 | `page_not_found` | Page not found | |
| 404 | `promotion_policy_not_found` | | |
| 404 | `title_not_found` | | |
| 405 | `method_not_allowed` | Method not allowed | |
| 406 | `not_acceptable` | | |
| 415 | `unsupported_media_type` | | |
| 500 | `delete_record_failed` | | |
| 500 | `insert_record_failed` | | |
| 500 | `op2_error` | | |
| 500 | `shogun_error` | | |
| 500 | `unexpected_error` | | |
| 500 | `unknown_issuer` | | |
| 500 | `update_record_failed` | | |
| 503 | `abort_retry` | | |
| 503 | `op2_maintenance` | | |
| 503 | `service_unavailable` | | |