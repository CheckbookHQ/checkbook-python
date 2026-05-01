# Payment 
Send, track, and manage payments — the core resource for moving money. A payment transfers funds from a user to one or more recipients as a digital payment, mailed check, or multi-party payment, settling over supported rails. Payments can be previewed, endorsed, printed, voided, deposited, or inspected for attachments, deposit details, tracking, failures, and verification codes.


Method | HTTP request | Description
------------- | ------------- | -------------
[**delete_check**](Payment.md#delete_check) | **DELETE** /v3/check/{check_id} | Void a payment
[**get_check**](Payment.md#get_check) | **GET** /v3/check/{check_id} | Get payment
[**get_check_attachment**](Payment.md#get_check_attachment) | **GET** /v3/check/{check_id}/attachment | Get attachment for a payment
[**get_check_deposit**](Payment.md#get_check_deposit) | **GET** /v3/check/{check_id}/deposit | Get deposit details
[**get_check_fail**](Payment.md#get_check_fail) | **GET** /v3/check/{check_id}/fail | Get details on failed payment
[**get_check_tracking**](Payment.md#get_check_tracking) | **GET** /v3/check/{check_id}/tracking | Get tracking details on mailed check
[**get_check_verification**](Payment.md#get_check_verification) | **GET** /v3/check/{check_id}/verification | Get verification code
[**get_checks**](Payment.md#get_checks) | **GET** /v3/check | Get sent/received payments
[**post_check_deposit**](Payment.md#post_check_deposit) | **POST** /v3/check/deposit/{check_id} | Deposit a payment
[**post_check_digital**](Payment.md#post_check_digital) | **POST** /v3/check/digital | Create a digital payment
[**post_check_endorse**](Payment.md#post_check_endorse) | **POST** /v3/check/endorse/{check_id} | Endorse a multi-party payment
[**post_check_multi**](Payment.md#post_check_multi) | **POST** /v3/check/multi | Create a multi-party payment
[**post_check_notify**](Payment.md#post_check_notify) | **POST** /v3/check/notify/{check_id} | Resend payment notification
[**post_check_physical**](Payment.md#post_check_physical) | **POST** /v3/check/physical | Create a physical check
[**post_check_preview**](Payment.md#post_check_preview) | **POST** /v3/check/preview | Preview payment
[**post_check_print**](Payment.md#post_check_print) | **POST** /v3/check/print/{check_id} | Print a payment
[**post_check_webhook**](Payment.md#post_check_webhook) | **PUT** /v3/check/webhook/{check_id} | Update a sandbox payment status


# **delete_check**
> delete_check(check_id)

Void the specified payment

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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |

    try:
        # Void a payment
        api_instance.delete_check(check_id)
    except Exception as e:
        print("Exception when calling Payment->delete_check: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 

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


# **get_check**
> GetCheckResponse get_check(check_id)

Get the specified payment

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_check_response import GetCheckResponse
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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |

    try:
        # Get payment
        api_response = api_instance.get_check(check_id)
        print("The response of Payment->get_check:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->get_check: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 

### Return type

[**GetCheckResponse**](GetCheckResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetCheckResponse |  -  |
**0** | Error |  -  |


# **get_check_attachment**
> bytearray get_check_attachment(check_id)

Get the attachment for a payment

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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |

    try:
        # Get attachment for a payment
        api_response = api_instance.get_check_attachment(check_id)
        print("The response of Payment->get_check_attachment:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->get_check_attachment: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 

### Return type

**bytearray**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/pdf, application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | PDF binary file |  -  |
**0** | Error |  -  |


# **get_check_deposit**
> GetCheckDepositedResponse get_check_deposit(check_id)

Get details on a deposited payment

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_check_deposited_response import GetCheckDepositedResponse
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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |

    try:
        # Get deposit details
        api_response = api_instance.get_check_deposit(check_id)
        print("The response of Payment->get_check_deposit:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->get_check_deposit: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 

### Return type

[**GetCheckDepositedResponse**](GetCheckDepositedResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetCheckDepositedResponse |  -  |
**0** | Error |  -  |


# **get_check_fail**
> GetCheckFailedResponse get_check_fail(check_id)

Get details on a failed payment

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_check_failed_response import GetCheckFailedResponse
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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |

    try:
        # Get details on failed payment
        api_response = api_instance.get_check_fail(check_id)
        print("The response of Payment->get_check_fail:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->get_check_fail: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 

### Return type

[**GetCheckFailedResponse**](GetCheckFailedResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetCheckFailedResponse |  -  |
**0** | Error |  -  |


# **get_check_tracking**
> GetCheckTrackingResponseExpress get_check_tracking(check_id)

Get tracking details on a mailed check

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_check_tracking_response_express import (
    GetCheckTrackingResponseExpress,
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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |

    try:
        # Get tracking details on mailed check
        api_response = api_instance.get_check_tracking(check_id)
        print("The response of Payment->get_check_tracking:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->get_check_tracking: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 

### Return type

[**GetCheckTrackingResponseExpress**](GetCheckTrackingResponseExpress.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetCheckTrackingResponseExpress |  -  |
**0** | Error |  -  |


# **get_check_verification**
> VerifyCheckResponse get_check_verification(check_id)

Get the verification code

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.verify_check_response import VerifyCheckResponse
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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |

    try:
        # Get verification code
        api_response = api_instance.get_check_verification(check_id)
        print("The response of Payment->get_check_verification:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->get_check_verification: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 

### Return type

[**VerifyCheckResponse**](VerifyCheckResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Verification code |  -  |
**0** | Error |  -  |


# **get_checks**
> GetChecksResponse get_checks(direction=direction, end_date=end_date, page=page, per_page=per_page, q=q, sort=sort, start_date=start_date, status=status)

Return the sent/received payments

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_checks_response import GetChecksResponse
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
    api_instance = checkbook.Payment(api_client)
    direction = "OUTGOING"  # str | Direction (optional)
    end_date = "2013-10-20"  # date | End date (optional)
    page = 1  # int | Page number (optional) (default to 1)
    per_page = 50  # int | Items per page (optional) (default to 50)
    q = "payment"  # str | Query (optional)
    sort = "+DATE"  # str | Sort (optional)
    start_date = "2013-10-20"  # date | Start date (optional)
    status = "PAID"  # str | Status (optional)

    try:
        # Get sent/received payments
        api_response = api_instance.get_checks(
            direction=direction,
            end_date=end_date,
            page=page,
            per_page=per_page,
            q=q,
            sort=sort,
            start_date=start_date,
            status=status,
        )
        print("The response of Payment->get_checks:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->get_checks: %s\n" % e)
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

[**GetChecksResponse**](GetChecksResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetChecksResponse |  -  |
**0** | Error |  -  |


# **post_check_deposit**
> GetCheckResponse post_check_deposit(check_id, deposit_check_request)

Deposit a payment

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.deposit_check_request import DepositCheckRequest
from checkbook.models.get_check_response import GetCheckResponse
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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |
    deposit_check_request = {"account": "string"}  # DepositCheckRequest |

    try:
        # Deposit a payment
        api_response = api_instance.post_check_deposit(check_id, deposit_check_request)
        print("The response of Payment->post_check_deposit:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->post_check_deposit: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 
 **deposit_check_request** | [**DepositCheckRequest**](DepositCheckRequest.md)|  | 

### Return type

[**GetCheckResponse**](GetCheckResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | GetCheckResponse |  -  |
**0** | Error |  -  |


# **post_check_digital**
> GetCheckResponse post_check_digital(create_digital_check_request)

Create a digital payment 
> [!NOTE]
> **Common Errors**
>
> - **`Invalid deposit option`:** If deposit options do not include `PRINT`, `MAIL`, or `BANK`, please ensure the payment is funded by a wallet. If you still encounter this error, please contact support@checkbook.io to ensure the specified payment rails are enabled for your account.
> - **`Amount is larger than $2000 and requires signature`:** Please add a signature to the sender using [`v3/user/signature`](#tag/user/post/v3/user/signature). A signature is required for users to send out payments over $2000.

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_digital_check_request import CreateDigitalCheckRequest
from checkbook.models.get_check_response import GetCheckResponse
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
    api_instance = checkbook.Payment(api_client)
    create_digital_check_request = {
        "name": "Dwight Schrute",
        "amount": 150.0,
        "recipient": "dwight@example.com",
        "deposit_options": ["BANK", "RTP"],
    }  # CreateDigitalCheckRequest |

    try:
        # Create a digital payment
        api_response = api_instance.post_check_digital(create_digital_check_request)
        print("The response of Payment->post_check_digital:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->post_check_digital: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_digital_check_request** | [**CreateDigitalCheckRequest**](CreateDigitalCheckRequest.md)|  | 

### Return type

[**GetCheckResponse**](GetCheckResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | GetCheckResponse |  -  |
**0** | Error |  -  |


# **post_check_endorse**
> post_check_endorse(check_id, endorse_check_request)

Endorse a multi party payment

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.endorse_check_request import EndorseCheckRequest
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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |
    endorse_check_request = {
        "name": "Johnny Appleseed",
        "signature": null,
    }  # EndorseCheckRequest |

    try:
        # Endorse a multi-party payment
        api_instance.post_check_endorse(check_id, endorse_check_request)
    except Exception as e:
        print("Exception when calling Payment->post_check_endorse: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 
 **endorse_check_request** | [**EndorseCheckRequest**](EndorseCheckRequest.md)|  | 

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


# **post_check_multi**
> GetCheckResponse post_check_multi(create_multi_check_request)

Create a new multi party payment

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_multi_check_request import CreateMultiCheckRequest
from checkbook.models.get_check_response import GetCheckResponse
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
    api_instance = checkbook.Payment(api_client)
    create_multi_check_request = {
        "account": "string",
        "amount": 5.23,
        "attachment": null,
        "comment": "string",
        "deposit_options": [["MAIL", "CARD"]],
        "description": "Example memo",
        "number": "5001",
        "recipients": [null],
        "remittance_advice": [null],
    }  # CreateMultiCheckRequest |

    try:
        # Create a multi-party payment
        api_response = api_instance.post_check_multi(create_multi_check_request)
        print("The response of Payment->post_check_multi:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->post_check_multi: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_multi_check_request** | [**CreateMultiCheckRequest**](CreateMultiCheckRequest.md)|  | 

### Return type

[**GetCheckResponse**](GetCheckResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | GetCheckResponse |  -  |
**0** | Error |  -  |


# **post_check_notify**
> post_check_notify(check_id)

Resend payment notification

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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |

    try:
        # Resend payment notification
        api_instance.post_check_notify(check_id)
    except Exception as e:
        print("Exception when calling Payment->post_check_notify: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 

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
**204** | No response body. |  -  |
**0** | Error |  -  |


# **post_check_physical**
> GetCheckResponse post_check_physical(create_physical_check_request)

Create a new paper check

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_physical_check_request import CreatePhysicalCheckRequest
from checkbook.models.get_check_response import GetCheckResponse
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
    api_instance = checkbook.Payment(api_client)
    create_physical_check_request = {
        "account": "string",
        "amount": 5.23,
        "attachment": null,
        "comment": "string",
        "description": "Example memo",
        "mail_type": "USPS_FIRST_CLASS",
        "name": "Widgets Inc.",
        "number": "5001",
        "recipient": null,
        "remittance_advice": "string",
    }  # CreatePhysicalCheckRequest |

    try:
        # Create a physical check
        api_response = api_instance.post_check_physical(create_physical_check_request)
        print("The response of Payment->post_check_physical:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->post_check_physical: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_physical_check_request** | [**CreatePhysicalCheckRequest**](CreatePhysicalCheckRequest.md)|  | 

### Return type

[**GetCheckResponse**](GetCheckResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | GetCheckResponse |  -  |
**0** | Error |  -  |


# **post_check_preview**
> PreviewCheckResponse post_check_preview(preview_check_request)

Preview a new payment

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.preview_check_request import PreviewCheckRequest
from checkbook.models.preview_check_response import PreviewCheckResponse
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
    api_instance = checkbook.Payment(api_client)
    preview_check_request = {
        "account": "string",
        "amount": 0.01,
        "description": "Test memo",
        "name": "Widgets Inc.",
        "number": "string",
    }  # PreviewCheckRequest |

    try:
        # Preview payment
        api_response = api_instance.post_check_preview(preview_check_request)
        print("The response of Payment->post_check_preview:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->post_check_preview: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **preview_check_request** | [**PreviewCheckRequest**](PreviewCheckRequest.md)|  | 

### Return type

[**PreviewCheckResponse**](PreviewCheckResponse.md)

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | PreviewCheckResponse |  -  |
**0** | Error |  -  |


# **post_check_print**
> bytearray post_check_print(check_id)

Print a check

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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |

    try:
        # Print a payment
        api_response = api_instance.post_check_print(check_id)
        print("The response of Payment->post_check_print:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Payment->post_check_print: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 

### Return type

**bytearray**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/pdf, application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | PDF binary file |  -  |
**0** | Error |  -  |


# **post_check_webhook**
> post_check_webhook(check_id, trigger_webhook_request)

Update a payment's status in sandbox. Triggers a sandbox check webhook notification.

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.trigger_webhook_request import TriggerWebhookRequest
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
    api_instance = checkbook.Payment(api_client)
    check_id = "check_id_example"  # str |
    trigger_webhook_request = {
        "options": null,
        "status": "PAID",
    }  # TriggerWebhookRequest |

    try:
        # Update a sandbox payment status
        api_instance.post_check_webhook(check_id, trigger_webhook_request)
    except Exception as e:
        print("Exception when calling Payment->post_check_webhook: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **check_id** | **str**|  | 
 **trigger_webhook_request** | [**TriggerWebhookRequest**](TriggerWebhookRequest.md)|  | 

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
**204** | No response body. |  -  |
**0** | Error |  -  |


