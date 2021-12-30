
# ItemGetRequest
ItemGetRequest defines the request schema for `/item/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |

# ItemGetResponse
ItemGetResponse defines the response schema for `/item/get` and `/item/webhook/update`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| item | Y | Item | &nbsp; | &nbsp; | &nbsp; |
| status | &nbsp; | ItemStatusNullable | &nbsp; | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# AuthGetRequest
AuthGetRequest defines the request schema for `/auth/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| options | &nbsp; | AuthGetRequestOptions | &nbsp; | &nbsp; | &nbsp; |

# AuthGetRequestOptions
An optional object to filter `/auth/get` results.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_ids | &nbsp; | array[] of strings | A list of `account_ids` to retrieve for the Item.<br/>Note: An error will be returned if a provided `account_id` is not associated with the Item. | &nbsp; | &nbsp; |

# AuthGetResponse
AuthGetResponse defines the response schema for `/auth/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| accounts | Y | array[] of AccountBase | The `accounts` for which numbers are being retrieved. | &nbsp; | &nbsp; |
| numbers | Y | AuthGetNumbers | &nbsp; | &nbsp; | &nbsp; |
| item | Y | Item | &nbsp; | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# AuthGetNumbers
An object containing identifying numbers used for making electronic transfers to and from the `accounts`. The identifying number type (ACH, EFT, IBAN, or BACS) used will depend on the country of the account. An account may have more than one number type. If a particular identifying number type is not used by any `accounts` for which data has been requested, the array for that type will be empty.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| ach | Y | array[] of NumbersACH | An array of ACH numbers identifying accounts. | &nbsp; | &nbsp; |

# TransactionsGetRequest
TransactionsGetRequest defines the request schema for `/transactions/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| options | &nbsp; | TransactionsGetRequestOptions | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| start_date | Y | date | The earliest date for which data should be returned. Dates should be formatted as YYYY-MM-DD. | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | &nbsp; |
| end_date | Y | date | The latest date for which data should be returned. Dates should be formatted as YYYY-MM-DD. | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | &nbsp; |

# TransactionsGetRequestOptions
An optional object to be used with the request. If specified, `options` must not be `null`.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_ids | &nbsp; | array[] of strings | A list of `account_ids` to retrieve for the Item<br/><br/>Note: An error will be returned if a provided `account_id` is not associated with the Item. | &nbsp; | &nbsp; |
| count | &nbsp; | integer | The number of transactions to fetch. | <ul><li>minimum : 1</li><li>maximum : 500</li></ul> | &nbsp; |
| offset | &nbsp; | integer | The number of transactions to skip. The default value is 0. | <ul><li>minimum : 0</li></ul> | &nbsp; |
| include_original_description | &nbsp; | boolean | Include the raw unparsed transaction description from the financial institution. This field is disabled by default. If you need this information in addition to the parsed data provided, contact your Plaid Account Manager. | &nbsp; | &nbsp; |
| include_personal_finance_category_beta | &nbsp; | boolean | Include the `personal_finance_category` object in the response. This feature is currently in beta – to request access, contact transactions-feedback@plaid.com. | &nbsp; | &nbsp; |

# TransactionsGetResponse
TransactionsGetResponse defines the response schema for `/transactions/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| accounts | Y | array[] of AccountBase | An array containing the `accounts` associated with the Item for which transactions are being returned. Each transaction can be mapped to its corresponding account via the `account_id` field. | &nbsp; | &nbsp; |
| transactions | Y | array[] of Transaction | An array containing transactions from the account. Transactions are returned in reverse chronological order, with the most recent at the beginning of the array. The maximum number of transactions returned is determined by the `count` parameter. | &nbsp; | &nbsp; |
| total_transactions | Y | integer | The total number of transactions available within the date range specified. If `total_transactions` is larger than the size of the `transactions` array, more transactions are available and can be fetched via manipulating the `offset` parameter. | &nbsp; | &nbsp; |
| item | Y | Item | &nbsp; | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# TransactionsRefreshRequest
TransactionsRefreshRequest defines the request schema for `/transactions/refresh`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |

# TransactionsRefreshResponse
TransactionsRefreshResponse defines the response schema for `/transactions/refresh`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# TransactionsRecurringGetRequest
TransactionsRecurringGetRequest defines the request schema for `/transactions/recurring/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| account_ids | Y | array[] of strings | A list of `account_ids` to retrieve for the Item<br/><br/>Note: An error will be returned if a provided `account_id` is not associated with the Item. | &nbsp; | &nbsp; |

# TransactionsRecurringGetResponse
TransactionsRecurringGetResponse defines the response schema for `/transactions/recurring/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| inflow_streams | Y | array[] of TransactionStream | An array of depository transaction streams. | &nbsp; | &nbsp; |
| outflow_streams | Y | array[] of TransactionStream | An array of expense transaction streams. | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# TransactionsSyncRequest
TransactionsSyncRequest defines the request schema for `/transactions/sync`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| cursor | &nbsp; | string | The cursor value represents the last update requested. Providing it will cause the response to only return changes after this update.<br/>If omitted, the entire history of updates will be returned, starting with the first-added transactions on the item.<br/>Note: The upper-bound length of this cursor is 256 characters of base64. | &nbsp; | &nbsp; |
| count | &nbsp; | integer | The number of transaction updates to fetch. | <ul><li>minimum : 1</li><li>maximum : 500</li></ul> | &nbsp; |

# TransactionsSyncResponse
TransactionsSyncResponse defines the response schema for `/transactions/sync`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| added | Y | array[] of Transaction | Transactions that have been added to the item since `cursor` ordered by ascending last modified time. | &nbsp; | &nbsp; |
| modified | Y | array[] of Transaction | Transactions that have been modified on the item since `cursor` ordered by ascending last modified time. | &nbsp; | &nbsp; |
| removed | Y | array[] of RemovedTransaction | Transactions that have been removed from the item since `cursor` ordered by ascending last modified time. | &nbsp; | &nbsp; |
| next_cursor | Y | string | Cursor used for fetching any future updates after the latest update provided in this response. | &nbsp; | &nbsp; |
| has_more | Y | boolean | Represents if more than requested count of transaction updates exist. If true, the additional updates can be fetched by making an additional request with `cursor` set to `next_cursor`. | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# InstitutionsGetRequest
InstitutionsGetRequest defines the request schema for `/institutions/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| count | Y | integer | The total number of Institutions to return. | <ul><li>maximum : 500</li></ul> | &nbsp; |
| offset | Y | integer | The number of Institutions to skip. | &nbsp; | &nbsp; |
| country_codes | Y | array[] of CountryCode | Specify an array of Plaid-supported country codes this institution supports, using the ISO-3166-1 alpha-2 country code standard. <br/><br/>In API versions 2019-05-29 and earlier, the `country_codes` parameter is an optional parameter within the `options` object and will default to `[US]` if it is not supplied.<br/> | <ul><li>minItems : 1</li></ul> | &nbsp; |
| options | &nbsp; | InstitutionsGetRequestOptions | &nbsp; | &nbsp; | &nbsp; |

# InstitutionsGetRequestOptions
An optional object to filter `/institutions/get` results.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| products | &nbsp; | array[] of Products | Filter the Institutions based on which products they support.  | &nbsp; | &nbsp; |
| routing_numbers | &nbsp; | array[] of strings | Specify an array of routing numbers to filter institutions. The response will only return institutions that match all of the routing numbers in the array. Routing number records used for this matching are not comprehensive; failure to match a given routing number to an institution does not mean that the institution is unsupported by Plaid. | &nbsp; | &nbsp; |
| oauth | &nbsp; | boolean | Limit results to institutions with or without OAuth login flows. This is primarily relevant to institutions with European country codes. | &nbsp; | &nbsp; |
| include_optional_metadata | &nbsp; | boolean | When `true`, return the institution's homepage URL, logo and primary brand color.<br/><br/>Note that Plaid does not own any of the logos shared by the API, and that by accessing or using these logos, you agree that you are doing so at your own risk and will, if necessary, obtain all required permissions from the appropriate rights holders and adhere to any applicable usage guidelines. Plaid disclaims all express or implied warranties with respect to the logos. | &nbsp; | &nbsp; |
| include_auth_metadata | &nbsp; | boolean | When `true`, returns metadata related to the Auth product indicating which auth methods are supported. | &nbsp; | &nbsp; |
| include_payment_initiation_metadata | &nbsp; | boolean | When `true`, returns metadata related to the Payment Initiation product indicating which payment configurations are supported. | &nbsp; | &nbsp; |

# InstitutionsGetResponse
InstitutionsGetResponse defines the response schema for `/institutions/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| institutions | Y | array[] of Institution | A list of Plaid Institution | &nbsp; | &nbsp; |
| total | Y | integer | The total number of institutions available via this endpoint | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# InstitutionsSearchRequest
InstitutionsSearchRequest defines the request schema for `/institutions/search`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| query | Y | string | The search query. Institutions with names matching the query are returned | &nbsp; | &nbsp; |
| products | Y | array[] of Products | Filter the Institutions based on whether they support all products listed in `products`. Provide `null` to get institutions regardless of supported products. Note that when `auth` is specified as a product, if you are enabled for Instant Match or Automated Micro-deposits, institutions that support those products will be returned even if `auth` is not present in their product array. | <ul><li>minItems : 1</li></ul> | &nbsp; |
| country_codes | Y | array[] of CountryCode | Specify an array of Plaid-supported country codes this institution supports, using the ISO-3166-1 alpha-2 country code standard. In API versions 2019-05-29 and earlier, the `country_codes` parameter is an optional parameter within the `options` object and will default to `[US]` if it is not supplied.<br/> | &nbsp; | &nbsp; |
| options | &nbsp; | InstitutionsSearchRequestOptions | &nbsp; | &nbsp; | &nbsp; |

# InstitutionsSearchRequestOptions
An optional object to filter `/institutions/search` results.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| oauth | &nbsp; | boolean | Limit results to institutions with or without OAuth login flows. This is primarily relevant to institutions with European country codes | &nbsp; | &nbsp; |
| include_optional_metadata | &nbsp; | boolean | When true, return the institution's homepage URL, logo and primary brand color. | &nbsp; | &nbsp; |
| include_auth_metadata | &nbsp; | boolean | When `true`, returns metadata related to the Auth product indicating which auth methods are supported. | &nbsp; | &nbsp; |
| include_payment_initiation_metadata | &nbsp; | boolean | When `true`, returns metadata related to the Payment Initiation product indicating which payment configurations are supported. | &nbsp; | &nbsp; |
| payment_initiation | &nbsp; | InstitutionsSearchPaymentInitiationOptions | &nbsp; | &nbsp; | &nbsp; |

# InstitutionsSearchPaymentInitiationOptions
Additional options that will be used to filter institutions by various Payment Initiation configurations.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| payment_id | &nbsp; | string | A unique ID identifying the payment | &nbsp; | &nbsp; |

# InstitutionsSearchResponse
InstitutionsSearchResponse defines the response schema for `/institutions/search`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| institutions | Y | array[] of Institution | An array of institutions matching the search criteria | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# InstitutionsGetByIdRequest
InstitutionsGetByIdRequest defines the request schema for `/institutions/get_by_id`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| institution_id | Y | string | The ID of the institution to get details about | &nbsp; | &nbsp; |
| country_codes | Y | array[] of CountryCode | Specify an array of Plaid-supported country codes this institution supports, using the ISO-3166-1 alpha-2 country code standard. In API versions 2019-05-29 and earlier, the `country_codes` parameter is an optional parameter within the `options` object and will default to `[US]` if it is not supplied.<br/> | &nbsp; | &nbsp; |
| options | &nbsp; | InstitutionsGetByIdRequestOptions | &nbsp; | &nbsp; | &nbsp; |

# InstitutionsGetByIdRequestOptions
Specifies optional parameters for `/institutions/get_by_id`. If provided, must not be `null`.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| include_optional_metadata | &nbsp; | boolean | When `true`, return an institution's logo, brand color, and URL. When available, the bank's logo is returned as a base64 encoded 152x152 PNG, the brand color is in hexadecimal format. The default value is `false`.<br/><br/>Note that Plaid does not own any of the logos shared by the API and that by accessing or using these logos, you agree that you are doing so at your own risk and will, if necessary, obtain all required permissions from the appropriate rights holders and adhere to any applicable usage guidelines. Plaid disclaims all express or implied warranties with respect to the logos. | &nbsp; | &nbsp; |
| include_status | &nbsp; | boolean | If `true`, the response will include status information about the institution. Default value is `false`. | &nbsp; | &nbsp; |
| include_auth_metadata | &nbsp; | boolean | When `true`, returns metadata related to the Auth product indicating which auth methods are supported. | &nbsp; | &nbsp; |
| include_payment_initiation_metadata | &nbsp; | boolean | When `true`, returns metadata related to the Payment Initiation product indicating which payment configurations are supported. | &nbsp; | &nbsp; |

# InstitutionsGetByIdResponse
InstitutionsGetByIdResponse defines the response schema for `/institutions/get_by_id`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| institution | Y | Institution | &nbsp; | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# ItemRemoveRequest
ItemRemoveRequest defines the request schema for `/item/remove`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |

# ItemRemoveResponse
ItemRemoveResponse defines the response schema for `/item/remove`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# AccountsGetRequest
AccountsGetRequest defines the request schema for `/accounts/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| options | &nbsp; | AccountsGetRequestOptions | &nbsp; | &nbsp; | &nbsp; |

# AccountsGetRequestOptions
An optional object to filter `/accounts/get` results.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_ids | &nbsp; | array[] of strings | An array of `account_ids` to retrieve for the Account. | &nbsp; | &nbsp; |

# AccountsGetResponse
AccountsGetResponse defines the response schema for `/accounts/get` and `/accounts/balance/get`.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| accounts | Y | array[] of AccountBase | An array of financial institution accounts associated with the Item.<br/>If `/accounts/balance/get` was called, each account will include real-time balance information. | &nbsp; | &nbsp; |
| item | Y | Item | &nbsp; | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# CategoriesGetRequest
CategoriesGetRequest defines the request schema for `/categories/get`



# CategoriesGetResponse
CategoriesGetResponse defines the response schema for `/categories/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| categories | Y | array[] of Category | An array of all of the transaction categories used by Plaid. | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# AccountsBalanceGetRequest
AccountsBalanceGetRequest defines the request schema for `/accounts/balance/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| options | &nbsp; | AccountsBalanceGetRequestOptions | &nbsp; | &nbsp; | &nbsp; |

# AccountsBalanceGetRequestOptions
An optional object to filter `/accounts/balance/get` results.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_ids | &nbsp; | array[] of strings | A list of `account_ids` to retrieve for the Item. The default value is `null`.<br/><br/>Note: An error will be returned if a provided `account_id` is not associated with the Item. | &nbsp; | &nbsp; |
| min_last_updated_datetime | &nbsp; | MinLastUpdatedDatetime | &nbsp; | &nbsp; | &nbsp; |

# IdentityGetRequest
IdentityGetRequest defines the request schema for `/identity/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| options | &nbsp; | IdentityGetRequestOptions | &nbsp; | &nbsp; | &nbsp; |

# IdentityGetRequestOptions
An optional object to filter `/identity/get` results.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_ids | &nbsp; | array[] of strings | A list of `account_ids` to retrieve for the Item.<br/>Note: An error will be returned if a provided `account_id` is not associated with the Item. | &nbsp; | &nbsp; |

# IdentityGetResponse
IdentityGetResponse defines the response schema for `/identity/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| accounts | Y | array[] of AccountIdentity | The accounts for which Identity data has been requested | &nbsp; | &nbsp; |
| item | Y | Item | &nbsp; | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# ProcessorAuthGetRequest
ProcessorAuthGetRequest defines the request schema for `/processor/auth/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| processor_token | Y | ProcessorToken | &nbsp; | &nbsp; | &nbsp; |

# ProcessorAuthGetResponse
ProcessorAuthGetResponse defines the response schema for `/processor/auth/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |
| numbers | Y | ProcessorNumber | &nbsp; | &nbsp; | &nbsp; |
| account | Y | AccountBase | &nbsp; | &nbsp; | &nbsp; |

# ProcessorNumber
An object containing identifying numbers used for making electronic transfers to and from the `account`. The identifying number type (ACH, EFT, IBAN, or BACS) used will depend on the country of the account. An account may have more than one number type. If a particular identifying number type is not used by the `account` for which auth data has been requested, a null value will be returned.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| ach | &nbsp; | NumbersACHNullable | &nbsp; | &nbsp; | &nbsp; |

# ProcessorIdentityGetRequest
ProcessorIdentityGetRequest defines the request schema for `/processor/identity/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| processor_token | Y | ProcessorToken | &nbsp; | &nbsp; | &nbsp; |

# ProcessorIdentityGetResponse
ProcessorIdentityGetResponse defines the response schema for `/processor/identity/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account | Y | AccountIdentity | &nbsp; | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# ProcessorBalanceGetRequest
ProcessorBalanceGetRequest defines the request schema for `/processor/balance/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| processor_token | Y | ProcessorToken | &nbsp; | &nbsp; | &nbsp; |
| options | &nbsp; | ProcessorBalanceGetRequestOptions | &nbsp; | &nbsp; | &nbsp; |

# ProcessorBalanceGetRequestOptions
An optional object to filter `/processor/balance/get` results.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| min_last_updated_datetime | &nbsp; | MinLastUpdatedDatetime | &nbsp; | &nbsp; | &nbsp; |

# ProcessorBalanceGetResponse
ProcessorBalanceGetResponse defines the response schema for `/processor/balance/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account | Y | AccountBase | &nbsp; | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# ItemAccessTokenInvalidateRequest
ItemAccessTokenInvalidateRequest defines the request schema for `/item/access_token/invalidate`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |

# ItemAccessTokenInvalidateResponse
ItemAccessTokenInvalidateResponse defines the response schema for `/item/access_token/invalidate`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| new_access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# ItemPublicTokenExchangeRequest
ItemPublicTokenExchangeRequest defines the request schema for `/item/public_token/exchange`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| public_token | Y | string | Your `public_token`, obtained from the Link `onSuccess` callback or `/sandbox/item/public_token/create`. | &nbsp; | &nbsp; |

# ItemPublicTokenExchangeResponse
ItemPublicTokenExchangeResponse defines the response schema for `/item/public_token/exchange`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| item_id | Y | string | The `item_id` value of the Item associated with the returned `access_token` | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# ProcessorTokenCreateRequest
ProcessorTokenCreateRequest defines the request schema for `/processor/token/create`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| account_id | Y | string | The `account_id` value obtained from the `onSuccess` callback in Link | &nbsp; | &nbsp; |
| processor | Y | enum | The processor you are integrating with. | <ul><li>achq</li><li>alpaca</li><li>astra</li><li>check</li><li>checkbook</li><li>circle</li><li>drivewealth</li><li>dwolla</li><li>galileo</li><li>lithic</li><li>modern_treasury</li><li>moov</li><li>ocrolus</li><li>prime_trust</li><li>rize</li><li>sila_money</li><li>svb_api</li><li>treasury_prime</li><li>unit</li><li>vesta</li><li>vopay</li><li>wyre</li></ul> | &nbsp; |

# ProcessorTokenCreateResponse
ProcessorTokenCreateResponse defines the response schema for `/processor/token/create` and `/processor/apex/processor_token/create`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| processor_token | Y | string | The `processor_token` that can then be used by the Plaid partner to make API requests | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# ProcessorStripeBankAccountTokenCreateRequest
ProcessorStripeBankAccountTokenCreateRequest defines the request schema for `/processor/stripe/bank_account/create`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| account_id | Y | string | The `account_id` value obtained from the `onSuccess` callback in Link | &nbsp; | &nbsp; |

# ProcessorStripeBankAccountTokenCreateResponse
ProcessorStripeBankAccountTokenCreateResponse defines the response schema for `/processor/stripe/bank_account/create`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| stripe_bank_account_token | Y | string | A token that can be sent to Stripe for use in making API calls to Plaid | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# ItemImportRequest
ItemImportRequest defines the request schema for `/item/import`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| products | Y | array[] of Products | Array of product strings | <ul><li>minItems : 1</li></ul> | &nbsp; |
| user_auth | Y | ItemImportRequestUserAuth | &nbsp; | &nbsp; | &nbsp; |
| options | &nbsp; | ItemImportRequestOptions | &nbsp; | &nbsp; | &nbsp; |

# ItemImportRequestOptions
An optional object to configure `/item/import` request.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| webhook | &nbsp; | string | Specifies a webhook URL to associate with an Item. Plaid fires a webhook if credentials fail.<br/> | &nbsp; | &nbsp; |

# ItemImportRequestUserAuth
Object of user ID and auth token pair, permitting Plaid to aggregate a user’s accounts


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| user_id | Y | string | Opaque user identifier | &nbsp; | &nbsp; |
| auth_token | Y | string | Authorization token Plaid will use to aggregate this user’s accounts | &nbsp; | &nbsp; |

# ItemImportResponse
ItemImportResponse defines the response schema for `/item/import`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# LinkTokenGetRequest
LinkTokenGetRequest defines the request schema for `/link/token/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| link_token | Y | string | A `link_token` from a previous invocation of `/link/token/create` | &nbsp; | &nbsp; |

# LinkTokenCreateRequest
LinkTokenCreateRequest defines the request schema for `/link/token/create`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_name | Y | string | CONSTANT The name of your application, as it should be displayed in Link. Maximum length of 30 characters. If a value longer than 30 characters is provided, Link will display "This Application" instead. | &nbsp; | &nbsp; |
| language | Y | string | The language that Link should be displayed in.<br/><br/>Supported languages are:<br/>- English (`'en'`)<br/>- French (`'fr'`)<br/>- Spanish (`'es'`)<br/>- Dutch (`'nl'`)<br/>- German(`'de'`)<br/><br/>When using a Link customization, the language configured here must match the setting in the customization, or the customization will not be applied. | &nbsp; | &nbsp; |
| country_codes | Y | array[] of CountryCode | Specify an array of Plaid-supported country codes using the ISO-3166-1 alpha-2 country code standard. Institutions from all listed countries will be shown.  Supported country codes are: `US`, `CA`, `DE`, `ES`, `FR`, `GB`, `IE`, `NL`. For a complete mapping of supported products by country, see https://plaid.com/global/.<br/><br/>If Link is launched with multiple country codes, only products that you are enabled for in all countries will be used by Link. Note that while all countries are enabled by default in Sandbox and Development, in Production only US and Canada are enabled by default. To gain access to European institutions in the Production environment, [file a product access Support ticket](https://dashboard.plaid.com/support/new/product-and-development/product-troubleshooting/request-product-access) via the Plaid dashboard. If you initialize with a European country code, your users will see the European consent panel during the Link flow.<br/><br/>If using a Link customization, make sure the country codes in the customization match those specified in `country_codes`. If both `country_codes` and a Link customization are used, the value in `country_codes` may override the value in the customization.<br/><br/>If using the Auth features Instant Match, Same-day Micro-deposits, or Automated Micro-deposits, `country_codes` must be set to `['US']`. | <ul><li>minItems : 1</li></ul> | &nbsp; |
| user | Y | LinkTokenCreateRequestUser | &nbsp; | &nbsp; | &nbsp; |
| products | &nbsp; | array[] of Products | List of Plaid product(s) you wish to use. If launching Link in update mode, should be omitted; required otherwise. Valid products are:<br/><br/>`transactions`, `auth`, `identity`, `assets`, `investments`, `liabilities`, `payment_initiation`, `deposit_switch`, `income_verification`, `transfer`<br/><br/>`balance` is *not* a valid value, the Balance product does not require explicit initalization and will automatically be initialized when any other product is initialized.<br/><br/>Only institutions that support *all* requested products will be shown in Link; to maximize the number of institutions listed, it is recommended to initialize Link with the minimal product set required for your use case. Additional products can be added after Link initialization by calling the relevant endpoints. For details and exceptions, see [Choosing when to initialize products](https://plaid.com/docs/link/best-practices/#choosing-when-to-initialize-products).<br/><br/>Note that, unless you have opted to disable Instant Match support, institutions that support Instant Match will also be shown in Link if `auth` is specified as a product, even though these institutions do not contain `auth` in their product array.<br/><br/>In Production, you will be billed for each product that you specify when initializing Link. Note that a product cannot be removed from an Item once the Item has been initialized with that product. To stop billing on an Item for subscription-based products, such as Liabilities, Investments, and Transactions, remove the Item via `/item/remove`. | <ul><li>uniqueItems : true</li></ul> | &nbsp; |
| webhook | &nbsp; | string | The destination URL to which any webhooks should be sent. | &nbsp; | &nbsp; |
| access_token | &nbsp; | string | The `access_token` associated with the Item to update, used when updating or modifying an existing `access_token`. Used when launching Link in update mode, when completing the Same-day (manual) Micro-deposit flow, or (optionally) when initializing Link as part of the Payment Initiation (UK and Europe) flow. | &nbsp; | &nbsp; |
| link_customization_name | &nbsp; | string | The name of the Link customization from the Plaid Dashboard to be applied to Link. If not specified, the `default` customization will be used. When using a Link customization, the language in the customization must match the language selected via the `language` parameter, and the countries in the customization should match the country codes selected via `country_codes`. | &nbsp; | &nbsp; |
| redirect_uri | &nbsp; | string | A URI indicating the destination where a user should be forwarded after completing the Link flow; used to support OAuth authentication flows when launching Link in the browser or via a webview. The `redirect_uri` should not contain any query parameters. When used in Production or Development, must be an https URI. To specify any subdomain, use `*` as a wildcard character, e.g. `https://*.example.com/oauth.html`. If `android_package_name` is specified, this field should be left blank.  Note that any redirect URI must also be added to the Allowed redirect URIs list in the [developer dashboard](https://dashboard.plaid.com/team/api). | &nbsp; | &nbsp; |
| account_filters | &nbsp; | LinkTokenAccountFilters | &nbsp; | &nbsp; | &nbsp; |
| institution_id | &nbsp; | string | Used for certain Europe-only configurations, as well as certain legacy use cases in other regions. | &nbsp; | &nbsp; |
| auth | &nbsp; | LinkTokenCreateRequestAuth | &nbsp; | &nbsp; | &nbsp; |
| transfer | &nbsp; | LinkTokenCreateRequestTransfer | &nbsp; | &nbsp; | &nbsp; |
| update | &nbsp; | LinkTokenCreateRequestUpdate | &nbsp; | &nbsp; | &nbsp; |

# LinkTokenAccountFilters
By default, Link will provide limited account filtering: it will only display Institutions that are compatible with all products supplied in the `products` parameter of `/link/token/create`, and, if `auth` is specified in the `products` array, will also filter out accounts other than `checking` and `savings` accounts on the Account Select pane. You can further limit the accounts shown in Link by using `account_filters` to specify the account subtypes to be shown in Link. Only the specified subtypes will be shown. This filtering applies to both the Account Select view (if enabled) and the Institution Select view. Institutions that do not support the selected subtypes will be omitted from Link. To indicate that all subtypes should be shown, use the value `"all"`. If the `account_filters` filter is used, any account type for which a filter is not specified will be entirely omitted from Link. For a full list of valid types and subtypes, see the [Account schema](https://plaid.com/docs/api/accounts#accounts-schema).

For institutions using OAuth, the filter will not affect the list of accounts shown by the bank in the OAuth window.



## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| depository | &nbsp; | DepositoryFilter | &nbsp; | &nbsp; | &nbsp; |
| credit | &nbsp; | CreditFilter | &nbsp; | &nbsp; | &nbsp; |

# LinkTokenCreateRequestTransfer
Specifies options for initializing Link for use with the Transfer product.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| intent_id | &nbsp; | string | The `id` returned by the `/transfer/intent/create` endpoint. | &nbsp; | &nbsp; |

# LinkTokenCreateRequestAuth
Specifies options for initializing Link for use with the Auth product. This field is currently only required if using the Flexible Auth product (currently in closed beta).


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| flow_type | Y | enum | The optional Auth flow to use. Currently only used to enable Flexible Auth. | <ul><li>FLEXIBLE_AUTH</li></ul> | &nbsp; |

# LinkTokenCreateRequestUser
An object specifying information about the end user who will be linking their account.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_user_id | Y | string | A unique ID representing the end user. Typically this will be a user ID number from your application. Personally identifiable information, such as an email address or phone number, should not be used in the `client_user_id`. It is currently used as a means of searching logs for the given user in the Plaid Dashboard. | &nbsp; | &nbsp; |
| legal_name | &nbsp; | string | The user's full legal name. This is an optional field used in the [returning user experience](https://plaid.com/docs/link/returning-user) to associate Items to the user. | &nbsp; | Richard Hendricks |
| phone_number | &nbsp; | string | The user's phone number in [E.164](https://en.wikipedia.org/wiki/E.164) format. This field is optional, but required to enable the [returning user experience](https://plaid.com/docs/link/returning-user). | &nbsp; | &nbsp; |
| phone_number_verified_time | &nbsp; | date-time | The date and time the phone number was verified in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format (`YYYY-MM-DDThh:mm:ssZ`). This field is optional, but required to enable any [returning user experience](https://plaid.com/docs/link/returning-user).<br/><br/> Only pass a verification time for a phone number that you have verified. If you have performed verification but don’t have the time, you may supply a signal value of the start of the UNIX epoch.<br/><br/> Example: `2020-01-01T00:00:00Z`<br/> | &nbsp; | &nbsp; |
| email_address | &nbsp; | string | The user's email address. This field is optional, but required to enable the [pre-authenticated returning user flow](https://plaid.com/docs/link/returning-user/#enabling-the-returning-user-experience). | &nbsp; | richard@piedpiper.con |
| email_address_verified_time | &nbsp; | date-time | The date and time the email address was verified in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format (`YYYY-MM-DDThh:mm:ssZ`). This is an optional field used in the [returning user experience](https://plaid.com/docs/link/returning-user).<br/><br/> Only pass a verification time for an email address that you have verified. If you have performed verification but don’t have the time, you may supply a signal value of the start of the UNIX epoch.<br/><br/> Example: `2020-01-01T00:00:00Z` | &nbsp; | &nbsp; |
| ssn | &nbsp; | string | To be provided in the format "ddd-dd-dddd". This field is optional and will support not-yet-implemented functionality for new products. | &nbsp; | &nbsp; |
| date_of_birth | &nbsp; | date | To be provided in the format "yyyy-mm-dd". This field is optional and will support not-yet-implemented functionality for new products. | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | &nbsp; |

# LinkTokenCreateRequestUpdate
Specifies options for initializing Link for [update mode](https://plaid.com/docs/link/update-mode).


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_selection_enabled | &nbsp; | boolean | If `true`, enables [update mode with Account Select](https://plaid.com/docs/link/update-mode/#using-update-mode-to-request-new-accounts). | &nbsp; | &nbsp; |

# LinkTokenCreateRequestAccountSubtypes
By default, Link will only display account types that are compatible with all products supplied in the `products` parameter of `/link/token/create`. You can further limit the accounts shown in Link by using `account_filters` to specify the account subtypes to be shown in Link. Only the specified subtypes will be shown. This filtering applies to both the Account Select view (if enabled) and the Institution Select view. Institutions that do not support the selected subtypes will be omitted from Link. To indicate that all subtypes should be shown, use the value `"all"`. If the `account_filters` filter is used, any account type for which a filter is not specified will be entirely omitted from Link.

For a full list of valid types and subtypes, see the [Account schema](https://plaid.com/docs/api/accounts#accounts-schema).

For institutions using OAuth, the filter will not affect the list of institutions or accounts shown by the bank in the OAuth window.



## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| depository | &nbsp; | object | A filter to apply to `depository`-type accounts | &nbsp; | &nbsp; |
| credit | &nbsp; | object | A filter to apply to `credit`-type accounts | &nbsp; | &nbsp; |

# LinkTokenGetResponse
LinkTokenGetResponse defines the response schema for `/link/token/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| link_token | Y | string | A `link_token`, which can be supplied to Link in order to initialize it and receive a `public_token`, which can be exchanged for an `access_token`. | &nbsp; | &nbsp; |
| created_at | Y | date-time | The creation timestamp for the `link_token`, in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format. | &nbsp; | &nbsp; |
| expiration | Y | date-time | The expiration timestamp for the `link_token`, in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format. | &nbsp; | &nbsp; |
| metadata | Y | LinkTokenGetMetadataResponse | &nbsp; | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# LinkTokenGetMetadataResponse
An object specifying the arguments originally provided to the `/link/token/create` call.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| initial_products | Y | array[] of Products | The `products` specified in the `/link/token/create` call. | &nbsp; | &nbsp; |
| webhook | Y | string | The `webhook` specified in the `/link/token/create` call. | &nbsp; | &nbsp; |
| country_codes | Y | array[] of CountryCode | The `country_codes` specified in the `/link/token/create` call. | &nbsp; | &nbsp; |
| language | Y | string | The `language` specified in the `/link/token/create` call. | &nbsp; | &nbsp; |
| account_filters | &nbsp; | AccountFiltersResponse | &nbsp; | &nbsp; | &nbsp; |
| redirect_uri | Y | string | The `redirect_uri` specified in the `/link/token/create` call. | &nbsp; | &nbsp; |
| client_name | Y | string | The `client_name` specified in the `/link/token/create` call. | &nbsp; | &nbsp; |

# LinkTokenCreateResponse
LinkTokenCreateResponse defines the response schema for `/link/token/create`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| link_token | Y | string | A `link_token`, which can be supplied to Link in order to initialize it and receive a `public_token`, which can be exchanged for an `access_token`. | &nbsp; | &nbsp; |
| expiration | Y | date-time | The expiration date for the `link_token`, in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format. A `link_token` created to generate a `public_token` that will be exchanged for a new `access_token` expires after 4 hours. A `link_token` created for an existing Item (such as when updating an existing `access_token` by launching Link in update mode) expires after 30 minutes. | &nbsp; | &nbsp; |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# Item
Metadata about the Item.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| item_id | Y | string | The Plaid Item ID. The `item_id` is always unique; linking the same account at the same institution twice will result in two Items with different `item_id` values. Like all Plaid identifiers, the `item_id` is case-sensitive. | &nbsp; | &nbsp; |
| institution_id | &nbsp; | string | The Plaid Institution ID associated with the Item. Field is `null` for Items created via Same Day Micro-deposits. | &nbsp; | &nbsp; |
| webhook | Y | string | The URL registered to receive webhooks for the Item. | &nbsp; | &nbsp; |
| error | Y | Error | &nbsp; | &nbsp; | &nbsp; |
| available_products | Y | array[] of Products | A list of products available for the Item that have not yet been accessed. | &nbsp; | &nbsp; |
| billed_products | Y | array[] of Products | A list of products that have been billed for the Item. Note - `billed_products` is populated in all environments but only requests in Production are billed.<br/> | &nbsp; | &nbsp; |
| products | &nbsp; | array[] of Products | A list of authorized products for the Item.<br/> | &nbsp; | &nbsp; |
| consent_expiration_time | Y | date-time | The RFC 3339 timestamp after which the consent provided by the end user will expire. Upon consent expiration, the item will enter the `ITEM_LOGIN_REQUIRED` error state. To circumvent the `ITEM_LOGIN_REQUIRED` error and maintain continuous consent, the end user can reauthenticate via Link’s update mode in advance of the consent expiration time.<br/><br/>Note - This is only relevant for certain OAuth-based institutions. For all other institutions, this field will be null.<br/> | &nbsp; | &nbsp; |
| update_type | Y | enum | Indicates whether an Item requires user interaction to be updated, which can be the case for Items with some forms of two-factor authentication.<br/><br/>`background` - Item can be updated in the background<br/><br/>`user_present_required` - Item requires user interaction to be updated | <ul><li>background</li><li>user_present_required</li></ul> | &nbsp; |

# Error
We use standard HTTP response codes for success and failure notifications, and our errors are further classified by `error_type`. In general, 200 HTTP codes correspond to success, 40X codes are for developer- or user-related failures, and 50X codes are for Plaid-related issues.  Error fields will be `null` if no error has occurred.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| error_type | Y | enum | A broad categorization of the error. Safe for programatic use. | <ul><li>INVALID_REQUEST</li><li>INVALID_RESULT</li><li>INVALID_INPUT</li><li>INSTITUTION_ERROR</li><li>RATE_LIMIT_EXCEEDED</li><li>API_ERROR</li><li>ITEM_ERROR</li><li>ASSET_REPORT_ERROR</li><li>RECAPTCHA_ERROR</li><li>OAUTH_ERROR</li><li>PAYMENT_ERROR</li><li>BANK_TRANSFER_ERROR</li><li>INCOME_VERIFICATION_ERROR</li></ul> | &nbsp; |
| error_code | Y | string | The particular error code. Safe for programmatic use. | &nbsp; | &nbsp; |
| error_message | Y | string | A developer-friendly representation of the error code. This may change over time and is not safe for programmatic use. | &nbsp; | &nbsp; |
| display_message | Y | string | A user-friendly representation of the error code. `null` if the error is not related to user action.<br/><br/>This may change over time and is not safe for programmatic use. | &nbsp; | &nbsp; |
| request_id | &nbsp; | string | A unique ID identifying the request, to be used for troubleshooting purposes. This field will be omitted in errors provided by webhooks. | &nbsp; | &nbsp; |
| causes | &nbsp; | array[] of  | In the Assets product, a request can pertain to more than one Item. If an error is returned for such a request, `causes` will return an array of errors containing a breakdown of these errors on the individual Item level, if any can be identified.<br/><br/>`causes` will only be provided for the `error_type` `ASSET_REPORT_ERROR`. `causes` will also not be populated inside an error nested within a `warning` object. | &nbsp; | &nbsp; |
| status | &nbsp; | number | The HTTP status code associated with the error. This will only be returned in the response body when the error information is provided via a webhook. | &nbsp; | &nbsp; |
| documentation_url | &nbsp; | string | The URL of a Plaid documentation page with more information about the error | &nbsp; | &nbsp; |
| suggested_action | &nbsp; | string | Suggested steps for resolving the error | &nbsp; | &nbsp; |

# ItemStatusNullable
&nbsp;


# ItemStatusTransactions
Information about the last successful and failed transactions update for the Item.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| last_successful_update | &nbsp; | date-time | [ISO 8601](https://wikipedia.org/wiki/ISO_8601) timestamp of the last successful transactions update for the Item. The status will update each time Plaid successfully connects with the institution, regardless of whether any new data is available in the update. | &nbsp; | &nbsp; |
| last_failed_update | &nbsp; | date-time | [ISO 8601](https://wikipedia.org/wiki/ISO_8601) timestamp of the last failed transactions update for the Item. The status will update each time Plaid fails an attempt to connect with the institution, regardless of whether any new data is available in the update. | &nbsp; | &nbsp; |

# ItemStatusInvestments
Information about the last successful and failed investments update for the Item.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| last_successful_update | &nbsp; | date-time | [ISO 8601](https://wikipedia.org/wiki/ISO_8601) timestamp of the last successful investments update for the Item. The status will update each time Plaid successfully connects with the institution, regardless of whether any new data is available in the update. | &nbsp; | &nbsp; |
| last_failed_update | &nbsp; | date-time | [ISO 8601](https://wikipedia.org/wiki/ISO_8601) timestamp of the last failed investments update for the Item. The status will update each time Plaid fails an attempt to connect with the institution, regardless of whether any new data is available in the update. | &nbsp; | &nbsp; |

# ItemStatusLastWebhook
Information about the last webhook fired for the Item.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| sent_at | &nbsp; | date-time | [ISO 8601](https://wikipedia.org/wiki/ISO_8601) timestamp of when the webhook was fired.<br/> | &nbsp; | &nbsp; |
| code_sent | &nbsp; | string | The last webhook code sent. | &nbsp; | &nbsp; |

# ItemStatus
An object with information about the status of the Item.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| investments | &nbsp; | ItemStatusInvestments | &nbsp; | &nbsp; | &nbsp; |
| transactions | &nbsp; | ItemStatusTransactions | &nbsp; | &nbsp; | &nbsp; |
| last_webhook | &nbsp; | ItemStatusLastWebhook | &nbsp; | &nbsp; | &nbsp; |

# AccountBase
A single account at a financial institution.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_id | Y | string | Plaid’s unique identifier for the account. This value will not change unless Plaid can't reconcile the account with the data returned by the financial institution. This may occur, for example, when the name of the account changes. If this happens a new `account_id` will be assigned to the account.<br/><br/>The `account_id` can also change if the `access_token` is deleted and the same credentials that were used to generate that `access_token` are used to generate a new `access_token` on a later date. In that case, the new `account_id` will be different from the old `account_id`.<br/><br/>If an account with a specific `account_id` disappears instead of changing, the account is likely closed. Closed accounts are not returned by the Plaid API.<br/><br/>Like all Plaid identifiers, the `account_id` is case sensitive. | &nbsp; | &nbsp; |
| balances | Y | AccountBalance | &nbsp; | &nbsp; | &nbsp; |
| mask | Y | string | The last 2-4 alphanumeric characters of an account's official account number. Note that the mask may be non-unique between an Item's accounts, and it may also not match the mask that the bank displays to the user. | &nbsp; | &nbsp; |
| name | Y | string | The name of the account, either assigned by the user or by the financial institution itself | &nbsp; | &nbsp; |
| official_name | Y | string | The official name of the account as given by the financial institution | &nbsp; | &nbsp; |
| type | Y | AccountType | &nbsp; | &nbsp; | &nbsp; |
| subtype | Y | AccountSubtype | &nbsp; | &nbsp; | &nbsp; |
| verification_status | &nbsp; | enum | The current verification status of an Auth Item initiated through Automated or Manual micro-deposits.  Returned for Auth Items only.<br/><br/>`pending_automatic_verification`: The Item is pending automatic verification<br/><br/>`pending_manual_verification`: The Item is pending manual micro-deposit verification. Items remain in this state until the user successfully verifies the two amounts.<br/><br/>`automatically_verified`: The Item has successfully been automatically verified	<br/><br/>`manually_verified`: The Item has successfully been manually verified<br/><br/>`verification_expired`: Plaid was unable to automatically verify the deposit within 7 calendar days and will no longer attempt to validate the Item. Users may retry by submitting their information again through Link.<br/><br/>`verification_failed`: The Item failed manual micro-deposit verification because the user exhausted all 3 verification attempts. Users may retry by submitting their information again through Link.	<br/>	 | <ul><li>automatically_verified</li><li>pending_automatic_verification</li><li>pending_manual_verification</li><li>manually_verified</li><li>verification_expired</li><li>verification_failed</li></ul> | &nbsp; |

# AccountBalance
A set of fields describing the balance for an account. Balance information may be cached unless the balance object was returned by `/accounts/balance/get`.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| available | Y | number | The amount of funds available to be withdrawn from the account, as determined by the financial institution.<br/><br/>For `credit`-type accounts, the `available` balance typically equals the `limit` less the `current` balance, less any pending outflows plus any pending inflows.<br/><br/>For `depository`-type accounts, the `available` balance typically equals the `current` balance less any pending outflows plus any pending inflows. For `depository`-type accounts, the `available` balance does not include the overdraft limit.<br/><br/>For `investment`-type accounts (or `brokerage`-type accounts for API versions 2018-05-22 and earlier), the `available` balance is the total cash available to withdraw as presented by the institution.<br/><br/>Note that not all institutions calculate the `available`  balance. In the event that `available` balance is unavailable, Plaid will return an `available` balance value of `null`.<br/><br/>Available balance may be cached and is not guaranteed to be up-to-date in realtime unless the value was returned by `/accounts/balance/get`.<br/><br/>If `current` is `null` this field is guaranteed not to be `null`. | &nbsp; | &nbsp; |
| current | Y | number | The total amount of funds in or owed by the account.<br/><br/>For `credit`-type accounts, a positive balance indicates the amount owed; a negative amount indicates the lender owing the account holder.<br/><br/>For `loan`-type accounts, the current balance is the principal remaining on the loan, except in the case of student loan accounts at Sallie Mae (`ins_116944`). For Sallie Mae student loans, the account's balance includes both principal and any outstanding interest.<br/><br/>For `investment`-type accounts (or `brokerage`-type accounts for API versions 2018-05-22 and earlier), the current balance is the total value of assets as presented by the institution.<br/><br/>Note that balance information may be cached unless the value was returned by `/accounts/balance/get`; if the Item is enabled for Transactions, the balance will be at least as recent as the most recent Transaction update. If you require realtime balance information, use the `available` balance as provided by `/accounts/balance/get`.<br/><br/>When returned by `/accounts/balance/get`, this field may be `null`. When this happens, `available` is guaranteed not to be `null`. | &nbsp; | &nbsp; |
| limit | Y | number | For `credit`-type accounts, this represents the credit limit.<br/><br/>For `depository`-type accounts, this represents the pre-arranged overdraft limit, which is common for current (checking) accounts in Europe.<br/><br/>In North America, this field is typically only available for `credit`-type accounts. | &nbsp; | &nbsp; |
| iso_currency_code | Y | string | The ISO-4217 currency code of the balance. Always null if `unofficial_currency_code` is non-null. | &nbsp; | &nbsp; |
| unofficial_currency_code | Y | string | The unofficial currency code associated with the balance. Always null if `iso_currency_code` is non-null. Unofficial currency codes are used for currencies that do not have official ISO currency codes, such as cryptocurrencies and the currencies of certain countries.<br/><br/>See the [currency code schema](https://plaid.com/docs/api/accounts#currency-code-schema) for a full listing of supported `unofficial_currency_code`s. | &nbsp; | &nbsp; |
| last_updated_datetime | &nbsp; | date-time | Timestamp in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format (`YYYY-MM-DDTHH:mm:ssZ`) indicating the last time that the balance for the given account has been updated<br/><br/>This is currently only provided when the `min_last_updated_datetime` is passed when calling `/accounts/balance/get` for `ins_128026` (Capital One). | &nbsp; | &nbsp; |

# NumbersACH
Identifying information for transferring money to or from a US account via ACH or wire transfer.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_id | Y | string | The Plaid account ID associated with the account numbers | &nbsp; | &nbsp; |
| account | Y | string | The ACH account number for the account.<br/><br/>Note that when using OAuth with Chase Bank (`ins_56`), Chase will issue "tokenized" routing and account numbers, which are not the user's actual account and routing numbers. These tokenized numbers should work identically to normal account and routing numbers. The digits returned in the `mask` field will continue to reflect the actual account number, rather than the tokenized account number; for this reason, when displaying account numbers to the user to help them identify their account in your UI, always use the `mask` rather than truncating the `account` number. If a user revokes their permissions to your app, the tokenized numbers will continue to work for ACH deposits, but not withdrawals. | &nbsp; | &nbsp; |
| routing | Y | string | The ACH routing number for the account. If the institution is `ins_56`, this may be a tokenized routing number. For more information, see the description of the `account` field. | &nbsp; | &nbsp; |
| wire_routing | Y | string | The wire transfer routing number for the account, if available | &nbsp; | &nbsp; |

# NumbersACHNullable
&nbsp;


# RemovedTransaction
A representation of a removed transaction


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| transaction_id | &nbsp; | string | The ID of the removed transaction. | &nbsp; | &nbsp; |

# TransactionBase
A representation of a transaction


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| pending_transaction_id | &nbsp; | string | The ID of a posted transaction's associated pending transaction, where applicable. | &nbsp; | &nbsp; |
| category_id | &nbsp; | string | The ID of the category to which this transaction belongs. See [Categories](https://plaid.com/docs/#category-overview).<br/><br/>If the `transactions` object was returned by an Assets endpoint such as `/asset_report/get/` or `/asset_report/pdf/get`, this field will only appear in an Asset Report with Insights. | &nbsp; | &nbsp; |
| category | &nbsp; | array[] of strings | A hierarchical array of the categories to which this transaction belongs. See [Categories](https://plaid.com/docs/#category-overview).<br/><br/>If the `transactions` object was returned by an Assets endpoint such as `/asset_report/get/` or `/asset_report/pdf/get`, this field will only appear in an Asset Report with Insights. | &nbsp; | &nbsp; |
| location | &nbsp; | Location | &nbsp; | &nbsp; | &nbsp; |
| payment_meta | &nbsp; | PaymentMeta | &nbsp; | &nbsp; | &nbsp; |
| account_owner | &nbsp; | string | The name of the account owner. This field is not typically populated and only relevant when dealing with sub-accounts. | &nbsp; | &nbsp; |
| name | &nbsp; | string | The merchant name or transaction description.<br/><br/>If the `transactions` object was returned by a Transactions endpoint such as `/transactions/get`, this field will always appear. If the `transactions` object was returned by an Assets endpoint such as `/asset_report/get/` or `/asset_report/pdf/get`, this field will only appear in an Asset Report with Insights. | &nbsp; | &nbsp; |
| original_description | &nbsp; | string | The string returned by the financial institution to describe the transaction. For transactions returned by `/transactions/get`, this field is in beta and will be omitted unless the client is both enrolled in the closed beta program and has set `options.include_original_description` to `true`. | &nbsp; | &nbsp; |
| account_id | Y | string | The ID of the account in which this transaction occurred. | &nbsp; | &nbsp; |
| amount | Y | number | The settled value of the transaction, denominated in the account's currency, as stated in `iso_currency_code` or `unofficial_currency_code`. Positive values when money moves out of the account; negative values when money moves in. For example, debit card purchases are positive; credit card payments, direct deposits, and refunds are negative. | &nbsp; | &nbsp; |
| iso_currency_code | Y | string | The ISO-4217 currency code of the transaction. Always `null` if `unofficial_currency_code` is non-null. | &nbsp; | &nbsp; |
| unofficial_currency_code | Y | string | The unofficial currency code associated with the transaction. Always `null` if `iso_currency_code` is non-`null`. Unofficial currency codes are used for currencies that do not have official ISO currency codes, such as cryptocurrencies and the currencies of certain countries.<br/><br/>See the [currency code schema](https://plaid.com/docs/api/accounts#currency-code-schema) for a full listing of supported `iso_currency_code`s. | &nbsp; | &nbsp; |
| date | Y | date | For pending transactions, the date that the transaction occurred; for posted transactions, the date that the transaction posted. Both dates are returned in an [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format ( `YYYY-MM-DD` ). | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | &nbsp; |
| pending | Y | boolean | When `true`, identifies the transaction as pending or unsettled. Pending transaction details (name, type, amount, category ID) may change before they are settled. | &nbsp; | &nbsp; |
| transaction_id | Y | string | The unique ID of the transaction. Like all Plaid identifiers, the `transaction_id` is case sensitive. | &nbsp; | &nbsp; |
| merchant_name | &nbsp; | string | The merchant name, as extracted by Plaid from the `name` field. | &nbsp; | &nbsp; |
| check_number | &nbsp; | string | The check number of the transaction. This field is only populated for check transactions. | &nbsp; | &nbsp; |

# Transaction
A representation of a transaction


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| payment_channel | Y | enum | The channel used to make a payment.<br/>`online:` transactions that took place online.<br/><br/>`in store:` transactions that were made at a physical location.<br/><br/>`other:` transactions that relate to banks, e.g. fees or deposits.<br/><br/>This field replaces the `transaction_type` field.<br/> | <ul><li>online</li><li>in store</li><li>other</li></ul> | &nbsp; |
| authorized_date | Y | date | The date that the transaction was authorized. Dates are returned in an [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format ( `YYYY-MM-DD` ). | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | &nbsp; |
| authorized_datetime | Y | date-time | Date and time when a transaction was authorized in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format ( `YYYY-MM-DDTHH:mm:ssZ` ).<br/><br/>This field is only populated for UK institutions. For institutions in other countries, will be `null`. | &nbsp; | &nbsp; |
| datetime | Y | date-time | Date and time when a transaction was posted in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format ( `YYYY-MM-DDTHH:mm:ssZ` ).<br/><br/>This field is only populated for UK institutions. For institutions in other countries, will be `null`. | &nbsp; | &nbsp; |
| transaction_code | Y | TransactionCode | &nbsp; | &nbsp; | &nbsp; |
| personal_finance_category | &nbsp; | undefined | &nbsp; | &nbsp; | &nbsp; |

# Location
A representation of where a transaction took place


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| address | Y | string | The street address where the transaction occurred. | &nbsp; | &nbsp; |
| city | Y | string | The city where the transaction occurred. | &nbsp; | &nbsp; |
| region | Y | string | The region or state where the transaction occurred. In API versions 2018-05-22 and earlier, this field is called `state`. | &nbsp; | &nbsp; |
| postal_code | Y | string | The postal code where the transaction occurred. In API versions 2018-05-22 and earlier, this field is called `zip`. | &nbsp; | &nbsp; |
| country | Y | string | The ISO 3166-1 alpha-2 country code where the transaction occurred. | &nbsp; | &nbsp; |
| lat | Y | number | The latitude where the transaction occurred. | &nbsp; | &nbsp; |
| lon | Y | number | The longitude where the transaction occurred. | &nbsp; | &nbsp; |
| store_number | Y | string | The merchant defined store number where the transaction occurred. | &nbsp; | &nbsp; |

# TransactionStream
A grouping of related transactions


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_id | Y | string | The ID of the account to which the stream belongs | &nbsp; | &nbsp; |
| stream_id | Y | string | A unique id for the stream | &nbsp; | &nbsp; |
| category_id | Y | string | The ID of the category to which this transaction belongs. See [Categories](https://plaid.com/docs/#category-overview). | &nbsp; | &nbsp; |
| category | Y | array[] of strings | A hierarchical array of the categories to which this transaction belongs. See [Categories](https://plaid.com/docs/#category-overview). | &nbsp; | &nbsp; |
| description | Y | string | A description of the transaction stream. | &nbsp; | &nbsp; |
| first_date | Y | date | The posted date of the earliest transaction in the stream. | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | &nbsp; |
| last_date | Y | date | The posted date of the latest transaction in the stream. | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | &nbsp; |
| frequency | Y | RecurringTransactionFrequency | &nbsp; | &nbsp; | &nbsp; |
| transaction_ids | Y | array[] of strings | An array of Plaid transaction IDs belonging to the stream, sorted by posted date. | &nbsp; | &nbsp; |
| average_amount | Y | TransactionStreamAmount | &nbsp; | &nbsp; | &nbsp; |
| is_active | Y | boolean | indicates whether the transaction stream is still live. | &nbsp; | &nbsp; |

# TransactionStreamAmount
Object with data pertaining to an amount on the transaction stream.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| amount | &nbsp; | number | represents the numerical value of an amount. | &nbsp; | &nbsp; |
| iso_currency_code | &nbsp; | string | The ISO-4217 currency code of the amount. Always `null` if `unofficial_currency_code` is non-`null`.<br/><br/>See the [currency code schema](https://plaid.com/docs/api/accounts#currency-code-schema) for a full listing of supported `iso_currency_code`s. | &nbsp; | &nbsp; |
| unofficial_currency_code | &nbsp; | string | The unofficial currency code of the amount. Always `null` if `iso_currency_code` is non-`null`. Unofficial currency codes are used for currencies that do not have official ISO currency codes, such as cryptocurrencies and the currencies of certain countries. | &nbsp; | &nbsp; |

# Institution
Details relating to a specific financial institution


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| institution_id | Y | string | Unique identifier for the institution | &nbsp; | &nbsp; |
| name | Y | string | The official name of the institution | &nbsp; | &nbsp; |
| products | Y | array[] of Products | A list of the Plaid products supported by the institution. Note that only institutions that support Instant Auth will return `auth` in the product array; institutions that do not list `auth` may still support other Auth methods such as Instant Match or Automated Micro-deposit Verification. For more details, see [Full Auth coverage](https://plaid.com/docs/auth/coverage/). | &nbsp; | &nbsp; |
| country_codes | Y | array[] of CountryCode | A list of the country codes supported by the institution. | &nbsp; | &nbsp; |
| url | &nbsp; | string | The URL for the institution's website | &nbsp; | &nbsp; |
| primary_color | &nbsp; | string | Hexadecimal representation of the primary color used by the institution | &nbsp; | &nbsp; |
| logo | &nbsp; | string | Base64 encoded representation of the institution's logo | &nbsp; | &nbsp; |
| routing_numbers | Y | array[] of strings | A partial list of routing numbers associated with the institution. This list is provided for the purpose of looking up institutions by routing number. It is not comprehensive and should never be used as a complete list of routing numbers for an institution. | &nbsp; | &nbsp; |
| oauth | Y | boolean | Indicates that the institution has an OAuth login flow. This is primarily relevant to institutions with European country codes. | &nbsp; | &nbsp; |
| status | &nbsp; | InstitutionStatus | &nbsp; | &nbsp; | &nbsp; |
| auth_metadata | &nbsp; | AuthMetadata | &nbsp; | &nbsp; | &nbsp; |

# InstitutionStatus
The status of an institution is determined by the health of its Item logins, Transactions updates, Investments updates, Liabilities updates, Auth requests, Balance requests, Identity requests, Investments requests, and Liabilities requests. A login attempt is conducted during the initial Item add in Link. If there is not enough traffic to accurately calculate an institution's status, Plaid will return null rather than potentially inaccurate data.

Institution status is accessible in the Dashboard and via the API using the `/institutions/get_by_id` endpoint with the `include_status` option set to true. Note that institution status is not available in the Sandbox environment.



## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| item_logins | Y | ProductStatus | &nbsp; | &nbsp; | &nbsp; |
| transactions_updates | Y | ProductStatus | &nbsp; | &nbsp; | &nbsp; |
| auth | Y | ProductStatus | &nbsp; | &nbsp; | &nbsp; |
| balance | Y | ProductStatus | &nbsp; | &nbsp; | &nbsp; |
| identity | Y | ProductStatus | &nbsp; | &nbsp; | &nbsp; |
| investments_updates | Y | ProductStatus | &nbsp; | &nbsp; | &nbsp; |
| liabilities_updates | &nbsp; | ProductStatus | &nbsp; | &nbsp; | &nbsp; |
| liabilities | &nbsp; | ProductStatus | &nbsp; | &nbsp; | &nbsp; |
| investments | &nbsp; | ProductStatus | &nbsp; | &nbsp; | &nbsp; |
| health_incidents | &nbsp; | array[] of HealthIncident | Details of recent health incidents associated with the institution. | &nbsp; | &nbsp; |

# PaymentMeta
Transaction information specific to inter-bank transfers. If the transaction was not an inter-bank transfer, all fields will be `null`.

If the `transactions` object was returned by a Transactions endpoint such as `/transactions/get`, the `payment_meta` key will always appear, but no data elements are guaranteed. If the `transactions` object was returned by an Assets endpoint such as `/asset_report/get/` or `/asset_report/pdf/get`, this field will only appear in an Asset Report with Insights.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| reference_number | Y | string | The transaction reference number supplied by the financial institution. | &nbsp; | &nbsp; |
| ppd_id | Y | string | The ACH PPD ID for the payer. | &nbsp; | &nbsp; |
| payee | Y | string | For transfers, the party that is receiving the transaction. | &nbsp; | &nbsp; |
| by_order_of | Y | string | The party initiating a wire transfer. Will be `null` if the transaction is not a wire transfer. | &nbsp; | &nbsp; |
| payer | Y | string | For transfers, the party that is paying the transaction. | &nbsp; | &nbsp; |
| payment_method | Y | string | The type of transfer, e.g. 'ACH' | &nbsp; | &nbsp; |
| payment_processor | Y | string | The name of the payment processor | &nbsp; | &nbsp; |
| reason | Y | string | The payer-supplied description of the transfer. | &nbsp; | &nbsp; |

# Category
Information describing a transaction category


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| category_id | Y | string | An identifying number for the category. `category_id` is a Plaid-specific identifier and does not necessarily correspond to merchant category codes. | &nbsp; | &nbsp; |
| group | Y | string | `place` for physical transactions or `special` for other transactions such as bank charges. | &nbsp; | &nbsp; |
| hierarchy | Y | array[] of strings | A hierarchical array of the categories to which this `category_id` belongs. | &nbsp; | &nbsp; |

# PersonalFinanceCategory
Information describing the intent of the transaction. Most relevant for personal finance use cases, but not limited to such use cases. The field is currently in beta.

The complete category can be generated by concatenating primary and detailed categories.

This feature is currently in beta – to request access, contact transactions-feedback@plaid.com.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| primary | Y | string | A high level category that communicates the broad category of the transaction. | &nbsp; | &nbsp; |
| detailed | Y | string | Provides additional granularity to the primary categorization. | &nbsp; | &nbsp; |

# PhoneNumber
A phone number


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| data | Y | string | The phone number. | &nbsp; | &nbsp; |
| primary | Y | boolean | When `true`, identifies the phone number as the primary number on an account. | &nbsp; | &nbsp; |
| type | Y | enum | The type of phone number. | <ul><li>home</li><li>work</li><li>office</li><li>mobile</li><li>mobile1</li><li>other</li></ul> | &nbsp; |

# Email
An object representing an email address


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| data | Y | string | The email address. | &nbsp; | &nbsp; |
| primary | Y | boolean | When `true`, identifies the email address as the primary email on an account. | &nbsp; | &nbsp; |
| type | Y | enum | The type of email account as described by the financial institution. | <ul><li>primary</li><li>secondary</li><li>other</li></ul> | &nbsp; |

# Address
A physical mailing address.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| data | Y | AddressData | &nbsp; | &nbsp; | &nbsp; |
| primary | &nbsp; | boolean | When `true`, identifies the address as the primary address on an account. | &nbsp; | &nbsp; |

# AddressData
Data about the components comprising an address.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| city | Y | string | The full city name | &nbsp; | &nbsp; |
| region | Y | string | The region or state. In API versions 2018-05-22 and earlier, this field is called `state`.<br/>Example: `"NC"` | &nbsp; | &nbsp; |
| street | Y | string | The full street address<br/>Example: `"564 Main Street, APT 15"` | &nbsp; | &nbsp; |
| postal_code | Y | string | The postal code. In API versions 2018-05-22 and earlier, this field is called `zip`. | &nbsp; | &nbsp; |
| country | Y | string | The ISO 3166-1 alpha-2 country code | &nbsp; | &nbsp; |

# HistoricalBalance
An object representing a balance held by an account in the past


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| date | Y | date | The date of the calculated historical balance, in an [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format (YYYY-MM-DD) | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | &nbsp; |
| current | Y | number | The total amount of funds in the account, calculated from the `current` balance in the `balance` object by subtracting inflows and adding back outflows according to the posted date of each transaction.<br/><br/>If the account has any pending transactions, historical balance amounts on or after the date of the earliest pending transaction may differ if retrieved in subsequent Asset Reports as a result of those pending transactions posting. | &nbsp; | &nbsp; |
| iso_currency_code | Y | string | The ISO-4217 currency code of the balance. Always `null` if `unofficial_currency_code` is non-`null`. | &nbsp; | &nbsp; |
| unofficial_currency_code | Y | string | The unofficial currency code associated with the balance. Always `null` if `iso_currency_code` is non-`null`.<br/><br/>See the [currency code schema](https://plaid.com/docs/api/accounts#currency-code-schema) for a full listing of supported `iso_currency_code`s. | &nbsp; | &nbsp; |

# Owner
Data returned from the financial institution about the owner or owners of an account. Only the `names` array must be non-empty.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| names | Y | array[] of strings | A list of names associated with the account by the financial institution. These should always be the names of individuals, even for business accounts. If the name of a business is reported, please contact Plaid Support. In the case of a joint account, Plaid will make a best effort to report the names of all account holders.<br/><br/>If an Item contains multiple accounts with different owner names, some institutions will report all names associated with the Item in each account's `names` array. | &nbsp; | &nbsp; |
| phone_numbers | Y | array[] of PhoneNumber | A list of phone numbers associated with the account by the financial institution. May be an empty array if no relevant information is returned from the financial institution. | &nbsp; | &nbsp; |
| emails | Y | array[] of Email | A list of email addresses associated with the account by the financial institution. May be an empty array if no relevant information is returned from the financial institution. | &nbsp; | &nbsp; |
| addresses | Y | array[] of Address | Data about the various addresses associated with the account by the financial institution. May be an empty array if no relevant information is returned from the financial institution. | &nbsp; | &nbsp; |

# OwnerOverride
Data about the owner or owners of an account. Any fields not specified will be filled in with default Sandbox information.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| names | Y | array[] of strings | A list of names associated with the account by the financial institution. These should always be the names of individuals, even for business accounts. Note that the same name data will be used for all accounts associated with an Item. | &nbsp; | &nbsp; |
| phone_numbers | Y | array[] of PhoneNumber | A list of phone numbers associated with the account. | &nbsp; | &nbsp; |
| emails | Y | array[] of Email | A list of email addresses associated with the account. | &nbsp; | &nbsp; |
| addresses | Y | array[] of Address | Data about the various addresses associated with the account. | &nbsp; | &nbsp; |

# AuthMetadata
Metadata that captures information about the Auth features of an institution.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| supported_methods | Y | AuthSupportedMethods | &nbsp; | &nbsp; | &nbsp; |

# AuthSupportedMethods
Metadata specifically related to which auth methods an institution supports.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| instant_auth | Y | boolean | Indicates if instant auth is supported. | &nbsp; | &nbsp; |
| instant_match | Y | boolean | Indicates if instant match is supported. | &nbsp; | &nbsp; |
| automated_micro_deposits | Y | boolean | Indicates if automated microdeposits are supported. | &nbsp; | &nbsp; |

# ProductStatus
A representation of the status health of a request type. Auth requests, Balance requests, Identity requests, Investments requests, Liabilities requests, Transactions updates, Investments updates, Liabilities updates, and Item logins each have their own status object.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| breakdown | Y | ProductStatusBreakdown | &nbsp; | &nbsp; | &nbsp; |

# ProductStatusBreakdown
A detailed breakdown of the institution's performance for a request type. The values for `success`, `error_plaid`, and `error_institution` sum to 1.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| success | Y | number | The percentage of login attempts that are successful, expressed as a decimal. | &nbsp; | &nbsp; |
| error_plaid | Y | number | The percentage of logins that are failing due to an internal Plaid issue, expressed as a decimal.<br/> | &nbsp; | &nbsp; |
| error_institution | Y | number | The percentage of logins that are failing due to an issue in the institution's system, expressed as a decimal. | &nbsp; | &nbsp; |
| refresh_interval | &nbsp; | enum | The `refresh_interval` may be `DELAYED` or `STOPPED` even when the success rate is high. This value is only returned for Transactions status breakdowns. | <ul><li>NORMAL</li><li>DELAYED</li><li>STOPPED</li></ul> | &nbsp; |

# UserCustomPassword
Custom test accounts are configured with a JSON configuration object formulated according to the schema below. All fields are optional. Sending an empty object as a configuration will result in an account configured with random balances and transaction history.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| version | &nbsp; | string | The version of the password schema to use, possible values are 1 or 2. The default value is 2. You should only specify 1 if you know it is necessary for your test suite. | &nbsp; | &nbsp; |
| seed | Y | string | A seed, in the form of a string, that will be used to randomly generate account and transaction data, if this data is not specified using the `override_accounts` argument. If no seed is specified, the randomly generated data will be different each time.<br/><br/>Note that transactions data is generated relative to the Item's creation date. Different Items created on different dates with the same seed for transactions data will have different dates for the transactions. The number of days between each transaction and the Item creation will remain constant. For example, an Item created on December 15 might show a transaction on December 14. An Item created on December 20, using the same seed, would show that same transaction occurring on December 19. | &nbsp; | &nbsp; |
| override_accounts | Y | array[] of OverrideAccounts | An array of account overrides to configure the accounts for the Item. By default, if no override is specified, transactions and account data will be randomly generated based on the account type and subtype, and other products will have fixed or empty data. | &nbsp; | &nbsp; |
| mfa | Y | MFA | &nbsp; | &nbsp; | &nbsp; |
| recaptcha | Y | string | You may trigger a reCAPTCHA in Plaid Link in the Sandbox environment by using the recaptcha field. Possible values are `good` or `bad`. A value of `good` will result in successful Item creation and `bad` will result in a `RECAPTCHA_BAD` error to simulate a failed reCAPTCHA. Both values require the reCAPTCHA to be manually solved within Plaid Link. | &nbsp; | &nbsp; |
| force_error | Y | string | An error code to force on Item creation. Possible values are:<br/><br/>`"INSTITUTION_NOT_RESPONDING"`<br/>`"INSTITUTION_NO_LONGER_SUPPORTED"`<br/>`"INVALID_CREDENTIALS"`<br/>`"INVALID_MFA"`<br/>`"ITEM_LOCKED"`<br/>`"ITEM_LOGIN_REQUIRED"`<br/>`"ITEM_NOT_SUPPORTED"`<br/>`"INVALID_LINK_TOKEN"`<br/>`"MFA_NOT_SUPPORTED"`<br/>`"NO_ACCOUNTS"`<br/>`"PLAID_ERROR"`<br/>`"PRODUCTS_NOT_SUPPORTED"`<br/>`"USER_SETUP_REQUIRED"` | &nbsp; | &nbsp; |

# MFA
Specifies the multi-factor authentication settings to use with this test account


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| type | Y | string | Possible values are `device`, `selections`, or `questions`.<br/><br/>If value is `device`, the MFA answer is `1234`.<br/><br/>If value is `selections`, the MFA answer is always the first option.<br/><br/>If value is `questions`, the MFA answer is  `answer_<i>_<j>` for the j-th question in the i-th round, starting from 0. For example, the answer to the first question in the second round is `answer_1_0`. | &nbsp; | &nbsp; |
| question_rounds | Y | number | Number of rounds of questions. Required if value of `type` is `questions`.  | &nbsp; | &nbsp; |
| questions_per_round | Y | number | Number of questions per round. Required if value of `type` is `questions`. If value of type is `selections`, default value is 2. | &nbsp; | &nbsp; |
| selection_rounds | Y | number | Number of rounds of selections, used if `type` is `selections`. Defaults to 1. | &nbsp; | &nbsp; |
| selections_per_question | Y | number | Number of available answers per question, used if `type` is `selection`. Defaults to 2.<br/> | &nbsp; | &nbsp; |

# OverrideAccounts
Data to use to set values of test accounts. Some values cannot be specified in the schema and will instead will be calculated from other test data in order to achieve more consistent, realistic test data.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| type | Y | OverrideAccountType | &nbsp; | &nbsp; | &nbsp; |
| subtype | Y | AccountSubtype | &nbsp; | &nbsp; | &nbsp; |
| starting_balance | Y | number | If provided, the account will start with this amount as the current balance.<br/> | &nbsp; | &nbsp; |
| force_available_balance | Y | number | If provided, the account will always have this amount as its  available balance, regardless of current balance or changes in transactions over time. | &nbsp; | &nbsp; |
| currency | Y | string | ISO-4217 currency code. If provided, the account will be denominated in the given currency. Transactions will also be in this currency by default. | &nbsp; | &nbsp; |
| meta | Y | Meta | &nbsp; | &nbsp; | &nbsp; |
| numbers | Y | Numbers | &nbsp; | &nbsp; | &nbsp; |
| transactions | Y | array[] of TransactionOverride | Specify the list of transactions on the account. | &nbsp; | &nbsp; |
| identity | Y | OwnerOverride | &nbsp; | &nbsp; | &nbsp; |

# Meta
Allows specifying the metadata of the test account


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| name | Y | string | The account's name | &nbsp; | &nbsp; |
| official_name | Y | string | The account's official name | &nbsp; | &nbsp; |
| limit | Y | number | The account's limit | &nbsp; | &nbsp; |

# Numbers
Account and bank identifier number data used to configure the test account. All values are optional.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account | &nbsp; | string | Will be used for the account number. | &nbsp; | &nbsp; |
| ach_routing | &nbsp; | string | Must be a valid ACH routing number. | &nbsp; | &nbsp; |
| ach_wire_routing | &nbsp; | string | Must be a valid wire transfer routing number. | &nbsp; | &nbsp; |
| eft_institution | &nbsp; | string | EFT institution number. Must be specified alongside `eft_branch`. | &nbsp; | &nbsp; |
| eft_branch | &nbsp; | string | EFT branch number. Must be specified alongside `eft_institution`. | &nbsp; | &nbsp; |
| international_bic | &nbsp; | string | Bank identifier code (BIC). Must be specified alongside `international_iban`. | &nbsp; | &nbsp; |
| international_iban | &nbsp; | string | International bank account number (IBAN). If no account number is specified via `account`, will also be used as the account number by default. Must be specified alongside `international_bic`. | &nbsp; | &nbsp; |
| bacs_sort_code | &nbsp; | string | BACS sort code | &nbsp; | &nbsp; |

# TransactionOverride
Data to populate as test transaction data. If not specified, random transactions will be generated instead.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| date_transacted | Y | date | The date of the transaction, in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) (YYYY-MM-DD) format. Transactions in Sandbox will move from pending to posted once their transaction date has been reached. | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | &nbsp; |
| date_posted | Y | date | The date the transaction posted, in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) (YYYY-MM-DD) format. Posted dates in the past or present will result in posted transactions; posted dates in the future will result in pending transactions. | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | &nbsp; |
| amount | Y | number | The transaction amount. Can be negative. | &nbsp; | &nbsp; |
| description | Y | string | The transaction description. | &nbsp; | &nbsp; |
| currency | &nbsp; | string | The ISO-4217 format currency code for the transaction. | &nbsp; | &nbsp; |

# Recaptcha_RequiredError
The request was flagged by Plaid's fraud system, and requires additional verification to ensure they are not a bot.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| error_type | Y | string | RECAPTCHA_ERROR | &nbsp; | &nbsp; |
| error_code | Y | string | RECAPTCHA_REQUIRED | &nbsp; | &nbsp; |
| display_message | Y | string | &nbsp; | &nbsp; | &nbsp; |
| http_code | Y | string | 400 | &nbsp; | &nbsp; |
| link_user_experience | Y | string | Your user will be prompted to solve a Google reCAPTCHA challenge in the Link Recaptcha pane. If they solve the challenge successfully, the user's request is resubmitted and they are directed to the next Item creation step. | &nbsp; | &nbsp; |
| common_causes | Y | string | Plaid's fraud system detects abusive traffic and considers a variety of parameters throughout Item creation requests. When a request is considered risky or possibly fraudulent, Link presents a reCAPTCHA for the user to solve. | &nbsp; | &nbsp; |
| troubleshooting_steps | Y | string | Link will automatically guide your user through reCAPTCHA verification. As a general rule, we recommend instrumenting basic fraud monitoring to detect and protect your website from spam and abuse.<br/><br/>If your user cannot verify their session, please submit a Support ticket with the following identifiers: `link_session_id` or `request_id` | &nbsp; | &nbsp; |

# Cause
An error object and associated `item_id` used to identify a specific Item and error when a batch operation operating on multiple Items has encountered an error in one of the Items.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| item_id | Y | ItemId | &nbsp; | &nbsp; | &nbsp; |
| error | Y | Error | &nbsp; | &nbsp; | &nbsp; |

# StandaloneCurrencyCodeList
The following currency codes are supported by Plaid.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| iso_currency_code | Y | string | Plaid supports all ISO 4217 currency codes. | &nbsp; | &nbsp; |
| unofficial_currency_code | Y | UnofficialCurrencyCodeList | &nbsp; | &nbsp; | &nbsp; |

# UnofficialCurrencyCodeList
List of unofficial currency codes


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| ADA | Y | string | Cardano | &nbsp; | &nbsp; |
| BAT | Y | string | Basic Attention Token | &nbsp; | &nbsp; |
| BCH | Y | string | Bitcoin Cash | &nbsp; | &nbsp; |
| BNB | Y | string | Binance Coin | &nbsp; | &nbsp; |
| BTC | Y | string | Bitcoin | &nbsp; | &nbsp; |
| BTG | Y | string | Bitcoin Gold | &nbsp; | &nbsp; |
| BSV | &nbsp; | string | Bitcoin Satoshi Vision | &nbsp; | &nbsp; |
| CNH | Y | string | Chinese Yuan (offshore) | &nbsp; | &nbsp; |
| DASH | Y | string | Dash | &nbsp; | &nbsp; |
| DOGE | Y | string | Dogecoin | &nbsp; | &nbsp; |
| ETC | Y | string | Ethereum Classic | &nbsp; | &nbsp; |
| ETH | Y | string | Ethereum | &nbsp; | &nbsp; |
| GBX | Y | string | Pence sterling, i.e. British penny | &nbsp; | &nbsp; |
| LSK | Y | string | Lisk | &nbsp; | &nbsp; |
| NEO | Y | string | Neo | &nbsp; | &nbsp; |
| OMG | Y | string | OmiseGO | &nbsp; | &nbsp; |
| QTUM | Y | string | Qtum | &nbsp; | &nbsp; |
| USDT | Y | string | TehterUS | &nbsp; | &nbsp; |
| XLM | Y | string | Stellar Lumen | &nbsp; | &nbsp; |
| XMR | Y | string | Monero | &nbsp; | &nbsp; |
| XRP | Y | string | Ripple | &nbsp; | &nbsp; |
| ZEC | Y | string | Zcash | &nbsp; | &nbsp; |
| ZRX | Y | string | 0x | &nbsp; | &nbsp; |

# StandaloneAccountType
The schema below describes the various `types` and corresponding `subtypes` that Plaid recognizes and reports for financial institution accounts.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| depository | Y | DepositoryAccount | &nbsp; | &nbsp; | &nbsp; |
| credit | Y | CreditAccount | &nbsp; | &nbsp; | &nbsp; |
| loan | Y | LoanAccount | &nbsp; | &nbsp; | &nbsp; |
| investment | Y | InvestmentAccountSubtype | &nbsp; | &nbsp; | &nbsp; |
| other | Y | string | Other or unknown account type. Supported products for `other` accounts are: Balance, Transactions, Identity, and Assets. | &nbsp; | &nbsp; |

# DepositoryAccount
An account type holding cash, in which funds are deposited. Supported products for `depository` accounts are: Auth, Balance, Transactions, Identity, Payment Initiation, and Assets.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| checking | Y | string | Checking account | &nbsp; | &nbsp; |
| savings | Y | string | Savings account | &nbsp; | &nbsp; |
| hsa | Y | string | Health Savings Account (US only) that can only hold cash | &nbsp; | &nbsp; |
| cd | Y | string | Certificate of deposit account | &nbsp; | &nbsp; |
| money market | Y | string | Money market account | &nbsp; | &nbsp; |
| paypal | Y | string | PayPal depository account | &nbsp; | &nbsp; |
| prepaid | Y | string | Prepaid debit card | &nbsp; | &nbsp; |
| cash management | Y | string | A cash management account, typically a cash account at a brokerage | &nbsp; | &nbsp; |
| ebt | Y | string | An Electronic Benefit Transfer (EBT) account, used by certain public assistance programs to distribute funds (US only) | &nbsp; | &nbsp; |

# CreditAccount
A credit card type account. Supported products for `credit` accounts are: Balance, Transactions, Identity, and Liabilities.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| credit card | Y | string | Bank-issued credit card | &nbsp; | &nbsp; |
| paypal | Y | string | PayPal-issued credit card | &nbsp; | &nbsp; |

# LoanAccount
A loan type account. Supported products for `loan` accounts are: Balance, Liabilities, and Transactions.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| auto | Y | string | Auto loan | &nbsp; | &nbsp; |
| business | Y | string | Business loan | &nbsp; | &nbsp; |
| commercial | Y | string | Commercial loan | &nbsp; | &nbsp; |
| construction | Y | string | Construction loan | &nbsp; | &nbsp; |
| consumer | Y | string | Consumer loan | &nbsp; | &nbsp; |
| home equity | Y | string | Home Equity Line of Credit (HELOC) | &nbsp; | &nbsp; |
| loan | Y | string | General loan | &nbsp; | &nbsp; |
| mortgage | Y | string | Mortgage loan | &nbsp; | &nbsp; |
| overdraft | Y | string | Pre-approved overdraft account, usually tied to a checking account | &nbsp; | &nbsp; |
| line of credit | Y | string | Pre-approved line of credit | &nbsp; | &nbsp; |
| student | Y | string | Student loan | &nbsp; | &nbsp; |
| other | Y | string | Other loan type or unknown loan type | &nbsp; | &nbsp; |

# InvestmentAccountSubtype
An investment account. Supported products for `investment` accounts are: Balance and Investments. In API versions 2018-05-22 and earlier, this type is called `brokerage`.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| 529 | Y | string | Tax-advantaged college savings and prepaid tuition 529 plans (US)<br/> | &nbsp; | &nbsp; |
| 401a | Y | string | Employer-sponsored money-purchase 401(a) retirement plan (US) | &nbsp; | &nbsp; |
| 401k | Y | string | Standard 401(k) retirement account (US) | &nbsp; | &nbsp; |
| 403B | Y | string | 403(b) retirement savings account for non-profits and schools (US) | &nbsp; | &nbsp; |
| 457b | Y | string | Tax-advantaged deferred-compensation 457(b) retirement plan for governments and non-profits (US) | &nbsp; | &nbsp; |
| brokerage | Y | string | Standard brokerage account | &nbsp; | &nbsp; |
| cash isa | Y | string | Individual Savings Account (ISA) that pays interest tax-free (UK) | &nbsp; | &nbsp; |
| education savings account | Y | string | Tax-advantaged Coverdell Education Savings Account (ESA) (US) | &nbsp; | &nbsp; |
| fixed annuity | Y | string | Fixed annuity | &nbsp; | &nbsp; |
| gic | Y | string | Guaranteed Investment Certificate (Canada) | &nbsp; | &nbsp; |
| health reimbursement arrangement | Y | string | Tax-advantaged Health Reimbursement Arrangement (HRA) benefit plan (US) | &nbsp; | &nbsp; |
| hsa | Y | string | Non-cash tax-advantaged medical Health Savings Account (HSA) (US)<br/> | &nbsp; | &nbsp; |
| ira | Y | string | Traditional Invididual Retirement Account (IRA) (US) | &nbsp; | &nbsp; |
| isa | Y | string | Non-cash Individual Savings Account (ISA) (UK) | &nbsp; | &nbsp; |
| keogh | Y | string | Keogh self-employed retirement plan (US) | &nbsp; | &nbsp; |
| lif | Y | string | Life Income Fund (LIF) retirement account (Canada)<br/> | &nbsp; | &nbsp; |
| life insurance | Y | string | Life insurance account | &nbsp; | &nbsp; |
| lira | Y | string | Locked-in Retirement Account (LIRA) (Canada) | &nbsp; | &nbsp; |
| lrif | Y | string | Locked-in Retirement Income Fund (LRIF) (Canada) | &nbsp; | &nbsp; |
| lrsp | Y | string | Locked-in Retirement Savings Plan (Canada) | &nbsp; | &nbsp; |
| mutual fund | Y | string | Mutual fund account | &nbsp; | &nbsp; |
| non-taxable brokerage account | Y | string | A non-taxable brokerage account that is not covered by a more specific subtype | &nbsp; | &nbsp; |
| other | Y | string | An account whose type could not be determined | &nbsp; | &nbsp; |
| other annuity | Y | string | An annuity account not covered by other subtypes | &nbsp; | &nbsp; |
| other insurance | Y | string | An insurance account not covered by other subtypes | &nbsp; | &nbsp; |
| pension | Y | string | Standard pension account | &nbsp; | &nbsp; |
| prif | Y | string | Prescribed Registered Retirement Income Fund (Canada) | &nbsp; | &nbsp; |
| profit sharing plan | Y | string | Plan that gives employees share of company profits | &nbsp; | &nbsp; |
| qshr | Y | string | Qualifying share account | &nbsp; | &nbsp; |
| rdsp | Y | string | Registered Disability Savings Plan (RSDP) (Canada) | &nbsp; | &nbsp; |
| resp | Y | string | Registered Education Savings Plan (Canada) | &nbsp; | &nbsp; |
| retirement | Y | string | Retirement account not covered by other subtypes | &nbsp; | &nbsp; |
| rlif | Y | string | Restricted Life Income Fund (RLIF) (Canada) | &nbsp; | &nbsp; |
| roth | Y | string | Roth IRA (US) | &nbsp; | &nbsp; |
| roth 401k | Y | string | Employer-sponsored Roth 401(k) plan (US) | &nbsp; | &nbsp; |
| rrif | Y | string | Registered Retirement Income Fund (RRIF) (Canada) | &nbsp; | &nbsp; |
| rrsp | Y | string | Registered Retirement Savings Plan (Canadian, similar to US 401(k)) | &nbsp; | &nbsp; |
| sarsep | Y | string | Salary Reduction Simplified Employee Pension Plan (SARSEP), discontinued retirement plan (US) | &nbsp; | &nbsp; |
| sep ira | Y | string | Simplified Employee Pension IRA (SEP IRA), retirement plan for small businesses and self-employed (US) | &nbsp; | &nbsp; |
| simple ira | Y | string | Savings Incentive Match Plan for Employees IRA, retirement plan for small businesses (US) | &nbsp; | &nbsp; |
| sipp | Y | string | Self-Invested Personal Pension (SIPP) (UK) | &nbsp; | &nbsp; |
| stock plan | Y | string | Standard stock plan account | &nbsp; | &nbsp; |
| tfsa | Y | string | Tax-Free Savings Account (TFSA), a retirement plan similar to a Roth IRA (Canada) | &nbsp; | &nbsp; |
| trust | Y | string | Account representing funds or assets held by a trustee for the benefit of a beneficiary. Includes both revocable and irrevocable trusts. | &nbsp; | &nbsp; |
| ugma | Y | string | 'Uniform Gift to Minors Act' (brokerage account for minors, US) | &nbsp; | &nbsp; |
| utma | Y | string | 'Uniform Transfers to Minors Act' (brokerage account for minors, US)<br/> | &nbsp; | &nbsp; |
| variable annuity | Y | string | Tax-deferred capital accumulation annuity contract | &nbsp; | &nbsp; |

# AccountFiltersResponse
The `account_filters` specified in the original call to `/link/token/create`.



## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| depository | &nbsp; | DepositoryFilter | &nbsp; | &nbsp; | &nbsp; |
| credit | &nbsp; | CreditFilter | &nbsp; | &nbsp; | &nbsp; |

# InstitutionsSearchAccountFilter
&nbsp;

## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| loan | &nbsp; | array[] of AccountSubtype | &nbsp; | &nbsp; | &nbsp; |
| depository | &nbsp; | array[] of AccountSubtype | &nbsp; | &nbsp; | &nbsp; |
| credit | &nbsp; | array[] of AccountSubtype | &nbsp; | &nbsp; | &nbsp; |
| investment | &nbsp; | array[] of AccountSubtype | &nbsp; | &nbsp; | &nbsp; |

# AccountIdentity
&nbsp;

## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| owners | Y | array[] of Owner | Data returned by the financial institution about the account owner or owners. Only returned by Identity or Assets endpoints. Multiple owners on a single account will be represented in the same `owner` object, not in multiple owner objects within the array. In API versions 2018-05-22 and earlier, the `owners` object is not returned, and instead identity information is returned in the top level `identity` object. For more details, see [Plaid API versioning](https://plaid.com/docs/api/versioning/#version-2019-05-29) | &nbsp; | &nbsp; |

# DepositoryFilter
A filter to apply to `depository`-type accounts


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_subtypes | Y | AccountSubtypes | &nbsp; | &nbsp; | &nbsp; |

# CreditFilter
A filter to apply to `credit`-type accounts


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_subtypes | Y | AccountSubtypes | &nbsp; | &nbsp; | &nbsp; |

# HealthIncident
&nbsp;

## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| start_date | Y | date-time | The start date of the incident, in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format, e.g. `"2020-10-30T15:26:48Z"`. | &nbsp; | &nbsp; |
| end_date | &nbsp; | date-time | The end date of the incident, in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format, e.g. `"2020-10-30T15:26:48Z"`. | &nbsp; | &nbsp; |
| title | Y | string | The title of the incident | &nbsp; | &nbsp; |
| incident_updates | Y | array[] of IncidentUpdate | Updates on the health incident. | &nbsp; | &nbsp; |

# IncidentUpdate
&nbsp;

## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| description | &nbsp; | string | The content of the update. | &nbsp; | &nbsp; |
| status | &nbsp; | enum | The status of the incident. | <ul><li>INVESTIGATING</li><li>IDENTIFIED</li><li>SCHEDULED</li><li>RESOLVED</li><li>UNKNOWN</li></ul> | &nbsp; |
| updated_date | &nbsp; | date-time | The date when the update was published, in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format, e.g. `"2020-10-30T15:26:48Z"`. | &nbsp; | &nbsp; |

# Application
Metadata about the application


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| application_id | Y | ApplicationID | &nbsp; | &nbsp; | &nbsp; |
| name | Y | string | The name of the application | &nbsp; | &nbsp; |
| created_at | Y | date | The date this application was linked in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) (YYYY-MM-DD) format in UTC. | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | &nbsp; |
| logo_url | Y | string | A URL that links to the application logo image. | &nbsp; | &nbsp; |
| application_url | Y | string | The URL for the application's website | &nbsp; | &nbsp; |
| reason_for_access | Y | string | A string provided by the connected app stating why they use their respective enabled products. | &nbsp; | &nbsp; |

# ApplicationGetRequest
ApplicationGetResponse defines the schema for `/application/get`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | Y | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | Y | APISecret | &nbsp; | &nbsp; | &nbsp; |
| application_id | Y | ApplicationID | &nbsp; | &nbsp; | &nbsp; |

# ApplicationGetResponse
The request ID associated with this call.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |
| application | Y | Application | &nbsp; | &nbsp; | &nbsp; |

# ProductAccess
The product access being requested. Used to or disallow product access across all accounts. If unset, defaults to all products allowed.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| statements | &nbsp; | boolean | Allow access to statements. Only used by certain partners. If relevant to the partner and unset, defaults to `true`. | &nbsp; | &nbsp; |
| identity | &nbsp; | boolean | Allow access to the Identity product (name, email, phone, address). Only used by certain partners. If relevant to the partner and unset, defaults to `true`. | &nbsp; | &nbsp; |
| auth | &nbsp; | boolean | Allow access to account number details. Only used by certain partners. If relevant to the partner and unset, defaults to `true`. | &nbsp; | &nbsp; |
| transactions | &nbsp; | boolean | Allow access to transaction details. Only used by certain partners. If relevant to the partner and unset, defaults to `true`. | &nbsp; | &nbsp; |

# AccountAccess
Allow or disallow product access by account. Unlisted (e.g. missing) accounts will be considered `new_accounts`.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| unique_id | Y | string | The unique account identifier for this account. This value must match that returned by the data access API for this account. | &nbsp; | &nbsp; |
| authorized | &nbsp; | boolean | Allow the application to see this account (and associated details, including balance) in the list of accounts  If unset, defaults to `true`. | &nbsp; | &nbsp; |

# AccountProductAccess
Allow the application to access specific products on this account


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| account_data | &nbsp; | boolean | Allow the application to access account data. Only used by certain partners. If relevant to the partner and unset, defaults to `true`. | &nbsp; | &nbsp; |
| statements | &nbsp; | boolean | Allow the application to access bank statements. Only used by certain partners. If relevant to the partner and unset, defaults to `true`. | &nbsp; | &nbsp; |
| tax_documents | &nbsp; | boolean | Allow the application to access tax documents. Only used by certain partners. If relevant to the partner and unset, defaults to `true`. | &nbsp; | &nbsp; |

# Scopes
The scopes object


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| product_access | &nbsp; | ProductAccess | &nbsp; | &nbsp; | &nbsp; |
| accounts | &nbsp; | array[] of AccountAccess | &nbsp; | &nbsp; | &nbsp; |
| new_accounts | &nbsp; | boolean | Allow access to newly opened accounts as they are opened. If unset, defaults to `true`. | &nbsp; | &nbsp; |

# RequestedScopes
Scope of required and optional account features or content from a ConnectedApplication.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| required_product_access | Y | ProductAccess | &nbsp; | &nbsp; | &nbsp; |
| optional_product_access | Y | ProductAccess | &nbsp; | &nbsp; | &nbsp; |
| account_filters | &nbsp; | AccountFilter | &nbsp; | &nbsp; | &nbsp; |
| account_selection_cardinality | Y | AccountSelectionCardinality | &nbsp; | &nbsp; | &nbsp; |

# ItemApplicationScopesUpdateRequest
ItemApplicationScopesUpdateRequest defines the request schema for `/item/application/scopes/update`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| application_id | Y | ApplicationID | &nbsp; | &nbsp; | &nbsp; |
| scopes | Y | Scopes | &nbsp; | &nbsp; | &nbsp; |
| state | &nbsp; | ScopesState | &nbsp; | &nbsp; | &nbsp; |
| context | Y | ScopesContext | &nbsp; | &nbsp; | &nbsp; |

# ItemApplicationScopesUpdateResponse
ItemApplicationScopesUpdateResponse defines the response schema for `/item/application/scopes/update`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# ItemApplicationListRequest
Request to list connected applications for a user.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| access_token | &nbsp; | AccessTokenNullable | &nbsp; | &nbsp; | &nbsp; |

# ItemApplicationListResponse
Describes the connected application for a particular end user.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| request_id | &nbsp; | RequestID | &nbsp; | &nbsp; | &nbsp; |
| applications | Y | array[] of ConnectedApplication | A list of connected applications. | &nbsp; | &nbsp; |

# ConnectedApplication
Describes the connected application for a particular end user.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| application_id | Y | ApplicationID | &nbsp; | &nbsp; | &nbsp; |
| name | Y | string | The name of the application | &nbsp; | &nbsp; |
| logo_url | Y | string | A URL that links to the application logo image. | &nbsp; | &nbsp; |
| application_url | Y | string | The URL for the application's website | &nbsp; | &nbsp; |
| reason_for_access | Y | string | A string provided by the connected app stating why they use their respective enabled products. | &nbsp; | &nbsp; |
| created_at | Y | date | The date this application was linked in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) (YYYY-MM-DD) format in UTC. | &nbsp;<ul><li>pattern : yyyy-MM-dd</li></ul> | 2020-01-01 |
| requested_scopes | &nbsp; | RequestedScopes | &nbsp; | &nbsp; | &nbsp; |

# AccountFilter
Enumerates the account subtypes that the application wishes for the user to be able to select from. For more details refer to Plaid documentation on account filters.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| depository | &nbsp; | AccountFilterSubtypes | &nbsp; | &nbsp; | &nbsp; |
| credit | &nbsp; | AccountFilterSubtypes | &nbsp; | &nbsp; | &nbsp; |
| loan | &nbsp; | AccountFilterSubtypes | &nbsp; | &nbsp; | &nbsp; |
| investment | &nbsp; | AccountFilterSubtypes | &nbsp; | &nbsp; | &nbsp; |

# SignalEvaluateRequest
SignalEvaluateRequest defines the request schema for `/signal/evaluate`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| access_token | Y | AccessToken | &nbsp; | &nbsp; | &nbsp; |
| account_id | Y | string | The `account_id` of the account whose verification status is to be modified | &nbsp; | &nbsp; |
| client_transaction_id | Y | string | The unique ID that you would like to use to refer to this transaction. For your convenience mapping your internal data, you could use your internal ID/identifier for this transaction. The max length for this field is 36 characters. | <ul><li>minLength : 1</li><li>maxLength : 36</li></ul> | &nbsp; |
| amount | Y | number | The transaction amount, in USD (e.g. `102.05`) | &nbsp; | &nbsp; |
| user_present | &nbsp; | boolean | `true` if the end user is present while initiating the ACH transfer and the endpoint is being called; `false` otherwise (for example, when the ACH transfer is scheduled and the end user is not present, or you call this endpoint after the ACH transfer but before submitting the Nacha file for ACH processing). | &nbsp; | &nbsp; |
| client_user_id | &nbsp; | string | A unique ID that identifies the end user in your system. This ID is used to correlate requests by a user with multiple Items. The max length for this field is 36 characters. | <ul><li>maxLength : 36</li></ul> | &nbsp; |
| user | &nbsp; | SignalUser | &nbsp; | &nbsp; | &nbsp; |
| device | &nbsp; | SignalDevice | &nbsp; | &nbsp; | &nbsp; |

# SignalUser
Details about the end user initiating the transaction (i.e., the account holder).


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| name | &nbsp; | SignalPersonName | &nbsp; | &nbsp; | &nbsp; |
| phone_number | &nbsp; | string | The user's phone number, in E.164 format: +{countrycode}{number}. For example: "+14151234567" | &nbsp; | &nbsp; |
| email_address | &nbsp; | string | The user's email address. | &nbsp; | &nbsp; |
| address | &nbsp; | SignalAddressData | &nbsp; | &nbsp; | &nbsp; |

# SignalPersonName
The user's legal name


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| prefix | &nbsp; | string | The user's name prefix (e.g. "Mr.") | &nbsp; | &nbsp; |
| given_name | &nbsp; | string | The user's given name. If the user has a one-word name, it should be provided in this field. | &nbsp; | &nbsp; |
| middle_name | &nbsp; | string | The user's middle name | &nbsp; | &nbsp; |
| family_name | &nbsp; | string | The user's family name / surname | &nbsp; | &nbsp; |
| suffix | &nbsp; | string | The user's name suffix (e.g. "II") | &nbsp; | &nbsp; |

# SignalAddressData
Data about the components comprising an address.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| city | &nbsp; | string | The full city name | &nbsp; | &nbsp; |
| region | &nbsp; | string | The region or state<br/>Example: `"NC"` | &nbsp; | &nbsp; |
| street | &nbsp; | string | The full street address<br/>Example: `"564 Main Street, APT 15"` | &nbsp; | &nbsp; |
| postal_code | &nbsp; | string | The postal code | &nbsp; | &nbsp; |
| country | &nbsp; | string | The ISO 3166-1 alpha-2 country code | &nbsp; | &nbsp; |

# SignalDevice
Details about the end user's device


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| ip_address | &nbsp; | string | The IP address of the device that initiated the transaction | &nbsp; | &nbsp; |
| user_agent | &nbsp; | string | The user agent of the device that initiated the transaction (e.g. "Mozilla/5.0") | &nbsp; | &nbsp; |

# SignalEvaluateResponse
SignalEvaluateResponse defines the response schema for `/signal/income/evaluate`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |
| scores | Y | SignalScores | &nbsp; | &nbsp; | &nbsp; |
| core_attributes | &nbsp; | SignalEvaluateCoreAttributes | &nbsp; | &nbsp; | &nbsp; |

# SignalScores
Risk scoring details broken down by risk category.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| customer_initiated_return_risk | &nbsp; | CustomerInitiatedReturnRisk | &nbsp; | &nbsp; | &nbsp; |
| bank_initiated_return_risk | &nbsp; | BankInitiatedReturnRisk | &nbsp; | &nbsp; | &nbsp; |

# CustomerInitiatedReturnRisk
The object contains a risk score and a risk tier that evaluate the transaction return risk of an unauthorized debit. Common return codes in this category include: “R05”, "R07", "R10", "R11", "R29". These returns typically have a return time frame of up to 60 calendar days. During this period, the customer of financial institutions can dispute a transaction as unauthorized.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| score | Y | SignalScore | &nbsp; | &nbsp; | &nbsp; |
| risk_tier | Y | CustomerInitiatedRiskTier | &nbsp; | &nbsp; | &nbsp; |

# BankInitiatedReturnRisk
The object contains a risk score and a risk tier that evaluate the transaction return risk because an account is overdrawn or because an ineligible account is used. Common return codes in this category include: "R01", "R02", "R03", "R04", "R06", “R08”,  "R09", "R13", "R16", "R17", "R20", "R23". These returns have a turnaround time of 2 banking days.


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| score | Y | SignalScore | &nbsp; | &nbsp; | &nbsp; |
| risk_tier | Y | BankInitiatedRiskTier | &nbsp; | &nbsp; | &nbsp; |

# SignalEvaluateCoreAttributes
The core attributes object contains additional data that can be used to assess the ACH return risk. Examples of data include:

`days_since_first_plaid_connection`: The number of days since the first time the Item was connected to an application via Plaid
`plaid_connections_count_7d`: The number of times the Item has been connected to applications via Plaid over the past 7 days
`plaid_connections_count_30d`: The number of times the Item has been connected to applications via Plaid over the past 30 days
`total_plaid_connections_count`: The number of times the Item has been connected to applications via Plaid
`is_savings_or_money_market_account`: Indicates whether the ACH transaction funding account is a savings/money market account

For the full list and detailed documentation of core attributes available, or to request that core attributes not be returned, contact Sales or your Plaid account manager


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| unauthorized_transactions_count_7d | &nbsp; | integer | We parse and analyze historical transaction metadata to identify the number of possible past returns due to unauthorized transactions over the past 7 days from the account that will be debited. | &nbsp; | &nbsp; |
| unauthorized_transactions_count_30d | &nbsp; | integer | We parse and analyze historical transaction metadata to identify the number of possible past returns due to unauthorized transactions over the past 30 days from the account that will be debited. | &nbsp; | &nbsp; |
| unauthorized_transactions_count_60d | &nbsp; | integer | We parse and analyze historical transaction metadata to identify the number of possible past returns due to unauthorized transactions over the past 60 days from the account that will be debited. | &nbsp; | &nbsp; |
| unauthorized_transactions_count_90d | &nbsp; | integer | We parse and analyze historical transaction metadata to identify the number of possible past returns due to unauthorized transactions over the past 90 days from the account that will be debited. | &nbsp; | &nbsp; |
| nsf_overdraft_transactions_count_7d | &nbsp; | integer | We parse and analyze historical transaction metadata to identify the number of possible past returns due to non-sufficient funds/overdrafts over the past 7 days from the account that will be debited. | &nbsp; | &nbsp; |
| nsf_overdraft_transactions_count_30d | &nbsp; | integer | We parse and analyze historical transaction metadata to identify the number of possible past returns due to non-sufficient funds/overdrafts over the past 30 days from the account that will be debited. | &nbsp; | &nbsp; |
| nsf_overdraft_transactions_count_60d | &nbsp; | integer | We parse and analyze historical transaction metadata to identify the number of possible past returns due to non-sufficient funds/overdrafts over the past 60 days from the account that will be debited. | &nbsp; | &nbsp; |
| nsf_overdraft_transactions_count_90d | &nbsp; | integer | We parse and analyze historical transaction metadata to identify the number of possible past returns due to non-sufficient funds/overdrafts over the past 90 days from the account that will be debited. | &nbsp; | &nbsp; |
| days_since_first_plaid_connection | &nbsp; | integer | The number of days since the first time the Item was connected to an application via Plaid | &nbsp; | &nbsp; |
| plaid_connections_count_7d | &nbsp; | integer | The number of times the Item has been connected to applications via Plaid over the past 7 days | &nbsp; | &nbsp; |
| plaid_connections_count_30d | &nbsp; | integer | The number of times the Item has been connected to applications via Plaid over the past 30 days | &nbsp; | &nbsp; |
| total_plaid_connections_count | &nbsp; | integer | The total number of times the Item has been connected to applications via Plaid | &nbsp; | &nbsp; |
| is_savings_or_money_market_account | &nbsp; | boolean | Indicates if the ACH transaction funding account is a savings/money market account | &nbsp; | &nbsp; |
| total_credit_transactions_amount_10d | &nbsp; | number | The total credit (inflow) transaction amount over the past 10 days from the account that will be debited | &nbsp; | &nbsp; |
| total_debit_transactions_amount_10d | &nbsp; | number | The total debit (outflow) transaction amount over the past 10 days from the account that will be debited | &nbsp; | &nbsp; |
| p50_credit_transactions_amount_28d | &nbsp; | number | The 50th percentile of all credit (inflow) transaction amounts over the past 28 days from the account that will be debited | &nbsp; | &nbsp; |
| p50_debit_transactions_amount_28d | &nbsp; | number | The 50th percentile of all debit (outflow) transaction amounts over the past 28 days from the account that will be debited | &nbsp; | &nbsp; |
| p95_credit_transactions_amount_28d | &nbsp; | number | The 95th percentile of all credit (inflow) transaction amounts over the past 28 days from the account that will be debited | &nbsp; | &nbsp; |
| p95_debit_transactions_amount_28d | &nbsp; | number | The 95th percentile of all debit (outflow) transaction amounts over the past 28 days from the account that will be debited | &nbsp; | &nbsp; |
| days_with_negative_balance_count_90d | &nbsp; | integer | The number of days within the past 90 days when the account that will be debited had a negative end-of-day available balance | &nbsp; | &nbsp; |
| p90_eod_balance_30d | &nbsp; | number | The 90th percentile of the end-of-day available balance over the past 30 days of the account that will be debited | &nbsp; | &nbsp; |
| p90_eod_balance_60d | &nbsp; | number | The 90th percentile of the end-of-day available balance over the past 60 days of the account that will be debited | &nbsp; | &nbsp; |
| p90_eod_balance_90d | &nbsp; | number | The 90th percentile of the end-of-day available balance over the past 90 days of the account that will be debited | &nbsp; | &nbsp; |
| p10_eod_balance_30d | &nbsp; | number | The 10th percentile of the end-of-day available balance over the past 30 days of the account that will be debited | &nbsp; | &nbsp; |
| p10_eod_balance_60d | &nbsp; | number | The 10th percentile of the end-of-day available balance over the past 60 days of the account that will be debited | &nbsp; | &nbsp; |
| p10_eod_balance_90d | &nbsp; | number | The 10th percentile of the end-of-day available balance over the past 90 days of the account that will be debited | &nbsp; | &nbsp; |
| available_balance | &nbsp; | number | Available balance, as of the `balance_last_updated` time. The available balance is the current balance less any outstanding holds or debits that have not yet posted to the account. | &nbsp; | &nbsp; |
| current_balance | &nbsp; | number | Current balance, as of the `balance_last_updated` time. The current balance is the total amount of funds in the account. | &nbsp; | &nbsp; |
| balance_last_updated | &nbsp; | date-time | Timestamp in [ISO 8601](https://wikipedia.org/wiki/ISO_8601) format (YYYY-MM-DDTHH:mm:ssZ) indicating the last time that the balance for the given account has been updated. | &nbsp; | &nbsp; |
| phone_change_count_28d | &nbsp; | integer | The number of times the account's phone numbers on file have changed over the past 28 days | &nbsp; | &nbsp; |
| phone_change_count_90d | &nbsp; | integer | The number of times the account's phone numbers on file have changed over the past 90 days | &nbsp; | &nbsp; |
| email_change_count_28d | &nbsp; | integer | The number of times the account's email addresses on file have changed over the past 28 days | &nbsp; | &nbsp; |
| email_change_count_90d | &nbsp; | integer | The number of times the account's email addresses on file have changed over the past 90 days | &nbsp; | &nbsp; |
| address_change_count_28d | &nbsp; | integer | The number of times the account's addresses on file have changed over the past 28 days | &nbsp; | &nbsp; |
| address_change_count_90d | &nbsp; | integer | The number of times the account's addresses on file have changed over the past 90 days | &nbsp; | &nbsp; |

# SignalDecisionReportRequest
SignalDecisionReportRequest defines the request schema for `/signal/decision/report`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| client_transaction_id | Y | string | Must be the same as the `client_transaction_id` supplied when calling `/signal/evaluate` | <ul><li>minLength : 1</li><li>maxLength : 36</li></ul> | &nbsp; |
| initiated | Y | boolean | `true` if the ACH transaction was initiated, `false` otherwise. | &nbsp; | &nbsp; |
| days_funds_on_hold | &nbsp; | integer | The actual number of days (hold time) since the ACH debit transaction that you wait before making funds available to your customers. The holding time could affect the ACH return rate. For example, use 0 if you make funds available to your customers instantly or the same day following the debit transaction, or 1 if you make funds available the next day following the debit initialization. | <ul><li>minimum : 0</li></ul> | &nbsp; |

# SignalDecisionReportResponse
SignalDecisionReportResponse defines the response schema for `/signal/decision/report`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |

# SignalReturnReportRequest
SignalReturnReportRequest defines the request schema for `/signal/return/report`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| client_id | &nbsp; | APIClientID | &nbsp; | &nbsp; | &nbsp; |
| secret | &nbsp; | APISecret | &nbsp; | &nbsp; | &nbsp; |
| client_transaction_id | Y | string | Must be the same as the `client_transaction_id` supplied when calling `/signal/evaluate` | <ul><li>minLength : 1</li><li>maxLength : 36</li></ul> | &nbsp; |
| return_code | Y | string | Must be a valid ACH return code (e.g. "R01") | &nbsp; | &nbsp; |

# SignalReturnReportResponse
SignalReturnReportResponse defines the response schema for `/signal/return/report`


## Properties
| property | required | type | description | details | example |
| :--- | :---: | :---: | :--- | :--- | :--- |
| request_id | Y | RequestID | &nbsp; | &nbsp; | &nbsp; |
