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

## Interacting with Your Node

Now that your node is up and running, you can interact with the ElonChain network:

- **Geth JavaScript Console**: Opened via the attach command, this console allows for direct blockchain interactions.
- **Web3.js**: This popular JavaScript library can be used to interact with your node through RPC calls.
- **Custom Scripts**: You can write scripts in languages like JavaScript or Python to automate tasks or interact with the blockchain.

## Additional Information

- **Chain Name**: ElonChain
- **Coin Symbol**: EMC
- **Consensus Mechanism**: Clique (Proof of Authority)

## Support and Contributions

For questions, support requests, or contributions, feel free to open an issue or submit a pull request to this repository. Community contributions are always welcome!

