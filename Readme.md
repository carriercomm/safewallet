# Safewallet

<img src="https://travis-ci.org/bigcompany/safewallet.svg?branch=master"/>

The world's first open-source crypto-currency bank.

## Introduction

One of the original purposes of a bank was to safely store it's clients' valuable assets. In mediaeval times it was usually not a very good idea for a merchant to store their gold and silver at home. If a robber came and stole the merchant's valuables, it would be an irrecoverable loss. The bank was a place where gold and silver could be stored in a secure building with armed guards.

In moderns times crypto-currencies are a store of value. Coins exists as digital bits protected by a private key. If a robber gains access to your private key or password, the coins are lost and irrecoverable. A bank is needed to protect the assets of the individual. Using Safe Wallet, individuals are protected from every possible scenario of theft and fraud. Safe Wallet represents the modern version of what a bank should be.

## Features

 - 100% open and open-source
 - Hybrid On-line Off-line wallet system
 - Supports many leading crypto-currencies such as [Bitcoin](http://bitcoin.org) or [Peercoin](http://peercoin.net/)
 - User Account Management
 - Wallet Management
 - Advanced Security Features
 - Our books are open
 - The bank is owned by the account holders

## Status

[http://status.safewallet.org/](http://status.safewallet.org/)

## Current Balance

[http://safewallet.org/vault](http://safewallet.org/vault)

## Open-ownership - Interest for account holders

Safe Wallet account holders are share holders in the bank and receive dividends in the form of a variable annual interest rate. This annual interest rate is directly determined by the banks revenue generated by premium features and transaction fees.

## Security

Security is paramount for Safe Wallet. In order to ensure safety we have enacted several security measures which prevent coins from loss due to: theft, hacks, identify-theft, or even compromised servers.

The Safe Wallet system is built in such a way that even with complete loss of server control the account holders are still protected. We encourage other online services with hosted "hot-wallets" to use the Safe Wallet architecture.

<img src="https://github.com/bigcompany/safewallet/raw/master/docs/safewallet-architecture.png" title="Safe Wallet Architecture"/>

### Key points

 - [There is a pool of offline "cold-wallets"](https://github.com/bigcompany/safewallet/blob/master/creating-offline-wallet.md)
 - Offline wallets are protected with physical security measures
 - Newly deposited coins are *immediately* transfer to offline wallets
 - A wallet database is used to keep track of account holder balances
 - All database actions are tracked with revision history
 - Withdrawals requests are processed on-demand
 - Withdrawals are subject to security procedures, such as email, voice, or video confirmation
 - When the ledger needs to be settled, an offline wallet is manually brought online, drained, and not re-used

## Architecture

Safe Wallet is separated into several smaller services. Each service is intended to run in an isolated environment to help thwart any possible security breach.

### Frontend Web

Serves the front facing web interface for Safe Wallet.

 - User Account Management
 - Sessions
 - Security Settings
 - Wallet Management
 - Withdrawal Requests
 
*To start the frontend in a development environment* 

    node bin/frontend

### Account Deposits

Responsible for all incoming coins. 

 - Immediately transfers received coins from the "hot-wallet" to an offline "cold-wallet".
 - When new coins are received the wallet database is updated
 - To minimize risk, this service moves coins from online to offline as quickly as possible.

*To start deposits in development environment* 

     node bin/deposits --currency bitcoin

### Account Withdrawals

Processes account holder coin withdrawal requests.

 - Checks ledger database for accounts payable
 - Settles accounts payable by draining current "hot-wallet"
 - Can only make payments if a previously offline wallet has been manually brought online
 - Withdrawal requests are subject to security measures before they are approved
 
*To start withdrawals in development environment* 

    node bin/withdrawals

## Built With

 - [Node.js](http://nodejs.org)
 - [CouchDB](http://couchdb.org)
 - [Express](http://expressjs.com)
 - [Resource](http://github.com/bigcompany/resource)
 - [View](http://github.com/bigcompany/view)
 - [mschema](http://mschema.org)
 - [JugglingDB](http://jugglingdb.co/)
 - [Alpaca Forms](http://www.alpacajs.org/)
 - [jQuery](http://jquery.com)

## License

MIT