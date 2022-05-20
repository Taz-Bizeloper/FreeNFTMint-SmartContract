<h1 align="center">
  <a href="https://FreeNFTMint.app"><img width="30%" src="https://freenftmint.app/assets/images/logo.png" alt="Free NFT Mint App logo" /></a>
</h1>

<h3 align="center">ERC-1155 NFT token smart contract used by <a href="FreeNFTMint.app">FreeNFTMint.app</a></h3>

<h4 align="center">Made With 🧡 By The <a href="https://Bizelop.app">Bizelop</a> Community </h4>
<p align="center">
  <a href="https://discord.gg/bizelop"><img src="https://img.shields.io/badge/chat-discord?style=for-the-badge&logo=discord&label=discord&logoColor=7389D8&color=ff6501" /></a>
  <a href="https://twitter.com/mmwirelesstech"><img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/mmwirelesstech?color=ff6501&label=twitter&logo=twitter&style=for-the-badge"></a>
</p>



# About
This smart contract is an example of how you can setup different metadata IPFS URL's for each token and allowing to update the metadata IPFS URL via smart contract.

 The metadata IPFS URL's are passed to the smart contract upon minting. The metadata IPFS URL for the token can then be updated on the blockchain to point to a new URL

This smart contract code is deployed on the Ethereum network and is currently used in the [FreeNFTMint.App](https://FreeNFTMint.App) dApp

Here is the deployed address and verified source code on etherscan.

Mainnet - [0x7527e85c4b224ad0301b99d2e5a09085661ae8f3](https://etherscan.io/address/0x7527e85c4b224ad0301b99d2e5a09085661ae8f3)

Rinkeby - [0xa72B399F44Eed50AcEa7194c63eD6b068E76AE6B](https://rinkeby.etherscan.io/address/0xa72B399F44Eed50AcEa7194c63eD6b068E76AE6B)


You are free to clone and update the code as needed and if you need any help join the [Discord](https://discord.gg/bizelop)




## Prerequisites

Node version 16.13.0 (This version is what we used) 
 
 - Use Node Version Manager (nvm) to install and use different node versions on the same machine

An IDE with Solidity compiler
- Visual Studio Code with the Solidity extension

## Initial Setup 

Clone the smart contract project to your local machine

```bash
git clone https://github.com/bizelop/FreeNFTMint-SmartContract.git
```

cd to the folder 

```bash
cd freeNFTMint-SmartContract
```
install node dependencies (see package.json)

```bash
npm install
```

Create a .env file with the following keys:

```
ALCHEMY_KEY = "" 
ACCOUNT_PRIVATE_KEY = ""
NETWORK=""
ETHERSCAN_API_KEY = ""
NFT_CONTRACT_ADDRESS=""
```
ALCHEMY_KEY - Create an [Alchemy](https://www.alchemy.com/) dev account and register your dApp to get your API Key

ACCOUNT_PRIVATE_KEY - The private key to your wallet. Please make sure to never sync or expose this private key to anyone or send it to anyone! Each developer should have their own test wallet to test with. 

NETWORK - Match the network from the hardhat.config.js network object. use "rinkeby" for deploying to test. use "mainnet" to deploy to live production.

ETHERSCAN_API_KEY - Create an [Etherscan](https://etherscan.io) dev account and register your dApp to get your API Key

NFT_CONTRACT_ADDRESS - (Optional) Can be used later to write scripts that will get the contract and do something with it

# Update The Smart Contract

Now that you have the initial setup you can now go into the smart contract file located at:

```
contracts/Free-NFT-Mint-App.sol
```

Update the file name and Smart Contract name to your project name


 Some data is needed specifically for NFT marketplaces like OpenSea to be able to read in your contract information and these are:


```
string public name = "FreeNFTMint.App"; //returns back the contract name for dApps
.
.
.
function contractURI() public view returns (string memory) {
    //Link to json file on a centralized server for marketplaces to read in
    //this file can contain project name, description, logo image, and website URL
        return "https://freenftmint.app/contractMeta.json";
    }
```


# Compile and Deploy 

The project uses [HardHat](https://hardhat.org) to compile and deploy the smart contract to the blockchain. The scripts folder has two files that are ready to go. A deploy.js that contains the hardhat deploy task to run, and a helper.js that contains ethers.js functions used by deploy.js

To test compiling the smart contract to make sure it compiles type in the hardhat command

```
npx hardhat compile
```

This will create two extra folders (artifacts and cache) You can now find your compiled ABI in:

```
artifacts/contracts/YOUR_CONTRACT.json 
```
the JSON has a few properties one which is the ABI that you can copy over to your dApp client side.

To deploy to the blockchain make sure your NETWORK property is set to the network you want to deploy to in your .env file. 

For deploying to rinkeby type in the command:
```
npx hardhat deploy --network rinkeby
```

For deploying to Mainnet type in the command:
```
npx hardhat deploy --network mainnet
```

This may take a few minutes. Once deployed you will get your smart contract address in the console log copy it.

# Verify Your Smart Contract On Etherscan 
You can verify your smart contract with etherscan very easily. Etherscan smart contract verification provides transparency for users interacting with smart contracts. Your smart contract source code will be uploaded and matched against the compiled version you deployed. Users can then verify and audit the code to make sure it does what it is supposed to do.

Once deployed if you want to have your smart contract verified on etherscan run the following command and replace NETWORK with "rinkeby" or "mainnet"

```
npx hardhat verify --network NETWORK smart_contract_address
```
Full example:

```
npx hardhat verify --network rinkeby 0xa72B399F44Eed50AcEa7194c63eD6b068E76AE6B
```

# License

```
MIT License

Copyright (c) 2022 Bizelop Community Code

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

```