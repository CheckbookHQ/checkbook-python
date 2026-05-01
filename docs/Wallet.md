# Wallet 
Create and manage wallets to manage prefunded flows from within a user's Checkbook account. External wallets are funded via ACH, wire, RTP, or FedNow; internal wallets are funded via ACH debit or wallet-to-wallet transfer. Both types support all payout methods, including instant rails (RTP, FedNow, PayPal, Venmo, wire, push-to-card) and standard rails (ACH, checks).


Method | HTTP request | Description
------------- | ------------- | -------------
[**add_wallet**](Wallet.md#add_wallet) | **POST** /v3/account/wallet | Create wallet
[**delete_wallet**](Wallet.md#delete_wallet) | **DELETE** /v3/account/wallet/{wallet_id} | Delete wallet
[**get_wallet**](Wallet.md#get_wallet) | **GET** /v3/account/wallet | Get wallets
[**update_wallet**](Wallet.md#update_wallet) | **PUT** /v3/account/wallet/{wallet_id} | Update wallet


# **add_wallet**
> CreateWalletResponse add_wallet(create_wallet_request)

Add a new wallet account for user 
> [!NOTE]
> **Tip**  
> Please securely save the unique routing and account numbers for EXTERNAL wallets after generation, as they are only revealed once.

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_wallet_request import CreateWalletRequest
from checkbook.models.create_wallet_response import CreateWalletResponse
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
    api_instance = checkbook.Wallet(api_client)
    create_wallet_request = {
        "name": "Wallet #1",
        "type": "EXTERNAL",
    }  # CreateWalletRequest |

    try:
        # Create wallet
        api_response = api_instance.add_wallet(create_wallet_request)
        print("The response of Wallet->add_wallet:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Wallet->add_wallet: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_wallet_request** | [**CreateWalletRequest**](CreateWalletRequest.md)|  | 

### Return type

[**CreateWalletResponse**](CreateWalletResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | CreateWalletResponse |  -  |
**0** | Error |  -  |


# **delete_wallet**
> object delete_wallet(wallet_id)

Delete a wallet account

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
    api_instance = checkbook.Wallet(api_client)
    wallet_id = "wallet_id_example"  # str | The ID of the wallet to be deleted

    try:
        # Delete wallet
        api_response = api_instance.delete_wallet(wallet_id)
        print("The response of Wallet->delete_wallet:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Wallet->delete_wallet: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **wallet_id** | **str**| The ID of the wallet to be deleted | 

### Return type

**object**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | DeleteWalletResponse |  -  |
**0** | Error |  -  |


# **get_wallet**
> InlineResponse200 get_wallet()

Get wallet accounts for user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.inline_response200 import InlineResponse200
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
    api_instance = checkbook.Wallet(api_client)

    try:
        # Get wallets
        api_response = api_instance.get_wallet()
        print("The response of Wallet->get_wallet:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Wallet->get_wallet: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

[**InlineResponse200**](InlineResponse200.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetWalletResponse |  -  |
**0** | Error |  -  |


# **update_wallet**
> object update_wallet(wallet_id, update_wallet_request)

Update wallet

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_wallet_request import UpdateWalletRequest
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
    api_instance = checkbook.Wallet(api_client)
    wallet_id = "wallet_id_example"  # str | The ID of the wallet to be updated
    update_wallet_request = {"name": "Wallet #1"}  # UpdateWalletRequest |

    try:
        # Update wallet
        api_response = api_instance.update_wallet(wallet_id, update_wallet_request)
        print("The response of Wallet->update_wallet:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Wallet->update_wallet: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **wallet_id** | **str**| The ID of the wallet to be updated | 
 **update_wallet_request** | [**UpdateWalletRequest**](UpdateWalletRequest.md)|  | 

### Return type

**object**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | UpdateWalletResponse |  -  |
**0** | Error |  -  |


