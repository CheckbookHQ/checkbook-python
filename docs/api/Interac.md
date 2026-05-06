# Interac 
Link and manage Interac e-Transfer accounts for receiving money in Canada, identified by the email or phone number tied to the recipient's Interac profile.


Method | HTTP request | Description
------------- | ------------- | -------------
[**add_interac**](Interac.md#add_interac) | **POST** /v3/account/interac | Create Interac account
[**get_interac**](Interac.md#get_interac) | **GET** /v3/account/interac | Get Interac accounts
[**put_interac**](Interac.md#put_interac) | **PUT** /v3/account/interac/{interac_id} | Update Interac account
[**remove_interac**](Interac.md#remove_interac) | **DELETE** /v3/account/interac/{interac_id} | Remove Interac account


## **add_interac**
> InteracAccountResponse add_interac(create_interac_request)

Add a new Interac account for a user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_interac_request import CreateInteracRequest
from checkbook.models.interac_account_response import InteracAccountResponse
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
    api_instance = checkbook.Interac(api_client)
    create_interac_request = {"username": "dschrute"}  # CreateInteracRequest |

    try:
        # Create Interac account
        api_response = api_instance.add_interac(create_interac_request)
        print("The response of Interac->add_interac:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Interac->add_interac: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_interac_request** | **CreateInteracRequest**|  | 

### Return type

**InteracAccountResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | InteracAccountResponse |  -  |
**0** | Error |  -  |


## **get_interac**
> GetInteracResponse get_interac()

Return the Interac accounts of a user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_interac_response import GetInteracResponse
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
    api_instance = checkbook.Interac(api_client)

    try:
        # Get Interac accounts
        api_response = api_instance.get_interac()
        print("The response of Interac->get_interac:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Interac->get_interac: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**GetInteracResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetInteracResponse |  -  |
**0** | Error |  -  |


## **put_interac**
> put_interac(interac_id, update_interac_request)

Update an existing Interac account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_interac_request import UpdateInteracRequest
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
    api_instance = checkbook.Interac(api_client)
    interac_id = "interac_id_example"  # str |
    update_interac_request = {"name": "string"}  # UpdateInteracRequest |

    try:
        # Update Interac account
        api_instance.put_interac(interac_id, update_interac_request)
    except Exception as e:
        print("Exception when calling Interac->put_interac: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **interac_id** | **str**|  | 
 **update_interac_request** | **UpdateInteracRequest**|  | 

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


## **remove_interac**
> remove_interac(interac_id)

Remove an existing Interac account

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
    api_instance = checkbook.Interac(api_client)
    interac_id = "interac_id_example"  # str |

    try:
        # Remove Interac account
        api_instance.remove_interac(interac_id)
    except Exception as e:
        print("Exception when calling Interac->remove_interac: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **interac_id** | **str**|  | 

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


