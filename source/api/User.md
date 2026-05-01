# User 
Onboard and manage users in your marketplace. Use this resource to manage a user's API keys, add KYC/KYB information, check user statuses, and customize their profile. Users do not need to sign in to Checkbook or maintain their own account to transact.


Method | HTTP request | Description
------------- | ------------- | -------------
[**delete_api_key**](User.md#delete_api_key) | **DELETE** /v3/user/api_key/{key_id} | Delete API key for user
[**delete_user**](User.md#delete_user) | **DELETE** /v3/user/{id} | Remove marketplace user
[**get_api_keys**](User.md#get_api_keys) | **GET** /v3/user/api_key | Get API keys for user
[**get_user**](User.md#get_user) | **GET** /v3/user | Get user details
[**get_users**](User.md#get_users) | **GET** /v3/user/list | Get marketplace users
[**new_api_key**](User.md#new_api_key) | **POST** /v3/user/api_key | Generate new API Key for user
[**post_user**](User.md#post_user) | **POST** /v3/user | Create user
[**post_user_signature**](User.md#post_user_signature) | **POST** /v3/user/signature | Add signature for user
[**put_user**](User.md#put_user) | **PUT** /v3/user | Update user
[**put_user_webhook**](User.md#put_user_webhook) | **PUT** /v3/user/webhook | Update a sandbox user status


# **delete_api_key**
> delete_api_key(key_id)

Delete API key for user

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
    api_instance = checkbook.User(api_client)
    key_id = "key_id_example"  # str |

    try:
        # Delete API key for user
        api_instance.delete_api_key(key_id)
    except Exception as e:
        print("Exception when calling User->delete_api_key: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **key_id** | **str**|  | 

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


# **delete_user**
> delete_user(id)

Delete a marketplace user. 
> [!NOTE]
> **Tip**  
> The id that gets passed in needs to be the Checkbook system generated `id`, not the `user_id`. 
> Users with active transactions may not be deleted.

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
    api_instance = checkbook.User(api_client)
    id = "id_example"  # str |

    try:
        # Remove marketplace user
        api_instance.delete_user(id)
    except Exception as e:
        print("Exception when calling User->delete_user: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

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


# **get_api_keys**
> APIKeyListResponse get_api_keys()

Return the API keys for the user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.api_key_list_response import APIKeyListResponse
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
    api_instance = checkbook.User(api_client)

    try:
        # Get API keys for user
        api_response = api_instance.get_api_keys()
        print("The response of User->get_api_keys:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling User->get_api_keys: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**APIKeyListResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Response fields for api key list |  -  |
**0** | Error |  -  |


# **get_user**
> GetUserResponse get_user()

Get user information

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_user_response import GetUserResponse
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
    api_instance = checkbook.User(api_client)

    try:
        # Get user details
        api_response = api_instance.get_user()
        print("The response of User->get_user:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling User->get_user: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**GetUserResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Response fields for user retrieval |  -  |
**0** | Error |  -  |


# **get_users**
> UserQueryResponse get_users(page=page, per_page=per_page, q=q, sort=sort)

Return the marketplace users

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.user_query_response import UserQueryResponse
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
    api_instance = checkbook.User(api_client)
    page = 1  # int | Page number (optional) (default to 1)
    per_page = 50  # int | Items per page (optional) (default to 50)
    q = "q_example"  # str | Query (optional)
    sort = "sort_example"  # str | Sort (optional)

    try:
        # Get marketplace users
        api_response = api_instance.get_users(
            page=page, per_page=per_page, q=q, sort=sort
        )
        print("The response of User->get_users:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling User->get_users: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| Page number | [optional] [default to 1]
 **per_page** | **int**| Items per page | [optional] [default to 50]
 **q** | **str**| Query | [optional] 
 **sort** | **str**| Sort | [optional] 

### Return type

**UserQueryResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Response fields for user query |  -  |
**0** | Error |  -  |


# **new_api_key**
> NewApiKeyResponse new_api_key(new_api_key_request)

Generate new API keys for the user

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.new_api_key_request import NewApiKeyRequest
from checkbook.models.new_api_key_response import NewApiKeyResponse
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
    api_instance = checkbook.User(api_client)
    new_api_key_request = {"expiration_date": null, "name": null}  # NewApiKeyRequest |

    try:
        # Generate new API Key for user
        api_response = api_instance.new_api_key(new_api_key_request)
        print("The response of User->new_api_key:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling User->new_api_key: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **new_api_key_request** | **NewApiKeyRequest**|  | 

### Return type

**NewApiKeyResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | NewApiKeyResponse |  -  |
**0** | Error |  -  |


# **post_user**
> CreateUserResponse post_user(create_user_request)

Create a new marketplace user.  
> [!NOTE]
> **Common Errors**
>
> - **`403: FORBIDDEN`**: Please ensure you are using the Marketplace Owner's keys. If the `403` error persists, it may indicate that marketplace is not enabled for your account or you do not have an active billing bank account onboarded. Contact support@checkbook.io for more details.

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_user_request import CreateUserRequest
from checkbook.models.create_user_response import CreateUserResponse
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
    api_instance = checkbook.User(api_client)
    create_user_request = {"name": "string", "user_id": "string"}  # CreateUserRequest |

    try:
        # Create user
        api_response = api_instance.post_user(create_user_request)
        print("The response of User->post_user:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling User->post_user: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_user_request** | **CreateUserRequest**|  | 

### Return type

**CreateUserResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | Response fields for user creation |  -  |
**0** | Error |  -  |


# **post_user_signature**
> post_user_signature(signature_request)

Add signature

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.signature_request import SignatureRequest
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
    api_instance = checkbook.User(api_client)
    signature_request = {"signature": "string"}  # SignatureRequest |

    try:
        # Add signature for user
        api_instance.post_user_signature(signature_request)
    except Exception as e:
        print("Exception when calling User->post_user_signature: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **signature_request** | **SignatureRequest**|  | 

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


# **put_user**
> put_user(update_user_request)

Update existing user information.  
> [!NOTE]
> **Note**  
> This endpoint is used for updating a user's KYB/KYC information. Checkbook validates this information asynchronously.

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_user_request import UpdateUserRequest
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
    api_instance = checkbook.User(api_client)
    update_user_request = {
        "bank": null,
        "brand": null,
        "developer": null,
        "merchant": null,
        "payment": null,
        "user": null,
    }  # UpdateUserRequest |

    try:
        # Update user
        api_instance.put_user(update_user_request)
    except Exception as e:
        print("Exception when calling User->put_user: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **update_user_request** | **UpdateUserRequest**|  | 

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


# **put_user_webhook**
> put_user_webhook(trigger_user_webhook_request)

Update a user's status in the sandbox environment.

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.trigger_user_webhook_request import TriggerUserWebhookRequest
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
    api_instance = checkbook.User(api_client)
    trigger_user_webhook_request = {
        "status": "UNVERIFIED"
    }  # TriggerUserWebhookRequest |

    try:
        # Update a sandbox user status
        api_instance.put_user_webhook(trigger_user_webhook_request)
    except Exception as e:
        print("Exception when calling User->put_user_webhook: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **trigger_user_webhook_request** | **TriggerUserWebhookRequest**|  | 

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


