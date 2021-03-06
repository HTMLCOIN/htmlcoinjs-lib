# althashjs-lib
This is an extend library called althashjs-lib, it supports two networks; althash-mainnet and althash-testnet
It can generate contracts and creating and send transactions
## Installation
``` bash
npm install althashjs-lib
```

## Setup
### Node.js
``` javascript
var althashjs = require('althashjs-lib')
```

## New features
### Network
https://en.bitcoin.it/wiki/List_of_address_prefixes
```
{
    althash: {
        messagePrefix: '\x15Htmlcoin Signed Message:\n',
        bech32: 'hc',
        bip32: {
            public: 0x0488b21e,
            private: 0x0488ade4
        },
        pubKeyHash: 0x29,
        scriptHash: 0x64,
        wif: 0xa9
    },
    althash_testnet: {
        messagePrefix: '\x15Htmlcoin Signed Message:\n',
        bech32: 'th',
        bip32: {
            public: 0x043587cf,
            private: 0x04358394
        },
        pubKeyHash: 0x64,
        scriptHash: 0x6e,
        wif: 0xef
    }
}

```

### Utils
#### Utils.selectTxs
```javascript
/**
 * This is a function for selecting HTML utxos to build transactions
 * the transaction object takes at least 3 fields, value(unit is 1e-8 HTML) , confirmations and isStake
 *
 * @param [transaction] unspentTransactions
 * @param Number amount(unit: HTML)
 * @param Number fee(unit: HTML)
 * @returns [transaction]
 */
function selectTxs(unspentTransactions, amount, fee)
```
#### Utils.buildPubKeyHashTransaction
```javascript
/**
 * This is a helper function to build a pubkeyhash transaction
 * the transaction object takes at least 5 fields, value(unit is 1e-8 HTML), confirmations, isStake, hash and pos
 *
 * @param bitcoinjs-lib.KeyPair keyPair
 * @param String to
 * @param Number amount(unit: HTML)
 * @param Number fee(unit: HTML)
 * @param [transaction] utxoList
 * @returns String the built tx
 */
function buildPubKeyHashTransaction(keyPair, to, amount, fee, utxoList)
```
#### Utils.buildCreateContractTransaction
```javascript
/**
 * This is a helper function to build a create-contract transaction
 * the transaction object takes at least 5 fields, value(unit is 1e-8 HTML), confirmations, isStake, hash and pos
 *
 * @param bitcoinjs-lib.KeyPair keyPair
 * @param String code The contract byte code
 * @param Number gasLimit
 * @param Number gasPrice(unit: 1e-8 HTML/gas)
 * @param Number fee(unit: HTML)
 * @param [transaction] utxoList
 * @returns String the built tx
 */
function buildCreateContractTransaction(keyPair, code, gasLimit, gasPrice, fee, utxoList)
```
#### Utils.buildSendToContractTransaction
```javascript
/**
 * This is a helper function to build a send-to-contract transaction
 * the transaction object takes at least 5 fields, value(unit is 1e-8 HTML), confirmations, isStake, hash and pos
 *
 * @param bitcoinjs-lib.KeyPair keyPair
 * @param String contractAddress The contract address
 * @param String encodedData The encoded abi data
 * @param Number gasLimit
 * @param Number gasPrice(unit: 1e-8 HTML/gas)
 * @param Number fee(unit: HTML)
 * @param [transaction] utxoList
 * @returns String the built tx
 */
function buildSendToContractTransaction(keyPair, contractAddress, encodedData, gasLimit, gasPrice, fee, utxoList)
```
