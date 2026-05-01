# Wire 
Link and manage wire accounts used as the destination for outbound wire transfers, intended for time-sensitive or high-value payments. Wires submitted before the 3:00 PM PT cutoff settle the same day.


Method | HTTP request | Description
------------- | ------------- | -------------
[**add_wire**](Wire.md#add_wire) | **POST** /v3/account/wire | Create wire account
[**get_wire**](Wire.md#get_wire) | **GET** /v3/account/wire | Get wire accounts
[**put_wire**](Wire.md#put_wire) | **PUT** /v3/account/wire/{account_id} | Update Wire account
[**remove_wire**](Wire.md#remove_wire) | **DELETE** /v3/account/wire/{wire_id} | Remove wire account


# **add_wire**
> WireAccountResponse add_wire(create_wire_request)

Create a new wire account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_wire_request import CreateWireRequest
from checkbook.models.wire_account_response import WireAccountResponse
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
    api_instance = checkbook.Wire(api_client)
    create_wire_request = {
        "account": "428100000",
        "name": "Checking account",
        "routing": "021000021",
        "type": "CHECKING",
    }  # CreateWireRequest |

    try:
        # Create wire account
        api_response = api_instance.add_wire(create_wire_request)
        print("The response of Wire->add_wire:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Wire->add_wire: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_wire_request** | **CreateWireRequest**|  | 

### Return type

**WireAccountResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | WireAccountResponse |  -  |
**0** | Error |  -  |


# **get_wire**
> GetWireResponse get_wire()

Return the wire accounts

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_wire_response import GetWireResponse
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
    api_instance = checkbook.Wire(api_client)

    try:
        # Get wire accounts
        api_response = api_instance.get_wire()
        print("The response of Wire->get_wire:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Wire->get_wire: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**GetWireResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetWireResponse |  -  |
**0** | Error |  -  |


# **put_wire**
> put_wire(account_id, update_wire_request)

Update an existing wire account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_wire_request import UpdateWireRequest
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
    api_instance = checkbook.Wire(api_client)
    account_id = "account_id_example"  # str |
    update_wire_request = {"name": "Checking account"}  # UpdateWireRequest |

    try:
        # Update Wire account
        api_instance.put_wire(account_id, update_wire_request)
    except Exception as e:
        print("Exception when calling Wire->put_wire: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **account_id** | **str**|  | 
 **update_wire_request** | **UpdateWireRequest**|  | 

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


# **remove_wire**
> remove_wire(wire_id)

Remove an existing wire account

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
    api_instance = checkbook.Wire(api_client)
    wire_id = "wire_id_example"  # str |

    try:
        # Remove wire account
        api_instance.remove_wire(wire_id)
    except Exception as e:
        print("Exception when calling Wire->remove_wire: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **wire_id** | **str**|  | 

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


