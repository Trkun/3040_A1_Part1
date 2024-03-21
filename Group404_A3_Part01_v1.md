# Crypto Wallet Management API

## API Description

The Crypto Wallet Management API is designed to empower users of 3040Crypto by enabling seamless management of their cryptocurrency wallets. This API allows users to create new wallets, check balances, and view their transaction history with ease.

## Endpoints with Parameters

#### 1. Create Wallet

- Endpoint: /createWallet
- Method: POST
- Description: Allows users to create a new cryptocurrency wallet.
- Parameters: None
- Request Body:
  ```json
  {
    "name": "string",
    "password": "string",
    "email": "string",
    "userName": "string",
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

#### example

- Request: `POST /createWallet`
  ```json
  Content-Type: application/json
  {
  "name": "Tom Cruse",
  "password": "i_love_tome_cruse",
  "email":"tomcruse@xyz.com",
  "userName": "tommy",
  "walletName": "tom"
  }
  ```
- Response:

  ```json
  {
    "walletId": "30403040",
    "message": "Wallet created successfully."
  }
  ```

#### 2. Get Wallet Balance

- Endpoint: `/getWalletBalance?walletId={wallet_id}`
- Method: GET
- Description: Retrieves the current balance of the specified wallet.
- Parameters: walletId: The unique identifier of the wallet.
- Response:
  ```json
  {
    "walletBalance": [
      {
        "currency": "string",
        "balance": "number"
      }
    ]
  }
  ```

#### example

- Request: `GET /getWalletBalance?walletId=30403040`
- Response:
  ```json
  {
    "walletBalance": [
      {
        "currency": "BTC",
        "balance": 1000
      },
      {
        "currency": "ETH",
        "balance": 500
      },
      {
        "balance": 200,
        "currency": "LTC"
      }
    ]
  }
  ```

#### 3. Get Transaction History

- Endpoint: `/getTransactionHistory?walletId={wallet_id}`
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

#### example

- Request: `GET /getTransactionHistory?walletId=30403040`
- Response:
  ```json
  {
    "transactions": [
      {
        "transactionId": "123",
        "type": "send",
        "amount": 10,
        "currency": "BTC",
        "date": "19-03-2024"
      },
      {
        "transactionId": "456",
        "type": "received",
        "amount": 20,
        "currency": "ETH",
        "date": "18-03-2024"
      }
    ]
  }
  ```

## Description of Resources

The primary resources managed by this API are:

- Wallet: Represents a cryptocurrency wallet.

  ```json
  {
    "name": "string",
    "password": "string",
    "email": "string",
    "userName": "string",
    "walletId": "string",
    "userId": "string",
    "walletName": "string",
    "walletBalance": [
      {
        "currency": "string",
        "balance": "number"
      }
    ]
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
