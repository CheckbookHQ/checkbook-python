# Invoice 
Send, manage, and pay invoices settled via ACH. Invoices can be sent on behalf of verified users to other users or external payers.


Method | HTTP request | Description
------------- | ------------- | -------------
[**delete_invoice**](Invoice.md#delete_invoice) | **DELETE** /v3/invoice/{invoice_id} | Void an invoice
[**get_invoice**](Invoice.md#get_invoice) | **GET** /v3/invoice/{invoice_id} | Get invoice
[**get_invoice_attachment**](Invoice.md#get_invoice_attachment) | **GET** /v3/invoice/{invoice_id}/attachment | Get attachment for an invoice
[**get_invoices**](Invoice.md#get_invoices) | **GET** /v3/invoice | Get sent/received invoices
[**post_invoice**](Invoice.md#post_invoice) | **POST** /v3/invoice | Create an invoice
[**post_invoice_payment**](Invoice.md#post_invoice_payment) | **POST** /v3/invoice/payment | Pay an invoice


# **delete_invoice**
> delete_invoice(invoice_id)

Cancel the specified invoice

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
    api_instance = checkbook.Invoice(api_client)
    invoice_id = "invoice_id_example"  # str |

    try:
        # Void an invoice
        api_instance.delete_invoice(invoice_id)
    except Exception as e:
        print("Exception when calling Invoice->delete_invoice: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **invoice_id** | **str**|  | 

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


# **get_invoice**
> GetInvoiceResponse get_invoice(invoice_id)

Get the specified invoice

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_invoice_response import GetInvoiceResponse
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
    api_instance = checkbook.Invoice(api_client)
    invoice_id = "invoice_id_example"  # str |

    try:
        # Get invoice
        api_response = api_instance.get_invoice(invoice_id)
        print("The response of Invoice->get_invoice:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Invoice->get_invoice: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **invoice_id** | **str**|  | 

### Return type

**GetInvoiceResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetInvoiceResponse |  -  |
**0** | Error |  -  |


# **get_invoice_attachment**
> bytearray get_invoice_attachment(invoice_id)

Get the attachment for an invoice

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
    api_instance = checkbook.Invoice(api_client)
    invoice_id = "invoice_id_example"  # str |

    try:
        # Get attachment for an invoice
        api_response = api_instance.get_invoice_attachment(invoice_id)
        print("The response of Invoice->get_invoice_attachment:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Invoice->get_invoice_attachment: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **invoice_id** | **str**|  | 

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


# **get_invoices**
> GetInvoicesResponse get_invoices(direction=direction, end_date=end_date, page=page, per_page=per_page, q=q, sort=sort, start_date=start_date, status=status)

Get sent/received invoices

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_invoices_response import GetInvoicesResponse
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
    api_instance = checkbook.Invoice(api_client)
    direction = "direction_example"  # str | Direction (optional)
    end_date = "2013-10-20"  # date | End date (optional)
    page = 1  # int | Page number (optional) (default to 1)
    per_page = 50  # int | Items per page (optional) (default to 50)
    q = "q_example"  # str | Query (optional)
    sort = "sort_example"  # str | Sort (optional)
    start_date = "2013-10-20"  # date | Start date (optional)
    status = "status_example"  # str | Status (optional)

    try:
        # Get sent/received invoices
        api_response = api_instance.get_invoices(
            direction=direction,
            end_date=end_date,
            page=page,
            per_page=per_page,
            q=q,
            sort=sort,
            start_date=start_date,
            status=status,
        )
        print("The response of Invoice->get_invoices:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Invoice->get_invoices: %s\n" % e)
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

**GetInvoicesResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetInvoicesResponse |  -  |
**0** | Error |  -  |


# **post_invoice**
> CreateInvoiceResponse post_invoice(create_invoice_request)

Create a new invoice

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_invoice_request import CreateInvoiceRequest
from checkbook.models.create_invoice_response import CreateInvoiceResponse
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
    api_instance = checkbook.Invoice(api_client)
    create_invoice_request = {
        "account": "string",
        "amount": 0.01,
        "attachment": null,
        "description": "string",
        "name": "string",
        "number": null,
        "recipient": "string",
    }  # CreateInvoiceRequest |

    try:
        # Create an invoice
        api_response = api_instance.post_invoice(create_invoice_request)
        print("The response of Invoice->post_invoice:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Invoice->post_invoice: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_invoice_request** | **CreateInvoiceRequest**|  | 

### Return type

**CreateInvoiceResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | CreateInvoiceResponse |  -  |
**0** | Error |  -  |


# **post_invoice_payment**
> PayInvoiceResponse post_invoice_payment(pay_invoice_request)

Pay an outstanding invoice

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.pay_invoice_request import PayInvoiceRequest
from checkbook.models.pay_invoice_response import PayInvoiceResponse
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
    api_instance = checkbook.Invoice(api_client)
    pay_invoice_request = {
        "account": "string",
        "amount": 0.01,
        "id": "string",
    }  # PayInvoiceRequest |

    try:
        # Pay an invoice
        api_response = api_instance.post_invoice_payment(pay_invoice_request)
        print("The response of Invoice->post_invoice_payment:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Invoice->post_invoice_payment: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **pay_invoice_request** | **PayInvoiceRequest**|  | 

### Return type

**PayInvoiceResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | PayInvoiceResponse |  -  |
**201** | PayInvoiceResponse |  -  |
**0** | Error |  -  |


