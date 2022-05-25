# Opensea.js
Forked from ProjectOpenSea/opensea-js#d17ebe1

## Installation
```
$ npm install GeorgiKJoseph/opensea-js#d1d73cca546d10cc956c71fccfd1322c96c5b56b
```

## Buying Items - Get Transaction Data - Gas Adjust 

To generate transaction data & value to buy an item via WyvernExchangeContract, 
first you need to get the sell order from Opensea.
```js
const TOKEN_CONTRACT_ADDRESS = '<< NFT contract address >>'
const TOKEN_ID = 10
const order = await seaport.api.getOrder({ 
  side: OrderSide.Sell,
  asset_contract_address: TOKEN_CONTRACT_ADDRESS
  token_id: TOKEN_ID
})
```

Get transaction data & value.
```js
const ACCOUNT_ADDRESS = "0x..." // The buyer's wallet address, also the taker
const tnxParams = await seaport.getFulfillOrderTxnData({
    order: order,
    accountAddress: ACCOUNT_ADDRESS
})
const data = tnxParams.txnAbiEncode
const value = txnParams.value.toString()
```

## Making Offers - Get http request payload.

Get payload for the bid request.
```js
const TOKEN_CONTRACT_ADDRESS = '<< NFT contract address >>'
const TOKEN_ID = 10
const MAKER_ACCOUNT_ADDRESS = '<< maker account address >>'
const BID_AMOUNT = 0.01 // in ETH
const EXPIRATION_TIME = 1653762600 //epoch

const offer = await seaport.createBuyOrderTxnData({
    asset: {
        tokenId: TOKEN_CONTRACT_ADDRESS,
        tokenAddress: TOKEN_ID
    },
    accountAddress: MAKER_ACCOUNT_ADDRESS,
    startAmount: BID_AMOUNT,
    expirationTime: EXPIRATION_TIME
})
```

> None of the functions from standard opensea-js package have been altered.

## Reference
ProjectOpenSea/opensea-js documentation [here](https://github.com/ProjectOpenSea/opensea-js/blob/master/README.md).
