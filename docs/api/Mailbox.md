# Mailbox 



Method | HTTP request | Description
------------- | ------------- | -------------
[**create_mailbox**](Mailbox.md#create_mailbox) | **POST** /v3/mailbox | Create a mailbox
[**get_mailbox**](Mailbox.md#get_mailbox) | **GET** /v3/mailbox/{mailbox_id} | Get mailbox info
[**get_mailbox_item**](Mailbox.md#get_mailbox_item) | **GET** /v3/mailbox/{mailbox_id}/mail/{item_id} | Get mailbox item
[**get_mailbox_item_attachment**](Mailbox.md#get_mailbox_item_attachment) | **GET** /v3/mailbox/{mailbox_id}/mail/{item_id}/attachment | Get attachment for a mail piece
[**query_mailbox**](Mailbox.md#query_mailbox) | **GET** /v3/mailbox | Get mailboxes
[**query_mailbox_item**](Mailbox.md#query_mailbox_item) | **GET** /v3/mailbox/{mailbox_id}/mail | Get mailbox info


## **create_mailbox**
> CreateMailboxResponse create_mailbox()

Create a new mailbox

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_mailbox_response import CreateMailboxResponse
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
    api_instance = checkbook.Mailbox(api_client)

    try:
        # Create a mailbox
        api_response = api_instance.create_mailbox()
        print("The response of Mailbox->create_mailbox:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Mailbox->create_mailbox: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**CreateMailboxResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | CreateMailboxResponse |  -  |
**0** | Error |  -  |


## **get_mailbox**
> CreateMailboxResponse get_mailbox(mailbox_id)

Get mailbox details

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_mailbox_response import CreateMailboxResponse
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
    api_instance = checkbook.Mailbox(api_client)
    mailbox_id = "mailbox_id_example"  # str |

    try:
        # Get mailbox info
        api_response = api_instance.get_mailbox(mailbox_id)
        print("The response of Mailbox->get_mailbox:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Mailbox->get_mailbox: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **mailbox_id** | **str**|  | 

### Return type

**CreateMailboxResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | CreateMailboxResponse |  -  |
**0** | Error |  -  |


## **get_mailbox_item**
> MailResponse get_mailbox_item(mailbox_id, item_id)

Get mailbox item

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.mail_response import MailResponse
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
    api_instance = checkbook.Mailbox(api_client)
    mailbox_id = "mailbox_id_example"  # str |
    item_id = "item_id_example"  # str |

    try:
        # Get mailbox item
        api_response = api_instance.get_mailbox_item(mailbox_id, item_id)
        print("The response of Mailbox->get_mailbox_item:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Mailbox->get_mailbox_item: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **mailbox_id** | **str**|  | 
 **item_id** | **str**|  | 

### Return type

**MailResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | MailResponse |  -  |
**0** | Error |  -  |


## **get_mailbox_item_attachment**
> Error get_mailbox_item_attachment(mailbox_id, item_id)

Get mailbox item

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.error import Error
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
    api_instance = checkbook.Mailbox(api_client)
    mailbox_id = "mailbox_id_example"  # str |
    item_id = "item_id_example"  # str |

    try:
        # Get attachment for a mail piece
        api_response = api_instance.get_mailbox_item_attachment(mailbox_id, item_id)
        print("The response of Mailbox->get_mailbox_item_attachment:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Mailbox->get_mailbox_item_attachment: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **mailbox_id** | **str**|  | 
 **item_id** | **str**|  | 

### Return type

**Error**

### Authorization

token

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**0** | Error |  -  |


## **query_mailbox**
> GetMailboxesResponse query_mailbox(page=page, per_page=per_page)

Return the mailboxes for the current user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_mailboxes_response import GetMailboxesResponse
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
    api_instance = checkbook.Mailbox(api_client)
    page = 1  # int | Page number (optional) (default to 1)
    per_page = 50  # int | Items per page (optional) (default to 50)

    try:
        # Get mailboxes
        api_response = api_instance.query_mailbox(page=page, per_page=per_page)
        print("The response of Mailbox->query_mailbox:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Mailbox->query_mailbox: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| Page number | [optional] [default to 1]
 **per_page** | **int**| Items per page | [optional] [default to 50]

### Return type

**GetMailboxesResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetMailboxesResponse |  -  |
**0** | Error |  -  |


## **query_mailbox_item**
> GetMailResponse query_mailbox_item(mailbox_id, end_date=end_date, page=page, per_page=per_page, q=q, start_date=start_date)

Get mailbox items

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_mail_response import GetMailResponse
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
    api_instance = checkbook.Mailbox(api_client)
    mailbox_id = "mailbox_id_example"  # str |
    end_date = "2013-10-20"  # date | End date (optional)
    page = 1  # int | Page number (optional) (default to 1)
    per_page = 50  # int | Items per page (optional) (default to 50)
    q = "payment"  # str | Query (optional)
    start_date = "2013-10-20"  # date | Start date (optional)

    try:
        # Get mailbox info
        api_response = api_instance.query_mailbox_item(
            mailbox_id,
            end_date=end_date,
            page=page,
            per_page=per_page,
            q=q,
            start_date=start_date,
        )
        print("The response of Mailbox->query_mailbox_item:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Mailbox->query_mailbox_item: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **mailbox_id** | **str**|  | 
 **end_date** | **date**| End date | [optional] 
 **page** | **int**| Page number | [optional] [default to 1]
 **per_page** | **int**| Items per page | [optional] [default to 50]
 **q** | **str**| Query | [optional] 
 **start_date** | **date**| Start date | [optional] 

### Return type

**GetMailResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetMailResponse |  -  |
**0** | Error |  -  |


