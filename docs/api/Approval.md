# Approval 
Submit and manage payments that must be approved by an authorized reviewer before funds move. All approval actions are logged for audit.


Method | HTTP request | Description
------------- | ------------- | -------------
[**delete_approval_check**](Approval.md#delete_approval_check) | **DELETE** /v3/approval/{approval_id} | Remove payment approval
[**get_approval_attachment**](Approval.md#get_approval_attachment) | **GET** /v3/approval/{approval_id}/attachment | Get attachment for payment approval
[**get_approval_check**](Approval.md#get_approval_check) | **GET** /v3/approval/{approval_id} | Get payment approval
[**get_approval_checks**](Approval.md#get_approval_checks) | **GET** /v3/approval | Get approval payments
[**post_approval_digital**](Approval.md#post_approval_digital) | **POST** /v3/approval/digital | Create approval digital payment
[**post_approval_multi**](Approval.md#post_approval_multi) | **POST** /v3/approval/multi | Create multi-party payment approval
[**post_approval_physical**](Approval.md#post_approval_physical) | **POST** /v3/approval/physical | Create physical check approval
[**post_approval_release**](Approval.md#post_approval_release) | **POST** /v3/approval/release | Approve payment
[**put_approval_check**](Approval.md#put_approval_check) | **PUT** /v3/approval/{approval_id} | Update payment approval


## **delete_approval_check**
> delete_approval_check(approval_id)

Cancel the specified check approval

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
    api_instance = checkbook.Approval(api_client)
    approval_id = "approval_id_example"  # str |

    try:
        # Remove payment approval
        api_instance.delete_approval_check(approval_id)
    except Exception as e:
        print("Exception when calling Approval->delete_approval_check: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **approval_id** | **str**|  | 

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


## **get_approval_attachment**
> bytearray get_approval_attachment(approval_id)

Get the attachment for a payment approval

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
    api_instance = checkbook.Approval(api_client)
    approval_id = "approval_id_example"  # str |

    try:
        # Get attachment for payment approval
        api_response = api_instance.get_approval_attachment(approval_id)
        print("The response of Approval->get_approval_attachment:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Approval->get_approval_attachment: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **approval_id** | **str**|  | 

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


## **get_approval_check**
> GetApprovalResponse get_approval_check(approval_id)

Get the specified payment approval

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_approval_response import GetApprovalResponse
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
    api_instance = checkbook.Approval(api_client)
    approval_id = "approval_id_example"  # str |

    try:
        # Get payment approval
        api_response = api_instance.get_approval_check(approval_id)
        print("The response of Approval->get_approval_check:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Approval->get_approval_check: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **approval_id** | **str**|  | 

### Return type

**GetApprovalResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetApprovalResponse |  -  |
**0** | Error |  -  |


## **get_approval_checks**
> GetApprovalsResponse get_approval_checks(direction=direction, end_date=end_date, page=page, per_page=per_page, q=q, sort=sort, start_date=start_date, status=status)

Return approvals

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_approvals_response import GetApprovalsResponse
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
    api_instance = checkbook.Approval(api_client)
    direction = "OUTGOING"  # str | Direction (optional)
    end_date = "2013-10-20"  # date | End date (optional)
    page = 1  # int | Page number (optional) (default to 1)
    per_page = 50  # int | Items per page (optional) (default to 50)
    q = "payment"  # str | Query (optional)
    sort = "+DATE"  # str | Sort (optional)
    start_date = "2013-10-20"  # date | Start date (optional)
    status = "PAID"  # str | Status (optional)

    try:
        # Get approval payments
        api_response = api_instance.get_approval_checks(
            direction=direction,
            end_date=end_date,
            page=page,
            per_page=per_page,
            q=q,
            sort=sort,
            start_date=start_date,
            status=status,
        )
        print("The response of Approval->get_approval_checks:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Approval->get_approval_checks: %s\n" % e)
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

**GetApprovalsResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetApprovalsResponse |  -  |
**0** | Error |  -  |


## **post_approval_digital**
> GetApprovalResponse post_approval_digital(create_digital_check_request)

Create a new approval digital payment

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_digital_check_request import CreateDigitalCheckRequest
from checkbook.models.get_approval_response import GetApprovalResponse
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
    api_instance = checkbook.Approval(api_client)
    create_digital_check_request = {
        "name": "Dwight Schrute",
        "amount": 150.0,
        "recipient": "dwight@example.com",
        "deposit_options": ["BANK", "RTP"],
    }  # CreateDigitalCheckRequest |

    try:
        # Create approval digital payment
        api_response = api_instance.post_approval_digital(create_digital_check_request)
        print("The response of Approval->post_approval_digital:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Approval->post_approval_digital: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_digital_check_request** | **CreateDigitalCheckRequest**|  | 

### Return type

**GetApprovalResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | GetApprovalResponse |  -  |
**0** | Error |  -  |


## **post_approval_multi**
> GetApprovalResponse post_approval_multi(create_multi_check_request)

Create a new multi-party payment approval

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_multi_check_request import CreateMultiCheckRequest
from checkbook.models.get_approval_response import GetApprovalResponse
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
    api_instance = checkbook.Approval(api_client)
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
        # Create multi-party payment approval
        api_response = api_instance.post_approval_multi(create_multi_check_request)
        print("The response of Approval->post_approval_multi:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Approval->post_approval_multi: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_multi_check_request** | **CreateMultiCheckRequest**|  | 

### Return type

**GetApprovalResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | GetApprovalResponse |  -  |
**0** | Error |  -  |


## **post_approval_physical**
> GetApprovalResponse post_approval_physical(create_physical_check_request)

Create a new physical check approval

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_physical_check_request import CreatePhysicalCheckRequest
from checkbook.models.get_approval_response import GetApprovalResponse
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
    api_instance = checkbook.Approval(api_client)
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
        # Create physical check approval
        api_response = api_instance.post_approval_physical(
            create_physical_check_request
        )
        print("The response of Approval->post_approval_physical:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Approval->post_approval_physical: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_physical_check_request** | **CreatePhysicalCheckRequest**|  | 

### Return type

**GetApprovalResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | GetApprovalResponse |  -  |
**0** | Error |  -  |


## **post_approval_release**
> GetCheckResponse post_approval_release(release_check_request)

Create a live payment from an approval

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_check_response import GetCheckResponse
from checkbook.models.release_check_request import ReleaseCheckRequest
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
    api_instance = checkbook.Approval(api_client)
    release_check_request = {"id": "string"}  # ReleaseCheckRequest |

    try:
        # Approve payment
        api_response = api_instance.post_approval_release(release_check_request)
        print("The response of Approval->post_approval_release:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Approval->post_approval_release: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **release_check_request** | **ReleaseCheckRequest**|  | 

### Return type

**GetCheckResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetCheckResponse |  -  |
**0** | Error |  -  |


## **put_approval_check**
> put_approval_check(approval_id, update_approval_request)

Update the specified payment approval

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_approval_request import UpdateApprovalRequest
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
    api_instance = checkbook.Approval(api_client)
    approval_id = "approval_id_example"  # str |
    update_approval_request = {
        "account": "string",
        "amount": 0.01,
        "description": null,
        "name": "string",
        "number": "string",
        "recipient": "string",
    }  # UpdateApprovalRequest |

    try:
        # Update payment approval
        api_instance.put_approval_check(approval_id, update_approval_request)
    except Exception as e:
        print("Exception when calling Approval->put_approval_check: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **approval_id** | **str**|  | 
 **update_approval_request** | **UpdateApprovalRequest**|  | 

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


