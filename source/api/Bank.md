# Bank 
Link and manage bank accounts used as a funding source or destination for ACH, RTP, and FedNow payments. Accounts can be linked to users instantly via Plaid or manually with a routing and account number; manually linked accounts are verified with micro-deposits.


Method | HTTP request | Description
------------- | ------------- | -------------
[**delete_bank**](Bank.md#delete_bank) | **DELETE** /v3/account/bank/{bank_id} | Remove bank account
[**get_bank_institutions**](Bank.md#get_bank_institutions) | **GET** /v3/account/bank/institutions | Get institutions
[**get_banks**](Bank.md#get_banks) | **GET** /v3/account/bank | Get bank accounts
[**post_bank**](Bank.md#post_bank) | **POST** /v3/account/bank | Add bank account
[**post_bank_iav**](Bank.md#post_bank_iav) | **POST** /v3/account/bank/iav | Add bank account with IAV
[**post_bank_plaid**](Bank.md#post_bank_plaid) | **POST** /v3/account/bank/iav/plaid | Retrieve bank account with Plaid
[**post_bank_release**](Bank.md#post_bank_release) | **POST** /v3/account/bank/release | Release micro-deposits
[**post_bank_verify**](Bank.md#post_bank_verify) | **POST** /v3/account/bank/verify | Verify micro-deposits
[**put_bank**](Bank.md#put_bank) | **PUT** /v3/account/bank/{bank_id} | Update bank account


# **delete_bank**
> delete_bank(bank_id)

Remove the specified bank account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://demo.checkbook.io
# See configuration.py for a list of all supported configuration parameters.
configuration = checkbook.Configuration(
    host="https://demo.checkbook.io", api_key={"token": "{public_key}:{private_key}"}
)


# Enter a context with an instance of the API client
with checkbook.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = checkbook.Bank(api_client)
    bank_id = "bank_id_example"  # str |

    try:
        # Remove bank account
        api_instance.delete_bank(bank_id)
    except Exception as e:
        print("Exception when calling Bank->delete_bank: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **bank_id** | **str**|  | 

### Return type

void (empty response body)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | No response body. |  -  |
**0** | Error |  -  |


# **get_bank_institutions**
> GetInstitutionsResponse get_bank_institutions()

Return a list of our supported institutions for instant account verification

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_institutions_response import GetInstitutionsResponse
from checkbook.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://demo.checkbook.io
# See configuration.py for a list of all supported configuration parameters.
configuration = checkbook.Configuration(
    host="https://demo.checkbook.io", api_key={"token": "{public_key}:{private_key}"}
)


# Enter a context with an instance of the API client
with checkbook.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = checkbook.Bank(api_client)

    try:
        # Get institutions
        api_response = api_instance.get_bank_institutions()
        print("The response of Bank->get_bank_institutions:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Bank->get_bank_institutions: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**GetInstitutionsResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetInstitutionsResponse |  -  |
**0** | Error |  -  |


# **get_banks**
> GetBanksResponse get_banks()

Get the bank accounts for a user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_banks_response import GetBanksResponse
from checkbook.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://demo.checkbook.io
# See configuration.py for a list of all supported configuration parameters.
configuration = checkbook.Configuration(
    host="https://demo.checkbook.io", api_key={"token": "{public_key}:{private_key}"}
)


# Enter a context with an instance of the API client
with checkbook.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = checkbook.Bank(api_client)

    try:
        # Get bank accounts
        api_response = api_instance.get_banks()
        print("The response of Bank->get_banks:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Bank->get_banks: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**GetBanksResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetBanksResponse |  -  |
**0** | Error |  -  |


# **post_bank**
> CreateBankResponse post_bank(create_bank_request)

Add a new bank account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_bank_request import CreateBankRequest
from checkbook.models.create_bank_response import CreateBankResponse
from checkbook.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://demo.checkbook.io
# See configuration.py for a list of all supported configuration parameters.
configuration = checkbook.Configuration(
    host="https://demo.checkbook.io", api_key={"token": "{public_key}:{private_key}"}
)


# Enter a context with an instance of the API client
with checkbook.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = checkbook.Bank(api_client)
    create_bank_request = {
        "account": "428100000",
        "name": "Checking account",
        "routing": "021000021",
        "type": "CHECKING",
    }  # CreateBankRequest |

    try:
        # Add bank account
        api_response = api_instance.post_bank(create_bank_request)
        print("The response of Bank->post_bank:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Bank->post_bank: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_bank_request** | **CreateBankRequest**|  | 

### Return type

**CreateBankResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | CreateBankResponse |  -  |
**0** | Error |  -  |


# **post_bank_iav**
> IAVLoginResponse post_bank_iav(post_bank_iav_request)

Add a new bank account with instant account verification

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.iav_login_response import IAVLoginResponse
from checkbook.models.post_bank_iav_request import PostBankIavRequest
from checkbook.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://demo.checkbook.io
# See configuration.py for a list of all supported configuration parameters.
configuration = checkbook.Configuration(
    host="https://demo.checkbook.io", api_key={"token": "{public_key}:{private_key}"}
)


# Enter a context with an instance of the API client
with checkbook.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = checkbook.Bank(api_client)
    post_bank_iav_request = {"institution_id": "string"}  # PostBankIavRequest |

    try:
        # Add bank account with IAV
        api_response = api_instance.post_bank_iav(post_bank_iav_request)
        print("The response of Bank->post_bank_iav:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Bank->post_bank_iav: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **post_bank_iav_request** | **PostBankIavRequest**|  | 

### Return type

**IAVLoginResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | IAVLoginResponse |  -  |
**0** | Error |  -  |


# **post_bank_plaid**
> IAVPlaidResponse post_bank_plaid(iav_plaid_request)

Retrieve the bank account(s) associated with the Plaid token.  
> [!NOTE]
> **Common Errors**
>
> - **`User login is required`** or **`Token Expired`**: The specified Plaid processor token has expired and a new token is required.

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.iav_plaid_request import IAVPlaidRequest
from checkbook.models.iav_plaid_response import IAVPlaidResponse
from checkbook.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://demo.checkbook.io
# See configuration.py for a list of all supported configuration parameters.
configuration = checkbook.Configuration(
    host="https://demo.checkbook.io", api_key={"token": "{public_key}:{private_key}"}
)


# Enter a context with an instance of the API client
with checkbook.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = checkbook.Bank(api_client)
    iav_plaid_request = {"processor_token": "string"}  # IAVPlaidRequest |

    try:
        # Retrieve bank account with Plaid
        api_response = api_instance.post_bank_plaid(iav_plaid_request)
        print("The response of Bank->post_bank_plaid:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Bank->post_bank_plaid: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **iav_plaid_request** | **IAVPlaidRequest**|  | 

### Return type

**IAVPlaidResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | IAVPlaidResponse |  -  |
**0** | Error |  -  |


# **post_bank_release**
> post_bank_release(bank_release_request)

Release the micro-deposits for a bank account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.bank_release_request import BankReleaseRequest
from checkbook.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://demo.checkbook.io
# See configuration.py for a list of all supported configuration parameters.
configuration = checkbook.Configuration(
    host="https://demo.checkbook.io", api_key={"token": "{public_key}:{private_key}"}
)


# Enter a context with an instance of the API client
with checkbook.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = checkbook.Bank(api_client)
    bank_release_request = {"account": "string"}  # BankReleaseRequest |

    try:
        # Release micro-deposits
        api_instance.post_bank_release(bank_release_request)
    except Exception as e:
        print("Exception when calling Bank->post_bank_release: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **bank_release_request** | **BankReleaseRequest**|  | 

### Return type

void (empty response body)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | No response body. |  -  |
**0** | Error |  -  |


# **post_bank_verify**
> post_bank_verify(bank_verify_request)

Verify the micro-deposits for a bank account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.bank_verify_request import BankVerifyRequest
from checkbook.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://demo.checkbook.io
# See configuration.py for a list of all supported configuration parameters.
configuration = checkbook.Configuration(
    host="https://demo.checkbook.io", api_key={"token": "{public_key}:{private_key}"}
)


# Enter a context with an instance of the API client
with checkbook.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = checkbook.Bank(api_client)
    bank_verify_request = {
        "account": "efdbaaaa17b244abba084e6c2ccfc990",
        "amount_1": 0.03,
        "amount_2": 0.05,
    }  # BankVerifyRequest |

    try:
        # Verify micro-deposits
        api_instance.post_bank_verify(bank_verify_request)
    except Exception as e:
        print("Exception when calling Bank->post_bank_verify: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **bank_verify_request** | **BankVerifyRequest**|  | 

### Return type

void (empty response body)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | No response body. |  -  |
**0** | Error |  -  |


# **put_bank**
> put_bank(bank_id, update_bank_request)

Update an existing bank account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_bank_request import UpdateBankRequest
from checkbook.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://demo.checkbook.io
# See configuration.py for a list of all supported configuration parameters.
configuration = checkbook.Configuration(
    host="https://demo.checkbook.io", api_key={"token": "{public_key}:{private_key}"}
)


# Enter a context with an instance of the API client
with checkbook.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = checkbook.Bank(api_client)
    bank_id = "bank_id_example"  # str |
    update_bank_request = {
        "billing": true,
        "default": true,
        "name": "Checking account",
    }  # UpdateBankRequest |

    try:
        # Update bank account
        api_instance.put_bank(bank_id, update_bank_request)
    except Exception as e:
        print("Exception when calling Bank->put_bank: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **bank_id** | **str**|  | 
 **update_bank_request** | **UpdateBankRequest**|  | 

### Return type

void (empty response body)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | No response body. |  -  |
**0** | Error |  -  |


