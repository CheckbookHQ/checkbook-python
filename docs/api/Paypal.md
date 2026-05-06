# Paypal 
Link and manage PayPal accounts used as a destination for outbound payouts, identified by the email or phone number tied to the recipient's PayPal profile.


Method | HTTP request | Description
------------- | ------------- | -------------
[**add_paypal**](Paypal.md#add_paypal) | **POST** /v3/account/paypal | Create PayPal account
[**get_paypal**](Paypal.md#get_paypal) | **GET** /v3/account/paypal | Get PayPal accounts
[**put_paypal**](Paypal.md#put_paypal) | **PUT** /v3/account/paypal/{paypal_id} | Update PayPal account
[**remove_paypal**](Paypal.md#remove_paypal) | **DELETE** /v3/account/paypal/{paypal_id} | Remove PayPal account


## **add_paypal**
> PaypalAccountResponse add_paypal(create_paypal_request)

Add a new Paypal account for a user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_paypal_request import CreatePaypalRequest
from checkbook.models.paypal_account_response import PaypalAccountResponse
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
    api_instance = checkbook.Paypal(api_client)
    create_paypal_request = {"username": "john@example.com"}  # CreatePaypalRequest |

    try:
        # Create PayPal account
        api_response = api_instance.add_paypal(create_paypal_request)
        print("The response of Paypal->add_paypal:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Paypal->add_paypal: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_paypal_request** | **CreatePaypalRequest**|  | 

### Return type

**PaypalAccountResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | PaypalAccountResponse |  -  |
**0** | Error |  -  |


## **get_paypal**
> GetPaypalResponse get_paypal()

Return the Paypal accounts of a user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_paypal_response import GetPaypalResponse
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
    api_instance = checkbook.Paypal(api_client)

    try:
        # Get PayPal accounts
        api_response = api_instance.get_paypal()
        print("The response of Paypal->get_paypal:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Paypal->get_paypal: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**GetPaypalResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetPaypalResponse |  -  |
**0** | Error |  -  |


## **put_paypal**
> put_paypal(paypal_id, update_paypal_request)

Update an existing Paypal account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_paypal_request import UpdatePaypalRequest
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
    api_instance = checkbook.Paypal(api_client)
    paypal_id = "paypal_id_example"  # str |
    update_paypal_request = {"name": "string"}  # UpdatePaypalRequest |

    try:
        # Update PayPal account
        api_instance.put_paypal(paypal_id, update_paypal_request)
    except Exception as e:
        print("Exception when calling Paypal->put_paypal: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **paypal_id** | **str**|  | 
 **update_paypal_request** | **UpdatePaypalRequest**|  | 

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


## **remove_paypal**
> remove_paypal(paypal_id)

Remove an existing PayPal account

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
    api_instance = checkbook.Paypal(api_client)
    paypal_id = "paypal_id_example"  # str |

    try:
        # Remove PayPal account
        api_instance.remove_paypal(paypal_id)
    except Exception as e:
        print("Exception when calling Paypal->remove_paypal: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **paypal_id** | **str**|  | 

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


