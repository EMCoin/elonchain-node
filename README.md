# ElonChain: Private Blockchain Network Guide

Welcome to the ElonChain network! This guide is designed to help you set up and participate in ElonChain, a bespoke private blockchain using the Geth implementation of Ethereum with the Clique consensus protocol. Our network is tailored for efficient, secure, and easy-to-manage operations, making it ideal for developers and enthusiasts interested in exploring blockchain technology in a controlled environment.

## Prerequisites

To participate in the ElonChain network, you will need to have the following prerequisites installed and configured on your system:

1. **Geth (Go Ethereum)**

   - The core of our blockchain network is based on Geth, the popular Go implementation of Ethereum.
   - Ensure you have Geth version 1.9 or later installed.
   - Installation guides for Geth can be found here: [Installing Geth](https://geth.ethereum.org/docs/install-and-build/installing-geth).

2. **Git (Optional)**

   - Git is used for version control and for easily cloning the necessary configurations and scripts from our repository.
   - If you prefer not to use Git, you can manually download the required files from the repository.
   - Installation guides for Git are available here: [Git Installation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

3. **Basic Command Line Knowledge**

   - Familiarity with using the command line is essential as most interactions with Geth and blockchain configuration will be done through it.

4. **A Code Editor (Optional)**

   - Having a code editor like Visual Studio Code, Sublime Text, or Atom can be helpful for editing configuration files and scripts.
   - Choose an editor that you're comfortable with.

5. **Stable Internet Connection**

   - A stable and active internet connection is required for downloading necessary software and synchronizing with the blockchain network.

6. **Sufficient Storage Space**
   - Ensure you have enough storage space on your device for blockchain data. The required space can grow over time with the network's activity.

Once you have these prerequisites in place, you can proceed with setting up your node on the ElonChain network as detailed in the following sections.

## Setting Up Your Node

### 1. Clone the Repository

To get started with your ElonChain node, clone the repository containing the essential `genesis.json` file:

```bash
git clone https://github.com/EMCoin/elonchain-node
cd elonchain-node
```

Replace `https://github.com/EMCoin/elonchain-node` and `elonchain-node` with the appropriate URL and name of your repository. If you are not using Git, simply download the `genesis.json` file directly from the repository.

### 2. Initialize Your Blockchain

With the `genesis.json` file in place, initialize your node using the following command:

```bash
geth init genesis.json --datadir /path/to/your/datadir
```

Here, `/path/to/your/datadir` should be replaced with the path to the directory where you want to store your blockchain data.

### 3. Start the Blockchain

Launch your ElonChain node with the following command:

```bash
geth --datadir /path/to/your/datadir --networkid 7106 --http --http.addr "0.0.0.0" --http.port 8545 --http.corsdomain "*" --http.api "admin,eth,debug,miner,net,txpool,personal,web3" --port 30303 --nodiscover --verbosity 3 --nat "any"
```

Make sure to use a unique `--networkid` for your ElonChain network. This command configures your node and opens necessary ports and APIs for interaction.

### 4. Attach to Your Node (Optional)

For direct interaction with your node, use the Geth JavaScript console:

```bash
geth attach /path/to/your/datadir/geth.ipc
```

This command allows you to execute Geth commands and interact with the blockchain directly.

### 5. Adding Peers

Once your node is up and running, you may want to connect it with other peers in the ElonChain network. This is essential for synchronizing your blockchain data with the network. Here are the steps to add peers:

1. **Access the Geth Console**:
   If you haven't already, attach to your node using the Geth JavaScript console:

   ```bash
   geth attach /path/to/your/datadir/geth.ipc
   ```

2. **Add Peers**:
   In the console, use the `admin.addPeer` command to connect to each peer. Here are the peers you can connect to:

   - Peer 1:
     ```bash
     admin.addPeer("enode://9ee6906a9d5264ac16ddf2cad501e9a30126d1f6546ce0deba706b0f4db376088fa9e48e3281c975bb44de20ac80ad51cbf0b877f5756b7e43065a7ac770d695@195.201.246.33:30303?discport=0")
     ```
   - Peer 2:
     ```bash
     admin.addPeer("enode://b5fec3f358a72153b89c0d84e474beb518d51961ee8d67b79326d00b79fde9e590ea57716a4393d4e55508871f179469a08b40cc46ffd01b994d16366dc4003e@65.108.61.194:30303?discport=0")
     ```

   After running these commands, your node will attempt to connect to the specified peers.

3. **Verify Connection**:
   To check if the peers are successfully added and your node is connected, use the following command:

   ```bash
   admin.peers
   ```

   This command will display information about all connected peers.

By connecting to peers, you ensure that your node stays up-to-date with the latest state of the blockchain and can participate in network consensus.

## Interacting with Your Node

Now that your ElonChain node is up and running, and connected to peers, you have various ways to interact with the network:

### 1. Using the Geth JavaScript Console

The Geth JavaScript Console provides a powerful interface for interacting with your node and the blockchain:

- **Access the Console**:
  You can access it by attaching to your node:

  ```bash
  geth attach /path/to/your/datadir/geth.ipc
  ```

- **Common Commands**:
  - Check your node's synchronization status:
    ```javascript
    eth.syncing;
    ```
  - Get the list of accounts:
    ```javascript
    eth.accounts;
    ```
  - Check your balance:
    ```javascript
    eth.getBalance(eth.accounts[0]);
    ```
  - Send a transaction (after unlocking the account):
    ```javascript
    personal.unlockAccount(eth.accounts[0]);
    eth.sendTransaction({
      from: eth.accounts[0],
      to: "RECIPIENT_ADDRESS",
      value: web3.toWei(1, "ether"),
    });
    ```

### 2. Interacting via Web3.js

Web3.js is a popular JavaScript library that allows you to interact with your node over HTTP, WebSocket, or IPC:

- **Setting Up Web3.js**:
  You can include Web3.js in your Node.js project or any web application. First, install it using npm:

  ```bash
  npm install web3
  ```

- **Basic Usage**:
  - Connect to your node:
    ```javascript
    const Web3 = require("web3");
    const web3 = new Web3("http://localhost:8545");
    ```
  - Retrieve the current block number:
    ```javascript
    web3.eth.getBlockNumber().then(console.log);
    ```
  - Listen for new blocks:
    ```javascript
    web3.eth.subscribe("newBlockHeaders", function (error, result) {
      if (!error) {
        console.log(result);
      }
    });
    ```

### 3. Creating Smart Contracts

Smart contracts are self-executing contracts with the terms of the agreement directly written into code:

- **Write the Contract**:
  Write your smart contract in Solidity, the programming language for Ethereum smart contracts.

- **Compile and Deploy**:
  Use tools like Truffle or Hardhat to compile and deploy your contracts to the ElonChain network.

- **Interact with the Contract**:
  Once deployed, interact with your smart contract through the Geth console or Web3.js.

### 4. Monitoring and Administration Tools

For advanced users, several tools and interfaces can provide more in-depth interaction and monitoring of the network:

- **Geth's built-in monitoring tools**: `geth monitor`
- **Blockchain explorers**: Customized for private networks to visualize block and transaction data. [ElonChain Scan] (https://scan.eloncoin.org)

Remember, interacting with a blockchain network requires a careful approach, especially when executing transactions or deploying smart contracts. Always test thoroughly in a safe environment before proceeding with real transactions.

## Additional Information

- **Chain Name**: ElonChain
- **Coin Symbol**: EMC
- **Consensus Mechanism**: Clique (Proof of Authority)

## References and Further Reading

The following resources provide additional information and detailed documentation, which can be extremely useful for both beginners and advanced users working with ElonChain and Geth:

### Geth Documentation

- **Interacting with Geth**: For a comprehensive guide on interacting with Geth, including the JavaScript console, check out the official Geth documentation:
  - [Geth - JavaScript Console](https://geth.ethereum.org/docs/interacting-with-geth/javascript-console)
    This resource provides in-depth details about various commands and functionalities available in the Geth JavaScript Console, a key tool for interacting with your node and the ElonChain network.

### Additional Learning Resources

- **Solidity Documentation**: To learn more about writing smart contracts in Solidity, visit [Solidity Documentation](https://docs.soliditylang.org/).
- **Web3.js Documentation**: For detailed information on using Web3.js to interact with Ethereum networks, refer to [Web3.js Documentation](https://web3js.readthedocs.io/).
- **Ethereum Development Tools**: Explore various tools and frameworks like Truffle, Hardhat, and Remix for Ethereum development at [Truffle Suite](https://www.trufflesuite.com/) and [Hardhat](https://hardhat.org/).

### Community and Support

- **Ethereum StackExchange**: A great place to ask questions and find answers from the Ethereum community is [Ethereum StackExchange](https://ethereum.stackexchange.com/).
- **Ethereum Reddit**: Join discussions and stay updated on the latest trends and topics in the Ethereum ecosystem at [r/ethereum](https://www.reddit.com/r/ethereum/).

Utilizing these resources will help you deepen your understanding of blockchain technology, smart contract development, and effective management of your ElonChain node.

## Support and Contributions

For questions, support requests, or contributions, feel free to open an issue or submit a pull request to this repository. Community contributions are always welcome!
