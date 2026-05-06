# Directory 
Save and manage recipients you pay or bill regularly, stored with name, email, address, and any linked bank accounts or cards. Acts as a reusable address book for future payments and invoices.


Method | HTTP request | Description
------------- | ------------- | -------------
[**create_directory**](Directory.md#create_directory) | **POST** /v3/directory | Create a directory entry
[**create_directory_bank**](Directory.md#create_directory_bank) | **POST** /v3/directory/{directory_id}/account/bank | Add a bank account to a directory entry
[**create_directory_card**](Directory.md#create_directory_card) | **POST** /v3/directory/{directory_id}/account/card | Add a credit/debit card to a directory entry
[**delete_directory**](Directory.md#delete_directory) | **DELETE** /v3/directory/{directory_id} | Remove a directory entry
[**delete_directory_account**](Directory.md#delete_directory_account) | **DELETE** /v3/directory/{directory_id}/account/{account_id} | Remove a payment account from a directory entry
[**get_directory**](Directory.md#get_directory) | **GET** /v3/directory | Get directory entries
[**update_directory**](Directory.md#update_directory) | **PUT** /v3/directory/{directory_id} | Update a directory entry


## **create_directory**
> CreateDirectoryResponse create_directory(create_directory_request)

Create a new directory item

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_directory_request import CreateDirectoryRequest
from checkbook.models.create_directory_response import CreateDirectoryResponse
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
    api_instance = checkbook.Directory(api_client)
    create_directory_request = {
        "address": null,
        "email": "string",
        "name": "string",
    }  # CreateDirectoryRequest |

    try:
        # Create a directory entry
        api_response = api_instance.create_directory(create_directory_request)
        print("The response of Directory->create_directory:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Directory->create_directory: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_directory_request** | **CreateDirectoryRequest**|  | 

### Return type

**CreateDirectoryResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | CreateDirectoryResponse |  -  |
**0** | Error |  -  |


## **create_directory_bank**
> CreateDirectoryBankResponse create_directory_bank(directory_id, create_directory_bank_request)

Create a new directory bank account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_directory_bank_request import CreateDirectoryBankRequest
from checkbook.models.create_directory_bank_response import CreateDirectoryBankResponse
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
    api_instance = checkbook.Directory(api_client)
    directory_id = "directory_id_example"  # str |
    create_directory_bank_request = {
        "account": "string",
        "name": "string",
        "routing": "string",
        "type": "CHECKING",
    }  # CreateDirectoryBankRequest |

    try:
        # Add a bank account to a directory entry
        api_response = api_instance.create_directory_bank(
            directory_id, create_directory_bank_request
        )
        print("The response of Directory->create_directory_bank:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Directory->create_directory_bank: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **directory_id** | **str**|  | 
 **create_directory_bank_request** | **CreateDirectoryBankRequest**|  | 

### Return type

**CreateDirectoryBankResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | CreateDirectoryBankResponse |  -  |
**0** | Error |  -  |


## **create_directory_card**
> CreateDirectoryCardResponse create_directory_card(directory_id, create_directory_card_request)

Create a new directory card account

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_directory_card_request import CreateDirectoryCardRequest
from checkbook.models.create_directory_card_response import CreateDirectoryCardResponse
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
    api_instance = checkbook.Directory(api_client)
    directory_id = "directory_id_example"  # str |
    create_directory_card_request = {
        "card_number": "string",
        "expiration_date": "string",
        "name": "string",
    }  # CreateDirectoryCardRequest |

    try:
        # Add a credit/debit card to a directory entry
        api_response = api_instance.create_directory_card(
            directory_id, create_directory_card_request
        )
        print("The response of Directory->create_directory_card:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Directory->create_directory_card: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **directory_id** | **str**|  | 
 **create_directory_card_request** | **CreateDirectoryCardRequest**|  | 

### Return type

**CreateDirectoryCardResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | CreateDirectoryCardResponse |  -  |
**0** | Error |  -  |


## **delete_directory**
> delete_directory(directory_id)

Remove the directory item

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
    api_instance = checkbook.Directory(api_client)
    directory_id = "directory_id_example"  # str |

    try:
        # Remove a directory entry
        api_instance.delete_directory(directory_id)
    except Exception as e:
        print("Exception when calling Directory->delete_directory: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **directory_id** | **str**|  | 

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


## **delete_directory_account**
> delete_directory_account(directory_id, account_id)

Remove a directory account

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
    api_instance = checkbook.Directory(api_client)
    directory_id = "directory_id_example"  # str |
    account_id = "account_id_example"  # str |

    try:
        # Remove a payment account from a directory entry
        api_instance.delete_directory_account(directory_id, account_id)
    except Exception as e:
        print("Exception when calling Directory->delete_directory_account: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **directory_id** | **str**|  | 
 **account_id** | **str**|  | 

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


## **get_directory**
> GetDirectoriesResponse get_directory(page=page, per_page=per_page, q=q)

Return the directory entry

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_directories_response import GetDirectoriesResponse
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
    api_instance = checkbook.Directory(api_client)
    page = 1  # int | Page number (optional) (default to 1)
    per_page = 50  # int | Items per page (optional) (default to 50)
    q = "q_example"  # str | Query (optional)

    try:
        # Get directory entries
        api_response = api_instance.get_directory(page=page, per_page=per_page, q=q)
        print("The response of Directory->get_directory:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Directory->get_directory: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| Page number | [optional] [default to 1]
 **per_page** | **int**| Items per page | [optional] [default to 50]
 **q** | **str**| Query | [optional] 

### Return type

**GetDirectoriesResponse**

### Authorization

token

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetDirectoriesResponse |  -  |
**0** | Error |  -  |


## **update_directory**
> update_directory(directory_id, update_directory_request)

Update a directory item

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_directory_request import UpdateDirectoryRequest
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
    api_instance = checkbook.Directory(api_client)
    directory_id = "directory_id_example"  # str |
    update_directory_request = {
        "address": null,
        "email": "string",
        "name": "string",
    }  # UpdateDirectoryRequest |

    try:
        # Update a directory entry
        api_instance.update_directory(directory_id, update_directory_request)
    except Exception as e:
        print("Exception when calling Directory->update_directory: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **directory_id** | **str**|  | 
 **update_directory_request** | **UpdateDirectoryRequest**|  | 

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


