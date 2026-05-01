# Subscription 
Schedule and manage recurring payments and invoices that run on a weekly or monthly cadence. Checkbook processes scheduled items daily between 4–5 PM UTC.


Method | HTTP request | Description
------------- | ------------- | -------------
[**delete_subscription**](Subscription.md#delete_subscription) | **DELETE** /v3/subscription/{subscription_id} | Remove subscription
[**get_subscription**](Subscription.md#get_subscription) | **GET** /v3/subscription/{subscription_id} | Get subscription
[**get_subscriptions**](Subscription.md#get_subscriptions) | **GET** /v3/subscription | Get subscriptions
[**post_subscription_check**](Subscription.md#post_subscription_check) | **POST** /v3/subscription/check | Create payment subscription
[**post_subscription_invoice**](Subscription.md#post_subscription_invoice) | **POST** /v3/subscription/invoice | Create invoice subscription
[**put_subscription**](Subscription.md#put_subscription) | **PUT** /v3/subscription/{subscription_id} | Update subscription


# **delete_subscription**
> delete_subscription(subscription_id)

Remove the specified subscription

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
    api_instance = checkbook.Subscription(api_client)
    subscription_id = "subscription_id_example"  # str |

    try:
        # Remove subscription
        api_instance.delete_subscription(subscription_id)
    except Exception as e:
        print("Exception when calling Subscription->delete_subscription: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **subscription_id** | **str**|  | 

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


# **get_subscription**
> GetSubscriptionResponse get_subscription(subscription_id)

Get the specified subscription

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_subscription_response import GetSubscriptionResponse
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
    api_instance = checkbook.Subscription(api_client)
    subscription_id = "subscription_id_example"  # str |

    try:
        # Get subscription
        api_response = api_instance.get_subscription(subscription_id)
        print("The response of Subscription->get_subscription:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Subscription->get_subscription: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **subscription_id** | **str**|  | 

### Return type

[**GetSubscriptionResponse**](GetSubscriptionResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetSubscriptionResponse |  -  |
**0** | Error |  -  |


# **get_subscriptions**
> GetSubscriptionsResponse get_subscriptions(direction=direction, end_date=end_date, page=page, per_page=per_page, q=q, sort=sort, start_date=start_date, status=status)

Return the subscriptions

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_subscriptions_response import GetSubscriptionsResponse
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
    api_instance = checkbook.Subscription(api_client)
    direction = "direction_example"  # str | Direction (optional)
    end_date = "2013-10-20"  # date | End date (optional)
    page = 1  # int | Page number (optional) (default to 1)
    per_page = 50  # int | Items per page (optional) (default to 50)
    q = "q_example"  # str | Query (optional)
    sort = "sort_example"  # str | Sort (optional)
    start_date = "2013-10-20"  # date | Start date (optional)
    status = "status_example"  # str | Status (optional)

    try:
        # Get subscriptions
        api_response = api_instance.get_subscriptions(
            direction=direction,
            end_date=end_date,
            page=page,
            per_page=per_page,
            q=q,
            sort=sort,
            start_date=start_date,
            status=status,
        )
        print("The response of Subscription->get_subscriptions:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Subscription->get_subscriptions: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **direction** | **str**| Direction | [optional] 
 **end_date** | **date**| End date | [optional] 
 **page** | **int**| Page number | [optional] [default to 1]
 **per_page** | **int**| Items per page | [optional] [default to 50]
 **q** | **str**| Query | [optional] 
 **sort** | **str**| Sort | [optional] 
 **start_date** | **date**| Start date | [optional] 
 **status** | **str**| Status | [optional] 

### Return type

[**GetSubscriptionsResponse**](GetSubscriptionsResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetSubscriptionsResponse |  -  |
**0** | Error |  -  |


# **post_subscription_check**
> CreateSubscriptionResponse post_subscription_check(create_check_subscription_request)

Create a new payment subscription

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_check_subscription_request import (
    CreateCheckSubscriptionRequest,
)
from checkbook.models.create_subscription_response import CreateSubscriptionResponse
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
    api_instance = checkbook.Subscription(api_client)
    create_check_subscription_request = {
        "account": "string",
        "amount": 0.01,
        "description": null,
        "duration": null,
        "interval": "WEEKLY",
        "name": "string",
        "recipient": "string",
        "remittance_advice": [null],
        "start_date": null,
    }  # CreateCheckSubscriptionRequest |

    try:
        # Create payment subscription
        api_response = api_instance.post_subscription_check(
            create_check_subscription_request
        )
        print("The response of Subscription->post_subscription_check:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Subscription->post_subscription_check: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_check_subscription_request** | [**CreateCheckSubscriptionRequest**](CreateCheckSubscriptionRequest.md)|  | 

### Return type

[**CreateSubscriptionResponse**](CreateSubscriptionResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | CreateSubscriptionResponse |  -  |
**0** | Error |  -  |


# **post_subscription_invoice**
> CreateSubscriptionResponse post_subscription_invoice(create_invoice_subscription_request)

Create a new invoice subscription

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_invoice_subscription_request import (
    CreateInvoiceSubscriptionRequest,
)
from checkbook.models.create_subscription_response import CreateSubscriptionResponse
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
    api_instance = checkbook.Subscription(api_client)
    create_invoice_subscription_request = {
        "account": "string",
        "amount": 0.01,
        "description": "string",
        "duration": null,
        "interval": "WEEKLY",
        "name": "string",
        "recipient": "string",
        "start_date": null,
    }  # CreateInvoiceSubscriptionRequest |

    try:
        # Create invoice subscription
        api_response = api_instance.post_subscription_invoice(
            create_invoice_subscription_request
        )
        print("The response of Subscription->post_subscription_invoice:\n")
        pprint(api_response)
    except Exception as e:
        print(
            "Exception when calling Subscription->post_subscription_invoice: %s\n" % e
        )
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_invoice_subscription_request** | [**CreateInvoiceSubscriptionRequest**](CreateInvoiceSubscriptionRequest.md)|  | 

### Return type

[**CreateSubscriptionResponse**](CreateSubscriptionResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | CreateSubscriptionResponse |  -  |
**0** | Error |  -  |


# **put_subscription**
> put_subscription(subscription_id, update_subscription_request)

Update the specified subscription

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_subscription_request import UpdateSubscriptionRequest
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
    api_instance = checkbook.Subscription(api_client)
    subscription_id = "subscription_id_example"  # str |
    update_subscription_request = {
        "autopay": true,
        "skipped": [0],
    }  # UpdateSubscriptionRequest |

    try:
        # Update subscription
        api_instance.put_subscription(subscription_id, update_subscription_request)
    except Exception as e:
        print("Exception when calling Subscription->put_subscription: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **subscription_id** | **str**|  | 
 **update_subscription_request** | [**UpdateSubscriptionRequest**](UpdateSubscriptionRequest.md)|  | 

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


