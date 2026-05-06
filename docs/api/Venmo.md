# Venmo 
Link and manage Venmo accounts used as a destination for outbound payouts, identified by the email or phone number tied to the recipient's Venmo wallet.


Method | HTTP request | Description
------------- | ------------- | -------------
[**add_venmo**](Venmo.md#add_venmo) | **POST** /v3/account/venmo | Create Venmo account
[**get_venmo**](Venmo.md#get_venmo) | **GET** /v3/account/venmo | Get Venmo accounts
[**put_venmo**](Venmo.md#put_venmo) | **PUT** /v3/account/venmo/{venmo_id} | Update Venmo account
[**remove_venmo**](Venmo.md#remove_venmo) | **DELETE** /v3/account/venmo/{venmo_id} | Remove Venmo account


## **add_venmo**
> VenmoAccountResponse add_venmo(create_venmo_request)

Add a new Venmo account for a user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_venmo_request import CreateVenmoRequest
from checkbook.models.venmo_account_response import VenmoAccountResponse
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
    api_instance = checkbook.Venmo(api_client)
    create_venmo_request = {
        "username": "dunder-mifflin@checkbook.io"
    }  # CreateVenmoRequest |

    try:
        # Create Venmo account
        api_response = api_instance.add_venmo(create_venmo_request)
        print("The response of Venmo->add_venmo:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Venmo->add_venmo: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_venmo_request** | **CreateVenmoRequest**|  | 

### Return type

**VenmoAccountResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | VenmoAccountResponse |  -  |
**0** | Error |  -  |


## **get_venmo**
> GetVenmoResponse get_venmo()

Return the Venmo accounts of a user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_venmo_response import GetVenmoResponse
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
    api_instance = checkbook.Venmo(api_client)

    try:
        # Get Venmo accounts
        api_response = api_instance.get_venmo()
        print("The response of Venmo->get_venmo:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Venmo->get_venmo: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**GetVenmoResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetVenmoResponse |  -  |
**0** | Error |  -  |


## **put_venmo**
> put_venmo(venmo_id, update_venmo_request)

Update an existing Venmo account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_venmo_request import UpdateVenmoRequest
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
    api_instance = checkbook.Venmo(api_client)
    venmo_id = "venmo_id_example"  # str |
    update_venmo_request = {"name": "string"}  # UpdateVenmoRequest |

    try:
        # Update Venmo account
        api_instance.put_venmo(venmo_id, update_venmo_request)
    except Exception as e:
        print("Exception when calling Venmo->put_venmo: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **venmo_id** | **str**|  | 
 **update_venmo_request** | **UpdateVenmoRequest**|  | 

### Return type

void (empty response body)

### Authorization

token

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | No response body. |  -  |
**0** | Error |  -  |


## **remove_venmo**
> remove_venmo(venmo_id)

Remove an existing Venmo account

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
    api_instance = checkbook.Venmo(api_client)
    venmo_id = "venmo_id_example"  # str |

    try:
        # Remove Venmo account
        api_instance.remove_venmo(venmo_id)
    except Exception as e:
        print("Exception when calling Venmo->remove_venmo: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **venmo_id** | **str**|  | 

### Return type

void (empty response body)

### Authorization

token

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | No response body. |  -  |
**0** | Error |  -  |


