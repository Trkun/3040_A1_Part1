# Crypto Wallet Management API

Authors: `Arshpreet Buttar, Jay Dodhiawala, Rui Zhang (Group 404)`

## API Description

The Crypto Wallet Management API is designed to empower users of 3040Crypto by enabling seamless management of their cryptocurrency wallets. This API allows users to create new wallets, check balances, and view their transaction history with ease

## Endpoints with Parameters

### 1. Create Wallet

- **Endpoint**: `/createWallet`
- **Method**: `POST`
- **Description**:  `Creates a new cryptocurrency wallet for the user with custom security settings`
- **Parameters**:
  - `userId`: A unique identifier for the user creating the wallet
  - `password`: A unique password for this user
  - `currency`: The primary cryptocurrency type for the wallet
  - `walletName`: The name the user wishes to give to their new wallet
  - `enable2FA`: A boolean value indicating whether two-factor authentication should be enabled for added security

- Example

  - Request: `POST /createWallet`
    ```json
    {
      "userId": "user_12345",
      "password": "rand0m",
      "walletName": "MyCryptoWallet",
      "currency": "BTC",
      "enable2FA": true
    }
    ```
  - Response:

    ```json
    {
      "walletId": 30403040,
      "message": "Wallet created successfully",
      "security": "2FA enabled"
    }
    ```

### 2. Get Wallet Balance

- Endpoint: `/getWalletBalance`
- Method: `GET`
- Description: `Retrieves the balance of the specified wallet in both the primary currency and the equivalent value in a specified fiat currency`
- Parameters:
  - `userId`: The unique identifier of the user
  - `password`: The unique password for this user
  - `walletName`: The name of the wallet user wants balance of
  - `fiatCurrency`: The fiat currency code to convert the crypto balance into

- Example

  - Request: 
    ```
    GET /getWalletBalance?userId=user_12345&password=rand0m&walletName=MyCryptoWallet&fiatCurrency=USD
    ```
  - Response:
    ```json
    {
      "walletId": 30403040,
      "message": "Wallet balance retrieved successfully",
      "security": "2FA enabled",
      "walletBalance": [
        {
          "currency": "USD",
          "balance": 500
        },
        {
          "currency": "BTC",
          "balance": 0.000015
        }
      ]
    }
    ```

### 3. Get Transaction History

- Endpoint: `/getTransactionHistory`
- Method: `GET`
- Description: `Fetches the transaction history for a specified wallet, filtered by transaction type and within a specified date range`
- Parameters:
  - `userId`: The unique identifier of the user
  - `password`: The unique password for this user
  - `walletName`: The name of the wallet user wants transaction history of
  - `transactionType`: The type of transactions to retrieve (send or receive)
  - `startDate`: The start date for the transaction history period
  - `endDate`: The end date for the transaction history period

- Example

  - Request: 
    ```
    GET /getTransactionHistory?userId=user_12345&password=rand0m&walletName=MyCryptoWallet&transactionType=send&startDate=2023-01-01&endDate=2023-03-01
    ```
  - Response:
    ```json
    {
      "walletId": 30403040,
      "message": "Wallet transactions retrieved successfully",
      "security": "2FA enabled",
      "transactions": [
        {
          "transactionId": "tid_225",
          "type": "send",
          "amount": 1.0,
          "currency": "BTC",
          "date": "2023-01-02",
          "recipient": "wallet_3040"
        }
      ]
    }
    ```

## Description of Resources

The primary resources managed by this API are:

- Wallet: Represents a user's cryptocurrency wallet, which can hold multiple types of cryptocurrencies and is secured with two-factor authentication (2FA)

  ```json
  {
    "walletId": "string",
    "userId": "string",
    "password": "string",
    "walletName": "string",
    "balance": "number",
    "currency": "string",
    "enable2FA": "boolean"
  }
  ```

- Transaction: Represents a movement of cryptocurrency amount from or to a wallet. Transactions can be filtered by type and date range for detailed financial tracking.
  ```json
  {
    "transactionId": "string",
    "walletId": "string",
    "transactionType": "string",
    "amount": "number",
    "currency": "string",
    "date": "string",
    "recipient": "string", 
    "sender": "string"
  }
  ```