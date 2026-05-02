# Card 
Link and manage debit cards for receiving push-to-card (OCT) payouts.


Method | HTTP request | Description
------------- | ------------- | -------------
[**delete_card**](Card.md#delete_card) | **DELETE** /v3/account/card/{card_id} | Remove card
[**get_cards**](Card.md#get_cards) | **GET** /v3/account/card | Get cards
[**post_card**](Card.md#post_card) | **POST** /v3/account/card | Add card
[**put_card**](Card.md#put_card) | **PUT** /v3/account/card/{card_id} | Update card


## **delete_card**
> delete_card(card_id)

Remove the specified card

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
    api_instance = checkbook.Card(api_client)
    card_id = "card_id_example"  # str |

    try:
        # Remove card
        api_instance.delete_card(card_id)
    except Exception as e:
        print("Exception when calling Card->delete_card: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **card_id** | **str**|  | 

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


## **get_cards**
> GetCardsResponse get_cards()

Return the cards

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.get_cards_response import GetCardsResponse
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
    api_instance = checkbook.Card(api_client)

    try:
        # Get cards
        api_response = api_instance.get_cards()
        print("The response of Card->get_cards:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Card->get_cards: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**GetCardsResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | GetCardsResponse |  -  |
**0** | Error |  -  |


## **post_card**
> CreateCardResponse post_card(create_card_request)

Add a new card

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.create_card_request import CreateCardRequest
from checkbook.models.create_card_response import CreateCardResponse
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
    api_instance = checkbook.Card(api_client)
    create_card_request = {
        "address": null,
        "card_number": "string",
        "cvv": "string",
        "expiration_date": "string",
    }  # CreateCardRequest |

    try:
        # Add card
        api_response = api_instance.post_card(create_card_request)
        print("The response of Card->post_card:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling Card->post_card: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_card_request** | **CreateCardRequest**|  | 

### Return type

**CreateCardResponse**

### Authorization

[token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | CreateCardResponse |  -  |
**0** | Error |  -  |


## **put_card**
> put_card(card_id, update_card_request)

Update the specified card

### Example

* Api Key Authentication (token):

```python
import checkbook
from checkbook.models.update_card_request import UpdateCardRequest
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
    api_instance = checkbook.Card(api_client)
    card_id = "card_id_example"  # str |
    update_card_request = {"default": true, "name": "Visa card"}  # UpdateCardRequest |

    try:
        # Update card
        api_instance.put_card(card_id, update_card_request)
    except Exception as e:
        print("Exception when calling Card->put_card: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **card_id** | **str**|  | 
 **update_card_request** | **UpdateCardRequest**|  | 

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


