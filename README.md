# Checkbook Python Client
<!-- BEGIN: intro -->
The Checkbook API enables businesses to programmatically send and receive payments using digital checks and other payment methods. With Checkbook, you can automate payment workflows, disburse funds instantly, and manage transactions securely—all without the delays and costs of traditional paper checks.
<!-- END: intro -->


<!-- BEGIN: install -->
## Installation & Usage

### Requirements 

Python 3.9+

### pip install

If the python package is hosted on a repository, you can install directly using:

```sh
pip install checkbook
```

Then import the package:
```python
import checkbook
```

### Obtaining Your API Keys


- First, log in to your account. Access your Checkbook dashboard via our website app.checkbook.io

- Second, navigate to the developer settings. The developer settings  page can be found under the Settings -> Developer menu

- Third, generate the API keys. Each Checkbook account can have multiple API keys, and each API key can have its own expiration date and name for easier management. A given API key will have two parts: a public key and a secret key.

Publishable Key (Public Key): This is an identifier associated with each key and may be included in emails or support tickets sent to the Checkbook team.

Secret Key (Private Key): This key is private and should never be exposed in client-side code or shared publicly. Treat it like a password.

Webhook Key: This key is used for verifying webhook signatures and ensuring the webhook originated from Checkbook. It can only be viewed after generating an API key.

Please securely save your keys immediately after generation, as we do not provide a way to retrieve your secret key after it has been created. Should you lose your keys, you can always generate a new one.
<!-- END: install -->


## Environment
<!-- BEGIN: environment -->

Checkbook supports three environments: demo, sandbox, and production.

Each of these environments can be accessed using their respective url: demo.checkbook.io, api.sandbox.checkbook.io, and api.checkbook.io

- The demo environment only returns fixed responses, it cannot be used to return any custom requests and only has one set of usable API keys which are public. The demo environment is intended for mimicking production or sandbox responses but does not move real money.

- The sandbox environment is used for early development and integration testing. It allows developers to experiment with the API, validate request/response behavior, and build workflows without creating real payments or moving funds. Data in sandbox is isolated and non-production.

- The production environment is used for live applications and real payment processing. All API calls in this environment result in actual transactions and should only be used once your integration has been fully tested and approved.
<!-- END: environment -->


## Authentication
<!-- BEGIN: auth -->

The Checkbook API authenticates requests with an API key passed in the `Authorization` header as `{public_key}:{secret_key}`. The Python SDK accepts this via the `api_key` parameter on `Configuration`, keyed by the security scheme name `token`:

```python
configuration = checkbook.Configuration(
    api_key={"token": "{public_key}:{secret_key}"},
)
```

See [Obtaining Your API Keys](#obtaining-your-api-keys) for how to generate these values.
<!-- END: auth -->


## Getting Started
<!-- BEGIN: quickstart -->

Please follow the [installation procedure](#installation--usage) and then run the following:

```python
import checkbook
from pprint import pprint

from checkbook.api.bank import Bank
from checkbook.api.payment import Payment

# Defining the host is optional and defaults to https://demo.checkbook.io
# See configuration.py for a list of all supported configuration parameters.
configuration = checkbook.Configuration(
    host="https://api.sandbox.checkbook.io",
    api_key={
        "token": "{PUBLIC_KEY_HERE}:{SECRET_KEY_HERE}"
    },
)

# Enter a context with an instance of the API client
with checkbook.ApiClient(configuration) as api_client:
    api_instance = Bank(api_client)
    create_bank_request = {
        "account": "428100001",
        "name": "Checking account",
        "routing": "021000021",
        "type": "CHECKING",
    }  # CreateBankRequest |

    try:
        # Add bank account
        api_response = api_instance.post_bank(create_bank_request)
        pprint(api_response)
        bank_id = api_response.id
        print("Bank Id:", bank_id)

        # Release Microdeposits
        api_instance = Bank(api_client)
        bank_release_request = {"account": bank_id}  # BankReleaseRequest |
        api_instance.post_bank_release(bank_release_request)
        print("Released micro deposits!")

        # Verify Microdeposits - sandbox amounts are always 0.07 and 0.15
        bank_verify_request = {
            "account": bank_id,
            "amount_1": 0.07,
            "amount_2": 0.15,
        }  # BankVerifyRequest |
        api_instance.post_bank_verify(bank_verify_request)
        print("Bank account successfully verified!")

        # Send a payment
        recipient = checkbook.models.CreateDigitalCheckRequestRecipient(
            "dwight@example.com"
        )
        api_instance = Payment(api_client)
        create_digital_check_request = {
            "account": bank_id,
            "name": "Dwight Schrute",
            "amount": 100.0,
            "recipient": recipient,
            "deposit_options": ["BANK"],
        }  # CreateDigitalCheckRequest |

        api_response = api_instance.post_check_digital(create_digital_check_request)
        print("The response of Payment->post_check_digital:\n")
        pprint(api_response)

    except Exception as e:
        print("Exception when running demo script: %s\n" % e)
```
<!-- END: quickstart -->


## API Endpoints
<!-- BEGIN: api-endpoints -->

### Approval

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **delete_approval_check** | **DELETE** /v3/approval/{approval_id} | Remove payment approval |
| **get_approval_attachment** | **GET** /v3/approval/{approval_id}/attachment | Get attachment for payment approval |
| **get_approval_check** | **GET** /v3/approval/{approval_id} | Get payment approval |
| **get_approval_checks** | **GET** /v3/approval | Get approval payments |
| **post_approval_digital** | **POST** /v3/approval/digital | Create approval digital payment |
| **post_approval_multi** | **POST** /v3/approval/multi | Create multi-party payment approval |
| **post_approval_physical** | **POST** /v3/approval/physical | Create physical check approval |
| **post_approval_release** | **POST** /v3/approval/release | Approve payment |
| **put_approval_check** | **PUT** /v3/approval/{approval_id} | Update payment approval |

### Bank

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **delete_bank** | **DELETE** /v3/account/bank/{bank_id} | Remove bank account |
| **get_bank_institutions** | **GET** /v3/account/bank/institutions | Get institutions |
| **get_banks** | **GET** /v3/account/bank | Get bank accounts |
| **post_bank** | **POST** /v3/account/bank | Add bank account |
| **post_bank_iav** | **POST** /v3/account/bank/iav | Add bank account with IAV |
| **post_bank_plaid** | **POST** /v3/account/bank/iav/plaid | Retrieve bank account with Plaid |
| **post_bank_release** | **POST** /v3/account/bank/release | Release micro-deposits |
| **post_bank_verify** | **POST** /v3/account/bank/verify | Verify micro-deposits |
| **put_bank** | **PUT** /v3/account/bank/{bank_id} | Update bank account |

### Card

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **delete_card** | **DELETE** /v3/account/card/{card_id} | Remove card |
| **get_cards** | **GET** /v3/account/card | Get cards |
| **post_card** | **POST** /v3/account/card | Add card |
| **put_card** | **PUT** /v3/account/card/{card_id} | Update card |

### Checkbook

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **delete_checkbook** | **DELETE** /v3/checkbook/{checkbook_id} | Cancel a checkbook |
| **get_checkbook** | **GET** /v3/checkbook/{checkbook_id} | Get checkbook |
| **get_checkbook_tracking** | **GET** /v3/checkbook/{checkbook_id}/tracking | Get tracking details on checkbooks |
| **get_checkbooks** | **GET** /v3/checkbook | Get checkbooks |
| **order_checkbook** | **POST** /v3/checkbook | Order a checkbook |

### Directory

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **create_directory** | **POST** /v3/directory | Create a directory entry |
| **create_directory_bank** | **POST** /v3/directory/{directory_id}/account/bank | Add a bank account to a directory entry |
| **create_directory_card** | **POST** /v3/directory/{directory_id}/account/card | Add a credit/debit card to a directory entry |
| **delete_directory** | **DELETE** /v3/directory/{directory_id} | Remove a directory entry |
| **delete_directory_account** | **DELETE** /v3/directory/{directory_id}/account/{account_id} | Remove a payment account from a directory entry |
| **get_directory** | **GET** /v3/directory | Get directory entries |
| **update_directory** | **PUT** /v3/directory/{directory_id} | Update a directory entry |

### Interac

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **add_interac** | **POST** /v3/account/interac | Create Interac account |
| **get_interac** | **GET** /v3/account/interac | Get Interac accounts |
| **put_interac** | **PUT** /v3/account/interac/{interac_id} | Update Interac account |
| **remove_interac** | **DELETE** /v3/account/interac/{interac_id} | Remove Interac account |

### Invoice

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **delete_invoice** | **DELETE** /v3/invoice/{invoice_id} | Void an invoice |
| **get_invoice** | **GET** /v3/invoice/{invoice_id} | Get invoice |
| **get_invoice_attachment** | **GET** /v3/invoice/{invoice_id}/attachment | Get attachment for an invoice |
| **get_invoices** | **GET** /v3/invoice | Get sent/received invoices |
| **post_invoice** | **POST** /v3/invoice | Create an invoice |
| **post_invoice_payment** | **POST** /v3/invoice/payment | Pay an invoice |

### Mailbox

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **create_mailbox** | **POST** /v3/mailbox | Create a mailbox |
| **get_mailbox** | **GET** /v3/mailbox/{mailbox_id} | Get mailbox info |
| **get_mailbox_item** | **GET** /v3/mailbox/{mailbox_id}/mail/{item_id} | Get mailbox item |
| **get_mailbox_item_attachment** | **GET** /v3/mailbox/{mailbox_id}/mail/{item_id}/attachment | Get attachment for a mail piece |
| **query_mailbox** | **GET** /v3/mailbox | Get mailboxes |
| **query_mailbox_item** | **GET** /v3/mailbox/{mailbox_id}/mail | Get mailbox info |

### Payment

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **delete_check** | **DELETE** /v3/check/{check_id} | Void a payment |
| **get_check** | **GET** /v3/check/{check_id} | Get payment |
| **get_check_attachment** | **GET** /v3/check/{check_id}/attachment | Get attachment for a payment |
| **get_check_deposit** | **GET** /v3/check/{check_id}/deposit | Get deposit details |
| **get_check_fail** | **GET** /v3/check/{check_id}/fail | Get details on failed payment |
| **get_check_tracking** | **GET** /v3/check/{check_id}/tracking | Get tracking details on mailed check |
| **get_check_verification** | **GET** /v3/check/{check_id}/verification | Get verification code |
| **get_checks** | **GET** /v3/check | Get sent/received payments |
| **post_check_deposit** | **POST** /v3/check/deposit/{check_id} | Deposit a payment |
| **post_check_digital** | **POST** /v3/check/digital | Create a digital payment |
| **post_check_endorse** | **POST** /v3/check/endorse/{check_id} | Endorse a multi-party payment |
| **post_check_multi** | **POST** /v3/check/multi | Create a multi-party payment |
| **post_check_notify** | **POST** /v3/check/notify/{check_id} | Resend payment notification |
| **post_check_physical** | **POST** /v3/check/physical | Create a physical check |
| **post_check_preview** | **POST** /v3/check/preview | Preview payment |
| **post_check_print** | **POST** /v3/check/print/{check_id} | Print a payment |
| **post_check_webhook** | **PUT** /v3/check/webhook/{check_id} | Update a sandbox payment status |

### Paypal

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **add_paypal** | **POST** /v3/account/paypal | Create PayPal account |
| **get_paypal** | **GET** /v3/account/paypal | Get PayPal accounts |
| **put_paypal** | **PUT** /v3/account/paypal/{paypal_id} | Update PayPal account |
| **remove_paypal** | **DELETE** /v3/account/paypal/{paypal_id} | Remove PayPal account |

### Subscription

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **delete_subscription** | **DELETE** /v3/subscription/{subscription_id} | Remove subscription |
| **get_subscription** | **GET** /v3/subscription/{subscription_id} | Get subscription |
| **get_subscriptions** | **GET** /v3/subscription | Get subscriptions |
| **post_subscription_check** | **POST** /v3/subscription/check | Create payment subscription |
| **post_subscription_invoice** | **POST** /v3/subscription/invoice | Create invoice subscription |
| **put_subscription** | **PUT** /v3/subscription/{subscription_id} | Update subscription |

### User

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **delete_api_key** | **DELETE** /v3/user/api_key/{key_id} | Delete API key for user |
| **delete_user** | **DELETE** /v3/user/{id} | Remove marketplace user |
| **get_api_keys** | **GET** /v3/user/api_key | Get API keys for user |
| **get_user** | **GET** /v3/user | Get user details |
| **get_users** | **GET** /v3/user/list | Get marketplace users |
| **new_api_key** | **POST** /v3/user/api_key | Generate new API Key for user |
| **post_user** | **POST** /v3/user | Create user |
| **post_user_signature** | **POST** /v3/user/signature | Add signature for user |
| **put_user** | **PUT** /v3/user | Update user |
| **put_user_webhook** | **PUT** /v3/user/webhook | Update a sandbox user status |

### Vcc

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **delete_vcc** | **DELETE** /v3/account/vcc/{vcc_id} | Remove virtual card |
| **get_vcc_transaction** | **GET** /v3/account/vcc/{vcc_id}/transaction | Get virtual card transactions |
| **get_vcc_transaction_by_id** | **GET** /v3/account/vcc/{vcc_id}/transaction/{transaction_id} | Get virtual card transaction by ID |
| **get_vccs** | **GET** /v3/account/vcc | Get virtual cards |
| **post_vcc** | **POST** /v3/account/vcc | Create virtual card |
| **put_vcc** | **PUT** /v3/account/vcc/{vcc_id} | Update virtual card |

### Venmo

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **add_venmo** | **POST** /v3/account/venmo | Create Venmo account |
| **get_venmo** | **GET** /v3/account/venmo | Get Venmo accounts |
| **put_venmo** | **PUT** /v3/account/venmo/{venmo_id} | Update Venmo account |
| **remove_venmo** | **DELETE** /v3/account/venmo/{venmo_id} | Remove Venmo account |

### Wallet

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **add_wallet** | **POST** /v3/account/wallet | Create wallet |
| **delete_wallet** | **DELETE** /v3/account/wallet/{wallet_id} | Delete wallet |
| **get_wallet** | **GET** /v3/account/wallet | Get wallets |
| **update_wallet** | **PUT** /v3/account/wallet/{wallet_id} | Update wallet |

### Wire

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| **add_wire** | **POST** /v3/account/wire | Create wire account |
| **get_wire** | **GET** /v3/account/wire | Get wire accounts |
| **put_wire** | **PUT** /v3/account/wire/{account_id} | Update Wire account |
| **remove_wire** | **DELETE** /v3/account/wire/{wire_id} | Remove wire account |
<!-- END: api-endpoints -->


