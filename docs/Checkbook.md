# Checkbook 
Order and manage physical checkbooks shipped to users for on-demand check issuance. Each order progresses through statuses such as `pending`, `in_process`, `mailed`, `canceled`, or `returned`, with shipment tracking available for mailed checkbooks.


Method | HTTP request | Description
------------- | ------------- | -------------
[**delete_checkbook**](Checkbook.md#delete_checkbook) | **DELETE** /v3/checkbook/{checkbook_id} | Cancel a checkbook
[**get_checkbook**](Checkbook.md#get_checkbook) | **GET** /v3/checkbook/{checkbook_id} | Get checkbook
[**get_checkbook_tracking**](Checkbook.md#get_checkbook_tracking) | **GET** /v3/checkbook/{checkbook_id}/tracking | Get tracking details on checkbooks
[**get_checkbooks**](Checkbook.md#get_checkbooks) | **GET** /v3/checkbook | Get checkbooks
[**order_checkbook**](Checkbook.md#order_checkbook) | **POST** /v3/checkbook | Order a checkbook


# **delete_checkbook**
> delete_checkbook(checkbook_id)

Cancel the specified checkbook order

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
    api_instance = checkbook.Checkbook(api_client)
    checkbook_id = "checkbook_id_example"  # str |

    try:
        # Cancel a checkbook
        api_instance.delete_checkbook(checkbook_id)
    except Exception as e:
        print("Exception when calling Checkbook->delete_checkbook: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **checkbook_id** | **str**|  | 

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


# **get_checkbook**
> GetCheckbookResponse get_checkbook(checkbook_id)

Get the specified checkbook

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_checkbook_response import GetCheckbookResponse
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
    api_instance = checkbook.Checkbook(api_client)
    checkbook_id = "checkbook_id_example"  # str |

    try:
        # Get checkbook
        api_response = api_instance.get_checkbook(checkbook_id)
        print("The response of Checkbook->get_checkbook:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Checkbook->get_checkbook: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **checkbook_id** | **str**|  | 

### Return type

[**GetCheckbookResponse**](GetCheckbookResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetCheckbookResponse |  -  |
**0** | Error |  -  |


# **get_checkbook_tracking**
> GetCheckbookTrackingResponseExpress get_checkbook_tracking(checkbook_id)

Get tracking details on checkbook

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_checkbook_tracking_response_express import (
    GetCheckbookTrackingResponseExpress,
)
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
    api_instance = checkbook.Checkbook(api_client)
    checkbook_id = "checkbook_id_example"  # str |

    try:
        # Get tracking details on checkbooks
        api_response = api_instance.get_checkbook_tracking(checkbook_id)
        print("The response of Checkbook->get_checkbook_tracking:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Checkbook->get_checkbook_tracking: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **checkbook_id** | **str**|  | 

### Return type

[**GetCheckbookTrackingResponseExpress**](GetCheckbookTrackingResponseExpress.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetCheckbookTrackingResponseExpress |  -  |
**0** | Error |  -  |


# **get_checkbooks**
> GetCheckbooksResponse get_checkbooks(page=page, per_page=per_page, q=q)

Return the checkbooks issued for a user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_checkbooks_response import GetCheckbooksResponse
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
    api_instance = checkbook.Checkbook(api_client)
    page = 1  # int | Page number (optional) (default to 1)
    per_page = 50  # int | Items per page (optional) (default to 50)
    q = "q_example"  # str | Query (optional)

    try:
        # Get checkbooks
        api_response = api_instance.get_checkbooks(page=page, per_page=per_page, q=q)
        print("The response of Checkbook->get_checkbooks:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Checkbook->get_checkbooks: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| Page number | [optional] [default to 1]
 **per_page** | **int**| Items per page | [optional] [default to 50]
 **q** | **str**| Query | [optional] 

### Return type

[**GetCheckbooksResponse**](GetCheckbooksResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetCheckbooksResponse |  -  |
**0** | Error |  -  |


# **order_checkbook**
> GetCheckbookResponse order_checkbook(base_checkbook_request)

Order a new Checkbook  
> [!NOTE]
> The address printed on the checkbook is the user's merchant address provided in `merchant` object when calling [`PUT /v3/user`](#tag/user/put/v3/user). If the user does not have a merchant address, the shipping address provided in the `recipient` object will be printed on the checkbook.

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.base_checkbook_request import BaseCheckbookRequest
from checkbook.models.get_checkbook_response import GetCheckbookResponse
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
    api_instance = checkbook.Checkbook(api_client)
    base_checkbook_request = {
        "account": "1e31faa3c38f451aa6095fbd84e6bcbb",
        "mail_type": "USPS_FIRST_CLASS",
        "number": "5001",
        "recipient": null,
    }  # BaseCheckbookRequest |

    try:
        # Order a checkbook
        api_response = api_instance.order_checkbook(base_checkbook_request)
        print("The response of Checkbook->order_checkbook:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Checkbook->order_checkbook: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **base_checkbook_request** | [**BaseCheckbookRequest**](BaseCheckbookRequest.md)|  | 

### Return type

[**GetCheckbookResponse**](GetCheckbookResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | GetCheckbookResponse |  -  |
**0** | Error |  -  |


