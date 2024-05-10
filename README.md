# Genitive-Network

Genitive Network is an FHE-based BTC L2 cross-chain bridge using Zamas fhEVM library.

## Project Overview

Currently, there are nearly a hundred BTC Layer 2 chains, which are independent of each other and cannot interconnect their states. Users who wish to transition from one L2 to another must first cross back to the BTC mainnet, and the multi-step cross-chain process incurs extremely high gas fees. That's why we need a BTC L2 cross-chain bridge.

And, the implementation method of BTC L2 cross-chain bridges should be different from those in the Ethereum ecosystem as they do not share the same security logic. Bitcoin's security comes from PoW and L2s built on PoS can't use PoW for security which means the tx can be traced. 

Furthermore, the current cross-chain bridges solutions in the market like Orbiter Finance and Owlto are often running with a centralized asset pool that controls users' funds. They said they are decentralized but actually not. Other solutions are looking for ZKP + BTC L2 model which is still in the Ethereum way. It won't work for BTC.

Our idea is using fhevm for encrypted transactions to keep Bitcoin L2 tx private for users, therefore enhance the security of the entire BTC ecosystem. In this way, it's equivalent to utilize pure cryptographic algorithms and mathematical proofs to secure cross-chain tx between BTC L2s to BTC's security level. Users can trust the cross-chain bridge tool itself, rather than trust a specific team.


## Test Here

https://genitive-bridge.vercel.app/bridge



## Repo

Repo includes:
 - fhevm
   - monitor bot
   - crosschain server
 - bevm
 - frontend

### fhevm
 - Smart contracts in **fhevm\py_transfer_monitor\contracts**
   - The contracts are based on the encrypted ERC20 contract code provided by ZAMA, with adjusted interface functions and added specific events, allowing for more accurate monitoring of on-chain data.
   - Main methods and event
     ```solidity
     function transfer(address to, bytes calldata encryptedAmount) returns (bool) {...}
     function balanceOf(address wallet, bytes32 publicKey, bytes calldata signature) view returns (bytes memory) {...}
     function mint(uint64 amount, address to) {...}
     event CrossChainTransfer(uint64 amount, address indexed from, address indexed to)
     ```
 - Monitor bot in **fhevm\py_transfer_monitor**
   - Using Python scripts to monitor on-chain data, when valid cross-chain transactions are identified, requests will be sent to the BEVM server to perform cross-chain operations.
 - crosschain server in **fhevm_js_server**
   - Using an HTTP server to receive cross-chain requests to FHEVM.
   - API：
     - url: **http://hostname:port/api/mint**
     - parameter：{"address":"0x000000000000000", "amount":123}
 
- Monitor bot in **bevm monitor**
  Use Bevm to implement back-end development, including monitoring data events on the blockchain and calling the Restful api to the fhEvm.

  Main functionalities:
  
  ```go
  func Mint(address string, amount big.Int) error : mint tokens based on amount
  func Burn(address string, amount decimal.Decimal) error: burn tokens based on amount
  func Runbevm() : listen for the transfer events in the bvem blockchain
  ```
  

*** in ***
(这个库实现了什么功能，然后提供了几个 public methods，分别是什么，什么用）




*** in ***
(这个库实现了什么功能，然后提供了几个 public methods，分别是什么，什么用）

*** in ***
(这个库实现了什么功能，然后提供了几个 public methods，分别是什么，什么用）

*** in ***
(这个库实现了什么功能，然后提供了几个 public methods，分别是什么，什么用）



## UI

UI signs/sends transaction using Metamask SDK.

Contract calls are written in ***

## Contact information beyond Github:

Email: genitive.network@proton.me









