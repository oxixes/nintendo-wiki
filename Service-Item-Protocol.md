## [[NEX Protocols]] > ServiceItemProtocol (119)

| Method ID | Method Name |
| --- | --- |
| 1 | [GetEnvironment](#1-getenvironment) |
| 2 | [HttpGetRequest](#2-httpgetrequest) |
| 3 | [HttpGetResponse](#3-httpgetresponse) |
| 4 | [PurchaseServiceItemRequest](#4-purchaseserviceitemrequest) |
| 5 | [PurchaseServiceItemResponse](#5-purchaseserviceitemresponse) |
| 6 | [ListServiceItemRequest](#6-listserviceitemrequest) |
| 7 | [ListServiceItemResponse](#7-listserviceitemresponse) |
| 8 | [GetBalanceRequest](#8-getbalancerequest) |
| 9 | [GetBalanceResponse](#9-getbalanceresponse) |
| 10 | [GetPrepurchaseInfoRequest](#10-getprepurchaseinforequest) |
| 11 | [GetPrepurchaseInfoResponse](#11-getprepurchaseinforesponse) |
| 12 | [GetServiceItemRightRequest](#12-getserviceitemrightrequest) |
| 13 | [GetServiceItemRightResponse](#13-getserviceitemrightresponse) |
| 14 | [GetPurchaseHistoryRequest](#14-getpurchasehistoryrequest) |
| 15 | [GetPurchaseHistoryResponse](#15-getpurchasehistoryresponse) |
| 16 | [PostRightBinaryByAccount](#16-postrightbinarybyaccount) |
| 17 | [UseServiceItemByAccountRequest](#17-useserviceitembyaccountrequest) |
| 18 | [UseServiceItemByAccountResponse](#18-useserviceitembyaccountresponse) |
| 19 | [AcquireServiceItemByAccount](#19-acquireserviceitembyaccount) |
| 20 | [GetSupportId](#20-getsupportid) |
| 21 | [GetLawMessageRequest](#21-getlawmessagerequest) |
| 22 | [GetLawMessageResponse](#22-getlawmessageresponse) |

# (1) GetEnvironment

## Request
| Type | Name |
| --- | --- |
| [String] | uniqueId |
| Uint8 | platform |

## Response
| Type | Name |
| --- | --- |
| [String] | str |

# (2) HttpGetRequest

## Request
| Type | Name |
| --- | --- |
| [ServiceItemHttpGetParam](#serviceitemhttpgetparam-structure) | url |

## Response
| Type | Name |
| --- | --- |
| Uint32 | requestId |

# (3) HttpGetResponse

## Request
| Type | Name |
| --- | --- |
| Uint32 | requestId |

## Response
| Type | Name |
| --- | --- |
| [ServiceItemHttpGetResponse](#serviceitemhttpgetresponse-structure) | response |

# (4) PurchaseServiceItemRequest

## Request
| Type | Name |
| --- | --- |
| [ServiceItemPurchaseServiceItemParam](#serviceitempurchaseserviceitemparam-structure) | purchaseServiceItemParam |

## Response
| Type | Name |
| --- | --- |
| Uint32 | requestId |

# (5) PurchaseServiceItemResponse

## Request
| Type | Name |
| --- | --- |
| Uint32 | requestId |

## Response
| Type | Name |
| --- | --- |
| [ServiceItemPurchaseServiceItemResponse](#serviceitempurchaseserviceitemresponse-structure) | purchaseServiceItemResponse |

# (6) ListServiceItemRequest

## Request
| Type | Name |
| --- | --- |
| [ServiceItemListServiceItemParam](#serviceitemlistserviceitemparam-structure) | listServiceItemParam |

## Response
| Type | Name |
| --- | --- |
| Uint32 | requestId |

# (7) ListServiceItemResponse

## Request
| Type | Name |
| --- | --- |
| Uint32 | requestId |

## Response
| Type | Name |
| --- | --- |
| [ServiceItemListServiceItemResponse](#serviceitemlistserviceitemresponse-structure) | listServiceItemResponse |

# (8) GetBalanceRequest

## Request
| Type | Name |
| --- | --- |
| [ServiceItemGetBalanceParam](#serviceitemgetbalanceparam-structure) | getBalanceParam |

## Response
| Type | Name |
| --- | --- |
| Uint32 | requestId |

# (9) GetBalanceResponse

## Request
| Type | Name |
| --- | --- |
| Uint32 | requestId |

## Response
| Type | Name |
| --- | --- |
| [ServiceItemGetBalanceResponse](#serviceitemgetbalanceresponse-structure) | getBalanceResponse |

# (10) GetPrepurchaseInfoRequest

## Request
| Type | Name |
| --- | --- |
| [ServiceItemGetPrepurchaseInfoParam](#serviceitemgetprepurchaseinfoparam-structure) | getPrepurchaseInfoParam |

## Response
| Type | Name |
| --- | --- |
| Uint32 | requestId |

# (11) GetPrepurchaseInfoResponse

## Request
| Type | Name |
| --- | --- |
| Uint32 | requestId |

## Response
| Type | Name |
| --- | --- |
| [ServiceItemGetPrepurchaseInfoResponse](#serviceitemgetprepurchaseinforesponse-structure) | getPrepurchaseInfoResponse |

# (12) GetServiceItemRightRequest

## Request
| Type | Name |
| --- | --- |
| [ServiceItemGetServiceItemRightParam](#serviceitemgetserviceitemrightparam-structure) | getServiceItemRightParam |
| Bool | withoutRightBinary |

## Response
| Type | Name |
| --- | --- |
| Uint32 | requestId |

# (13) GetServiceItemRightResponse

## Request
| Type | Name |
| --- | --- |
| Uint32 | requestId |

## Response
| Type | Name |
| --- | --- |
| [ServiceItemGetServiceItemRightResponse](#serviceitemgetserviceitemrightresponse-structure) | getServiceItemRightResponse |

# (14) GetPurchaseHistoryRequest

## Request
| Type | Name |
| --- | --- |
| [ServiceItemGetPurchaseHistoryParam](#serviceitemgetpurchasehistoryparam-structure) | getPurchaseHistoryParam |

## Response
| Type | Name |
| --- | --- |
| Uint32 | requestId |

# (15) GetPurchaseHistoryResponse

## Request
| Type | Name |
| --- | --- |
| Uint32 | requestId |

## Response
| Type | Name |
| --- | --- |
| [ServiceItemGetPurchaseHistoryResponse](#serviceitemgetpurchasehistoryresponse-structure) | getPurchaseHistoryResponse |

# (16) PostRightBinaryByAccount

## Request
| Type | Name |
| --- | --- |
| [ServiceItemPostRightBinaryByAccountParam](#serviceitempostrightbinarybyaccountparam-structure) | postRightBinaryByAccountParam |

## Response
| Type | Name |
| --- | --- |
| [ServiceItemPostRightBinaryResponse](#serviceitempostrightbinaryresponse-structure) | postRightBinaryResponse |

# (17) UseServiceItemByAccountRequest

## Request
| Type | Name |
| --- | --- |
| [ServiceItemUseServiceItemByAccountParam](#serviceitemuseserviceitembyaccountparam-structure) | useServiceItemByAccountParam |

## Response
| Type | Name |
| --- | --- |
| Uint32 | requestId |

# (18) UseServiceItemByAccountResponse

## Request
| Type | Name |
| --- | --- |
| Uint32 | requestId |

## Response
| Type | Name |
| --- | --- |
| [ServiceItemUseServiceItemResponse](#serviceitemuseserviceitemresponse-structure) | useServiceItemResponse |

# (19) AcquireServiceItemByAccount

## Request
| Type | Name |
| --- | --- |
| [ServiceItemAcquireServiceItemByAccountParam](#serviceitemacquireserviceitembyaccountparam-structure) | acquireServiceItemByAccountParam |

## Response
| Type | Name |
| --- | --- |
| [ServiceItemAcquireServiceItemResponse](#serviceitemacquireserviceitemresponse-structure) | acquireServiceItemResponse |

# (20) GetSupportId

## Request
| Type | Name |
| --- | --- |
| [ServiceItemGetSupportIdParam](#serviceitemgetsupportidparam-structure) | getSuppordIdParam |

## Response
| Type | Name |
| --- | --- |
| [String] | supportId |

# (21) GetLawMessageRequest

## Request
| Type | Name |
| --- | --- |
| [ServiceItemGetLawMessageParam](#serviceitemgetlawmessageparam-structure) | getLawMessageParam |

## Response
| Type | Name |
| --- | --- |
| Uint32 | requestId |

# (22) GetLawMessageResponse

## Request
| Type | Name |
| --- | --- |
| Uint32 | requestId |

## Response
| Type | Name |
| --- | --- |
| [ServiceItemGetLawMessageResponse](#serviceitemgetlawmessageresponse-structure) | getLawMessageResponse |

# Types

## ServiceItemHttpGetParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | url |

## ServiceItemHttpGetResponse ([Structure])
| Type | Name |
| --- | --- |
| [qBuffer] | response |

## ServiceItemEShopResponse ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | httpStatus |
| Uint32 | errorCode |
| [String] | correlationId |

## ServiceItemAmount ([Structure])
| Type | Name |
| --- | --- |
| [String] | formattedAmount |
| [String] | currency |
| [String] | rawValue |

## ServiceItemPurchaseServiceItemParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | itemCode |
| [String] | priceId |
| [String] | referenceId |
| [String] | balance |
| [String] | itemName |
| [String] | ecServiceToken |
| [String] | language |
| Uint32 | uniqueId |

Revision 1:

| Type | Name |
| --- | --- |
| Uint8 | platform |

## ServiceItemPurchaseInfo ([Structure])
| Type | Name |
| --- | --- |
| [String] | transactionId |
| [String] | extTransactionId |
| [String] | itemCode |
| [ServiceItemAmount](#serviceitemamount) | postBalance |

## ServiceItemPurchaseServiceItemResponse ([Structure])
| This structure inherits from [ServiceItemEShopResponse](#serviceitemeshopresponse-structure) |
| --- |

| Type | Name |
| --- | --- |
| [List]&lt;[ServiceItemPurchaseInfo](#serviceitempurchaseinfo-structure)&gt; | nullablePurchaseInfo |

## ServiceItemListServiceItemParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | language |
| Uint32 | offset |
| Uint32 | size |
| Bool | isBalanceAvailable |
| Uint32 | uniqueId |

Revision 1:

| Type | Name |
| --- | --- |
| Uint8 | platform |

## ServiceItemLimitation ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | limitationType |
| Uint32 | limitationValue |

## ServiceItemAttribute ([Structure])
| Type | Name |
| --- | --- |
| [String] | name |
| [String] | value |

## ServiceItemListItem ([Structure])
| Type | Name |
| --- | --- |
| [String] | itemCode |
| [ServiceItemAmount](#serviceitemamount-structure) | regularPrice |
| Bool | taxExcluded |
| Bool | initialPurchaseOnly |
| [ServiceItemLimitation](#serviceitemlimitation-structure) | limitation |
| [List]&lt;[ServiceItemAttribute](#serviceitemattribute-structure)&gt; | attributes |

## ServiceItemCatalog ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | totalSize |
| Uint32 | offset |
| [List]&lt;[ServiceItemListItem](#serviceitemlistitem-structure)&gt; | listItems |
| Bool | isBalanceAvailable |
| [ServiceItemAmount](#serviceitemamount-structure) | balance |

## ServiceItemListServiceItemResponse ([Structure])
| This structure inherits from [ServiceItemEShopResponse](#serviceitemeshopresponse-structure) |
| --- |

| Type | Name |
| --- | --- |
| [List]&lt;[ServiceItemCatalog](#serviceitemcatalog-structure)&gt; | nullableCatalog |

## ServiceItemGetBalanceParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | language |
| Uint32 | uniqueId |

Revision 1:

| Type | Name |
| --- | --- |
| Uint8 | platform |

## ServiceItemGetBalanceResponse ([Structure])
| This structure inherits from [ServiceItemEShopResponse](#serviceitemeshopresponse-structure) |
| --- |

| Type | Name |
| --- | --- |
| [List]&lt;[ServiceItemAmount](#serviceitemamount-structure)&gt; | nullableBalance |

## ServiceItemGetPrepurchaseInfoParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | itemCode |
| [String] | referenceId |
| [ServiceItemLimitation](#serviceitemlimitation-structure) | limitation |
| [String] | language |
| Uint32 | uniqueId |

Revision 1:

| Type | Name |
| --- | --- |
| Uint8 | platform |

## ServiceItemPrepurchaseRightInfo ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | limitationType |
| Uint32 | acquiredCount |
| Uint32 | usedCount |
| Uint32 | expiryDate |
| Uint32 | expiredCount |
| [List]&lt;Uint32&gt; | expiryCounts |

## ServiceItemPrepurchaseInfo ([Structure])
| Type | Name |
| --- | --- |
| [String] | itemCode |
| [String] | priceId |
| [ServiceItemAmount](#serviceitemamount-structure) | regularPrice |
| Bool | isTaxAvailable |
| [ServiceItemAmount](#serviceitemamount-structure) | taxAmount |
| [ServiceItemAmount](#serviceitemamount-structure3) | totalAmount |
| [ServiceItemAmount](#serviceitemamount-structure) | currentBalance |
| [ServiceItemAmount](#serviceitemamount-structure3) | postBalance |
| [ServiceItemPrepurchaseRightInfo](#serviceitemprepurchaserightinfo-structure) | currentRightInfo |
| [ServiceItemPrepurchaseRightInfo](#serviceitemprepurchaserightinfo-structure) | postRightInfo |

## ServiceItemGetPrepurchaseInfoResponse ([Structure])
| This structure inherits from [ServiceItemEShopResponse](#serviceitemeshopresponse-structure) |
| --- |

| Type | Name |
| --- | --- |
| [List]&lt;[ServiceItemPrepurchaseInfo](#serviceitemprepurchaseinfo-structure)&gt; | nullablePrepurchaseInfo |

## ServiceItemGetServiceItemRightParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | referenceId |
| [String] | deviceId |
| Uint32 | uniqueId |
| Uint8 | itemGroup |

Revision 1:

| Type | Name |
| --- | --- |
| Uint8 | platform |

## ServiceItemRightBinary ([Structure])
| Type | Name |
| --- | --- |
| Uint8 | useType |
| [qBuffer] | rightBinary |

## ServiceItemAccountRight ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | pid |
| [ServiceItemLimitation](#serviceitemlimitation-structure) | limitation |
| [List]&lt;[ServiceItemRightBinary](#serviceitemrightbinary-structure)&gt; | rightBinaries |

## ServiceItemAccountRightTime ([Structure])
| This structure inherits from [ServiceItemAccountRight](#serviceitemaccountright-structure) |
| --- |

This structure does not contain any fields.

## ServiceItemAccountRightConsumption ([Structure])
| This structure inherits from [ServiceItemAccountRight](#serviceitemaccountright-structure) |
| --- |

| Type | Name |
| --- | --- |
| Uint32 | usedCount |
| Uint32 | expiredCount |
| [List]&lt;Uint32&gt; | expiryCounts |

## ServiceItemRightInfo ([Structure])
| Type | Name |
| --- | --- |
| [String] | referenceId |
| Uint32 | referenceIdType |

## ServiceItemRightTimeInfo ([Structure])
| This structure inherits from [ServiceItemRightInfo](#serviceitemrightinfo-structure) |
| --- |

| Type | Name |
| --- | --- |
| [List]&lt;[ServiceItemAccountRightTime](#serviceitemaccountrighttime-structure)&gt; | accountRights |

## ServiceItemRightConsumptionInfo ([Structure])
| This structure inherits from [ServiceItemRightInfo](#serviceitemrightinfo-structure) |
| --- |

| Type | Name |
| --- | --- |
| [List]&lt;[ServiceItemAccountRightConsumption](#serviceitemaccountrightconsumption-structure)&gt; | accountRights |

## ServiceItemRightInfos ([Structure])
| Type | Name |
| --- | --- |
| [String] | supportId |
| [List]&lt;[ServiceItemRightConsumptionInfo](#serviceitemrightconsumptioninfo-structure)&gt; | consumptionRightInfos |
| [List]&lt;[ServiceItemRightTimeInfo](#serviceitemrighttimeinfo-structure)&gt; | additionalTimeRightInfos |
| [List]&lt;[ServiceItemRightTimeInfo](#serviceitemrighttimeinfo-structure)&gt; | permanentRightInfos |
| Bool | alreadyPurchasedInitialOnlyItem |

## ServiceItemGetServiceItemRightResponse ([Structure])
| This structure inherits from [ServiceItemEShopResponse](#serviceitemeshopresponse-structure) |
| --- |

| Type | Name |
| --- | --- |
| [List]&lt;[ServiceItemRightInfos](#serviceitemrightinfos-structure)&gt; | nullableRightInfos |

## ServiceItemGetPurchaseHistoryParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | language |
| Uint32 | offset |
| Uint32 | size |
| Uint32 | uniqueId |

Revision 1:

| Type | Name |
| --- | --- |
| Uint8 | platform |

## ServiceItemTransaction ([Structure])
| Type | Name |
| --- | --- |
| [String] | transactionId |
| [String] | extTransactionId |
| [DateTime] | time |
| Uint32 | transactionType |
| [String] | transactionDescription |
| [ServiceItemAmount](#serviceitemamount-structure) | transactionAmount |
| [String] | itemCode |
| [String] | referenceId |
| [ServiceItemLimitation](#serviceitemlimitation-structure) | limitation |

## ServiceItemPurchaseHistory ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | totalSize |
| Uint32 | offset |
| [List]&lt;[ServiceItemTransaction](#serviceitemtransaction-structure)&gt; | transactions |

## ServiceItemGetPurchaseHistoryResponse ([Structure])
| This structure inherits from [ServiceItemEShopResponse](#serviceitemeshopresponse-structure) |
| --- |

| Type | Name |
| --- | --- |
| [List]&lt;[ServiceItemPurchaseHistory](#serviceitempurchasehistory-structure)&gt; | nullablePurchaseHistory |

## ServiceItemLawMessage ([Structure])
| Type | Name |
| --- | --- |
| Bool | isMessageRequired |
| [String] | lawMessage |

## ServiceItemGetLawMessageParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | language |
| Uint32 | uniqueId |

Revision 1:

| Type | Name |
| --- | --- |
| Uint8 | platform |

## ServiceItemGetLawMessageResponse ([Structure])
| This structure inherits from [ServiceItemEShopResponse](#serviceitemeshopresponse-structure) |
| --- |

| Type | Name |
| --- | --- |
| [List]&lt;[ServiceItemLawMessage](#serviceitemlawmessage-structure)&gt; | nullableLawMessage |

## ServiceItemPostRightBinaryByAccountParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | referenceId |
| Uint8 | useType |
| [qBuffer] | rightBinary |
| [String] | logMessage |
| Uint32 | uniqueId |

Revision 1:

| Type | Name |
| --- | --- |
| Uint8 | platform |

## ServiceItemPostRightBinaryResponse ([Structure])
| This structure inherits from [ServiceItemEShopResponse](#serviceitemeshopresponse-structure) |
| --- |

This structure does not contain any fields.

## ServiceItemUseServiceItemByAccountParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | referenceIdForUse |
| [String] | referenceIdForRightBinary |
| Uint8 | useType |
| Uint8 | useNumber |
| [qBuffer] | rightBinary |
| [String] | logMessage |
| Uint32 | uniqueId |

Revision 1:

| Type | Name |
| --- | --- |
| Uint8 | platform |

## ServiceItemUsedInfo ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | acquiredCount |
| Uint32 | usedCount |

## ServiceItemUseServiceItemResponse ([Structure])
| This structure inherits from [ServiceItemEShopResponse](#serviceitemeshopresponse-structure) |
| --- |

| Type | Name |
| --- | --- |
| [List]&lt;[ServiceItemUsedInfo](#serviceitemusedinfo-structure)&gt; | nullableUsedInfo |

## ServiceItemAcquireServiceItemByAccountParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | referenceIdForAcquisition |
| [String] | referenceIdForRightBinary |
| Uint8 | useType |
| Uint32 | limitationType |
| Uint32 | limitationValue |
| [qBuffer] | rightBinary |
| [String] | logMessage |
| Uint32 | uniqueId |

Revision 1:

| Type | Name |
| --- | --- |
| Uint8 | platform |

## ServiceItemAcquireServiceItemResponse ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | limitationType |
| Uint32 | acquiredCount |
| Uint32 | usedCount |
| Uint32 | expiryDate |
| Uint32 | expiredCount |
| [List]&lt;Uint32&gt; | expiryCounts |

## ServiceItemGetSupportIdParam ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | uniqueId |

Revision 1:

| Type | Name |
| --- | --- |
| Uint8 | platform |

## ServiceItemGetNoticeParam ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | scheduleType |

## ServiceItemNotice ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | scheduleId |
| Uint32 | scheduleType |
| Sint32 | paramInt |
| [String] | paramString |
| [qBuffer] | paramBinary |
| [DateTime] | timeBegin |
| [DateTime] | timeEnd |

## ServiceItemUserInfo ([Structure])
| Type | Name |
| --- | --- |
| [qBuffer] | applicationBuffer |

[Result]: NEX-Common-Types#result
[String]: NEX-Common-Types#string
[Buffer]: NEX-Common-Types#buffer
[qBuffer]: NEX-Common-Types#qbuffer
[List]: NEX-Common-Types#list
[Map]: NEX-Common-Types#map
[DateTime]: NEX-Common-Types#date-time
[Structure]: NEX-Common-Types#structure
[Data]: NEX-Common-Types#any-data-holder
[PID]: NEX-Common-Types#pid
