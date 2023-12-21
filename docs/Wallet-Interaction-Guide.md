# Interacting with ElonChain Geth Node

This guide covers the essentials of interacting with your node on the ElonChain network using Geth. You'll learn how to create a wallet account, send and receive transactions, and check your balance and transaction details.

## Prerequisites

- A running instance of a Geth node on the ElonChain network.
- Access to the Geth JavaScript Console.

## 1. Creating a Wallet Account

To interact with the blockchain, you first need an account.

### Accessing the Geth Console

Open the Geth JavaScript console by running:

```bash
geth attach /path/to/your/datadir/geth.ipc
```

### Create a New Account

In the Geth console, create a new account:

```javascript
personal.newAccount()
```

You will be prompted to enter a passphrase. Remember this passphrase as it is required to unlock your account for transactions.

## 2. Checking Your Balance

To check the balance of your account:

### Get Account Address

First, list your accounts to get the address:

```javascript
eth.accounts
```

### Check Balance

Then, check the balance of the first account:

```javascript
eth.getBalance(eth.accounts[0])
```

This will display your balance in Wei. To convert it to Ether:

```javascript
web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")
```

## 3. Sending Transactions

To send Ether to another account:

### Unlock Your Account

Unlock your account using your passphrase:

```javascript
personal.unlockAccount(eth.accounts[0])
```

### Send Ether

Send Ether to the recipient:

```javascript
eth.sendTransaction({from: eth.accounts[0], to: 'RECIPIENT_ADDRESS', value: web3.toWei(AMOUNT_IN_ETHER, "ether")})
```

Replace `'RECIPIENT_ADDRESS'` with the recipient's account address and `AMOUNT_IN_ETHER` with the amount you wish to send.

## 4. Receiving Transactions

To receive a transaction, simply provide your account address (from `eth.accounts`) to the sender. There is no active step required on your part to receive Ether.

## 5. Checking Transaction Details

To check the details of a transaction:

### Get Transaction Receipt

Use the transaction hash to get the receipt:

```javascript
eth.getTransactionReceipt('TRANSACTION_HASH')
```

Replace `'TRANSACTION_HASH'` with the hash of the transaction you want to check.

## 6. Monitoring Transactions

To monitor incoming transactions for your account:

### Watch for Transactions

You can set up a filter to watch for transactions:

```javascript
eth.filter({address: eth.accounts[0], toBlock: 'latest'}).watch((error, result) => {
  if (!error)
    console.log(result);
})
```

This will log any new transactions involving your account.

## Conclusion

This guide covers the basic operations you'll need to manage your wallet and interact with the ElonChain network using Geth. Remember to always keep your passphrase secure and to regularly backup your wallet.

## Support

For further assistance or questions, feel free to raise an issue in the repository or contact the ElonChain support team.
