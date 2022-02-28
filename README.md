# How to Create an NFT
This has been built while following the tuorials (below References from Part-1 to Part-3) for minting NFT with ERC721 token using [Alchemy developer platform](https://www.alchemy.com/) and its web3 library [@alch/alchemy-web3](https://www.npmjs.com/package/@alch/alchemy-web3)

### Environment Setup
Make .env file in the root oy your project and add following as mentioned at [Part-2-step-6-update-the-env-file](https://docs.alchemy.com/alchemy/tutorials/how-to-create-an-nft/how-to-mint-a-nft#step-6-update-the-env-file) 
```
API_URL = "https://eth-ropsten.alchemyapi.io/v2/your-api-key"
PRIVATE_KEY = "your-metamask-wallet-account-PRIVATE-Key"
PUBLIC_KEY = "your-metamask-wallet-account-PUBLIC-address"
```

### Reference
Part-1 https://www.web3.university/article/how-to-create-an-nft
Part-2 https://docs.alchemyapi.io/alchemy/tutorials/how-to-write-and-deploy-a-nft-smart-contract/how-to-mint-a-nft
Part-3 https://docs.alchemyapi.io/alchemy/tutorials/how-to-write-and-deploy-a-nft-smart-contract/how-to-view-your-nft-in-your-wallet

Folder location ```/Users/ajay/Blockchain/web3.university/Alchemy/my-nft```

### Activity Codes
```
ajay@Ajays-MacBook-Pro my-nft % npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (my-nft) 
version: (1.0.0) 
description: 
entry point: (index.js) 
test command: 
git repository: 
keywords: 
author: 
license: (ISC) 
About to write to /Users/ajay/Blockchain/web3.university/Alchemy/my-nft/package.json:

{
  "name": "my-nft",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


Is this OK? (yes) 
```


```
ajay@Ajays-MacBook-Pro my-nft % npm install --save-dev hardhat
npm WARN deprecated fsevents@2.1.3: "Please update to latest v2.3 or v2.2"
npm WARN deprecated debug@3.2.6: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)

added 338 packages, and audited 339 packages in 32s

61 packages are looking for funding
  run `npm fund` for details

9 moderate severity vulnerabilities

To address all issues, run:
  npm audit fix

Run `npm audit` for details.
```
```
ajay@Ajays-MacBook-Pro my-nft % npx hardhat
888    888                      888 888               888
888    888                      888 888               888
888    888                      888 888               888
8888888888  8888b.  888d888 .d88888 88888b.   8888b.  888888
888    888     "88b 888P"  d88" 888 888 "88b     "88b 888
888    888 .d888888 888    888  888 888  888 .d888888 888
888    888 888  888 888    Y88b 888 888  888 888  888 Y88b.
888    888 "Y888888 888     "Y88888 888  888 "Y888888  "Y888

👷 Welcome to Hardhat v2.8.4 👷‍

✔ What do you want to do? · Create an empty hardhat.config.js
✨ Config file created ✨
```
```
ajay@Ajays-MacBook-Pro my-nft % mkdir contracts
```
```
ajay@Ajays-MacBook-Pro my-nft % mkdir scripts
```
```
ajay@Ajays-MacBook-Pro my-nft % npm install @openzeppelin/contracts@3.1.0-solc-0.7

added 1 package, and audited 340 packages in 7s

61 packages are looking for funding
  run `npm fund` for details

9 moderate severity vulnerabilities

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.
```
```
ajay@Ajays-MacBook-Pro my-nft % npm install dotenv --save

added 1 package, and audited 341 packages in 3s

61 packages are looking for funding
  run `npm fund` for details

9 moderate severity vulnerabilities

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.
```
```
ajay@Ajays-MacBook-Pro my-nft % npm install --save-dev @nomiclabs/hardhat-ethers "ethers@^5.0.0"

added 17 packages, and audited 358 packages in 5s

74 packages are looking for funding
  run `npm fund` for details

10 moderate severity vulnerabilities

Some issues need review, and may require choosing
a different dependency.

Run `npm audit` for details.
```
```
ajay@Ajays-MacBook-Pro my-nft % npx hardhat compile
Downloading compiler 0.7.3
Compiling 16 files with 0.7.3
contracts/MyNFT.sol:14:5: Warning: Visibility for constructor is ignored. If you want the contract to be non-deployable, making it "abstract" is sufficient.
    constructor() public ERC721("MyNFT", "NFT") {}
    ^--------------------------------------------^

Solidity compilation finished successfully
```
```
ajay@Ajays-MacBook-Pro my-nft % npx hardhat run scripts/deploy.js --network ropsten
Contract deployed to address: 0x7c97666d1d898684757F1DF14585a647Ca0c5D65
```
```
ajay@Ajays-MacBook-Pro my-nft % node scripts/mint-nft.js
Transaction receipt: ```javascript{"transactionHash":"0x0d45762a0d96fcf97aae888cd9613907dd9935a854aa6008bbe490e2ab038eb4","blockHash":"0xa8c13326a48a71dded3c1a757b3262020974a481f088310ac2e368928696b772","blockNumber":12023319,"contractAddress":null,"cumulativeGasUsed":317409,"effectiveGasPrice":"0xb2d05e02","from":"0x6a7ae043f469a583b569776714b0d9a1af9a5457","gasUsed":296409,"logs":[{"address":"0x7c97666d1d898684757F1DF14585a647Ca0c5D65","topics":["0xddf252ad1be2c89b69c2b068fc378daa952ba7f163c4a11628f55a4df523b3ef","0x0000000000000000000000000000000000000000000000000000000000000000","0x0000000000000000000000006a7ae043f469a583b569776714b0d9a1af9a5457","0x0000000000000000000000000000000000000000000000000000000000000001"],"data":"0x","blockNumber":12023319,"transactionHash":"0x0d45762a0d96fcf97aae888cd9613907dd9935a854aa6008bbe490e2ab038eb4","transactionIndex":1,"blockHash":"0xa8c13326a48a71dded3c1a757b3262020974a481f088310ac2e368928696b772","logIndex":0,"removed":false,"id":"log_780bef8b"}],"logsBloom":"0x00000000000000000000000000400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000040000000000000000000000000008000000000000000000040000000000000000000000000000020000000000000000000800000000000000000000000010000000000000200000000000000000000000000000000000008000000000000000000008000000000000000000000000000000000000000000000000000000000000000000000002000000000080000040000000000000000000000000000000000060000000000000000000000000000000000000000000000000000000000000000000","status":true,"to":"0x7c97666d1d898684757f1df14585a647ca0c5d65","transactionIndex":1,"type":"0x2"}```
