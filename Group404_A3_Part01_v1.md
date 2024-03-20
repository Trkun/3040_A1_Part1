# Crypto Wallet Management API

### API Description
The Crypto Wallet Management API is designed to empower users of 3040Crypto by enabling seamless management of their cryptocurrency wallets. This API allows users to create new wallets, check balances, and view their transaction history with ease.

### Endpoints with Parameters
##### 1. Create Wallet
- Endpoint: /createWallet
- Method: POST
- Description: Allows users to create a new cryptocurrency wallet.
- Parameters: None
- Request Body:
    ```json
    {
      "userId": "string",
      "walletName": "string"
    }
    ```
- Response:
    ```json
    {
      "walletId": "string",
      "message": "Wallet created successfully."
    }
    ```
##### 2. Get Wallet Balance
- Endpoint: /getWalletBalance
- Method: GET
- Description: Retrieves the current balance of the specified wallet.
- Parameters: walletId: The unique identifier of the wallet.
- Response:
    ```json
    {
      "walletId": "string",
      "balance": "number",
      "currency": "string"
    }
    ```
##### 3. Get Transaction History
- Endpoint: /getTransactionHistory
- Method: GET
- Description: Fetches a list of all transactions for a specified wallet.
- Parameters: walletId: The unique identifier of the wallet.
- Response:
    ```json
    {
      "transactions": [
        {
          "transactionId": "string",
          "type": "string",
          "amount": "number",
          "currency": "string",
          "date": "string"
        }
      ]
    }
    ```
### Description of Resources

The primary resources managed by this API are:

- Wallet: Represents a cryptocurrency wallet.
    ```json
    {
      "walletId": "string",
      "userId": "string",
      "walletName": "string",
      "balance": "number",
      "currency": "string"
    }
    ```

- Transaction: Represents a transaction within a wallet.
    ```json
    {
      "transactionId": "string",
      "walletId": "string",
      "type": "string", // "send" or "receive"
      "amount": "number",
      "currency": "string",
      "date": "string"
    }
    ```

### Sample Request with Sample Response

- Request: ```GET /getWalletBalance?walletId=12345```
- Response:
    ```json
    {
      "walletId": "12345",
      "balance": 500,
      "currency": "BTC"
    }
    ```