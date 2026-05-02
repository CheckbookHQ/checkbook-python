# Vcc 
Issue and manage virtual cards — digital, temporary card numbers used for controlled online, in-person, or mobile-wallet spending. Each card provides access to its full transaction history.


Method | HTTP request | Description
------------- | ------------- | -------------
[**delete_vcc**](Vcc.md#delete_vcc) | **DELETE** /v3/account/vcc/{vcc_id} | Remove virtual card
[**get_vcc_transaction**](Vcc.md#get_vcc_transaction) | **GET** /v3/account/vcc/{vcc_id}/transaction | Get virtual card transactions
[**get_vcc_transaction_by_id**](Vcc.md#get_vcc_transaction_by_id) | **GET** /v3/account/vcc/{vcc_id}/transaction/{transaction_id} | Get virtual card transaction by ID
[**get_vccs**](Vcc.md#get_vccs) | **GET** /v3/account/vcc | Get virtual cards
[**post_vcc**](Vcc.md#post_vcc) | **POST** /v3/account/vcc | Create virtual card
[**put_vcc**](Vcc.md#put_vcc) | **PUT** /v3/account/vcc/{vcc_id} | Update virtual card


## **delete_vcc**
> delete_vcc(vcc_id)

Remove the specified vcc

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
    api_instance = checkbook.Vcc(api_client)
    vcc_id = "vcc_id_example"  # str |

    try:
        # Remove virtual card
        api_instance.delete_vcc(vcc_id)
    except Exception as e:
        print("Exception when calling Vcc->delete_vcc: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **vcc_id** | **str**|  | 

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


## **get_vcc_transaction**
> VccTransactionsResponse get_vcc_transaction(vcc_id, beta=beta, end_date=end_date, page=page, per_page=per_page, start_date=start_date)

Get the transactions for the specified VCC

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.vcc_transactions_response import VccTransactionsResponse
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
    api_instance = checkbook.Vcc(api_client)
    vcc_id = "vcc_id_example"  # str |
    beta = False  # bool |  (optional) (default to False)
    end_date = "2013-10-20"  # date | End date (optional)
    page = 1  # int | Page number (optional) (default to 1)
    per_page = 50  # int | Items per page (optional) (default to 50)
    start_date = "2013-10-20"  # date | Start date (optional)

    try:
        # Get virtual card transactions
        api_response = api_instance.get_vcc_transaction(
            vcc_id,
            beta=beta,
            end_date=end_date,
            page=page,
            per_page=per_page,
            start_date=start_date,
        )
        print("The response of Vcc->get_vcc_transaction:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Vcc->get_vcc_transaction: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **vcc_id** | **str**|  | 
 **beta** | **bool**|  | [optional] [default to False]
 **end_date** | **date**| End date | [optional] 
 **page** | **int**| Page number | [optional] [default to 1]
 **per_page** | **int**| Items per page | [optional] [default to 50]
 **start_date** | **date**| Start date | [optional] 

### Return type

**VccTransactionsResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | VccTransactionsResponse |  -  |
**0** | Error |  -  |


## **get_vcc_transaction_by_id**
> VccTransaction get_vcc_transaction_by_id(vcc_id, transaction_id)

Get the requested transaction for the specified VCC

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.vcc_transaction import VccTransaction
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
    api_instance = checkbook.Vcc(api_client)
    vcc_id = "vcc_id_example"  # str |
    transaction_id = "transaction_id_example"  # str |

    try:
        # Get virtual card transaction by ID
        api_response = api_instance.get_vcc_transaction_by_id(vcc_id, transaction_id)
        print("The response of Vcc->get_vcc_transaction_by_id:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Vcc->get_vcc_transaction_by_id: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **vcc_id** | **str**|  | 
 **transaction_id** | **str**|  | 

### Return type

**VccTransaction**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | VccTransaction |  -  |
**0** | Error |  -  |


## **get_vccs**
> VccQueryResponse get_vccs()

Return the virtual cards

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.vcc_query_response import VccQueryResponse
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
    api_instance = checkbook.Vcc(api_client)

    try:
        # Get virtual cards
        api_response = api_instance.get_vccs()
        print("The response of Vcc->get_vccs:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Vcc->get_vccs: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**VccQueryResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | VccQueryResponse |  -  |
**0** | Error |  -  |


## **post_vcc**
> CreateVccResponse post_vcc(create_vcc_request)

Add a new vcc

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_vcc_request import CreateVccRequest
from checkbook.models.create_vcc_response import CreateVccResponse
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
    api_instance = checkbook.Vcc(api_client)
    create_vcc_request = {
        "address": null,
        "email": "john@example.com",
        "phone": null,
    }  # CreateVccRequest |

    try:
        # Create virtual card
        api_response = api_instance.post_vcc(create_vcc_request)
        print("The response of Vcc->post_vcc:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Vcc->post_vcc: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_vcc_request** | **CreateVccRequest**|  | 

### Return type

**CreateVccResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | CreateVccResponse |  -  |
**0** | Error |  -  |


## **put_vcc**
> put_vcc(vcc_id, update_vcc_request)

Update the specified vcc

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_vcc_request import UpdateVccRequest
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
    api_instance = checkbook.Vcc(api_client)
    vcc_id = "vcc_id_example"  # str |
    update_vcc_request = {
        "address": null,
        "default": null,
        "name": null,
    }  # UpdateVccRequest |

    try:
        # Update virtual card
        api_instance.put_vcc(vcc_id, update_vcc_request)
    except Exception as e:
        print("Exception when calling Vcc->put_vcc: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **vcc_id** | **str**|  | 
 **update_vcc_request** | **UpdateVccRequest**|  | 

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


