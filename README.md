# NFT Contracts

Features include:

## ERC721CommunityImplementation.sol
- Limited supply
- Mint N tokens in one transaction
- Generative art
- Lazy Mint – buyers pays for mint
- Manually start/stop sale
- Reserve X tokens for team or community
- Deployed by Factory using Clones
- Supports `NFTExtension` to upgrade mint and tokenURI functions

## ERC721CommunityBase.sol
- Same features as ERC721CommunityImplementation
- Import and inherit in your own projects

```solidity
contract MyPFPNFT is ERC721CommunityBase {

    constructor() ERC721CommunityBase(
        0.1 ether, // public mint price, you can change later
        10000, // total supply
        100, // reserved
        20, // max mint per transaction
        0, // royalty fee
        "ipfs://Qm/", // baseURI
        "Bored Ape Yacht Club", 
        "BAYC",
        false // should start at 1 or at 0?
    ) {}

}
```

## ERC721CommunityImplementation_

```bash
colordiff contracts/ERC721CommunityImplementation_.sol contracts/ERC721CommunityImplementation.sol
```

## NFTExtension
- Can be added to main NFT using `addExtension`
- Support changing mint and tokenURI functions

## How to use:

### Init

```bash
npm i
touch .mnemonic
node scripts/generate_mnemonic.mjs
vim .mnemonic # input generated mnemonic

cp .env.example .env
vim .env # input your keys
```

### Development

When you change something, run:

```bash
npx hardhat compile
```

Then, to test your code:

```bash
npx hardhat test
```

### Checking different versions of ERC721CommunityImplementation:

```bash
colordiff contracts/ERC721CommunityBase.sol contracts/ERC721CommunityImplementation.sol --context=1
colordiff contracts/ERC721CommunityBase_ERC1155.sol contracts/ERC721CommunityBase.sol --context=1
```

### Deploy to production

You can deploy using Hardhat. Refer to Hardhat scripts and console guides for deployment.
https://hardhat.org/guides/deploying.html

However, we also support deploying with your Metamask:

### Upload to IPFS for Frontend Deploy

Instead of deploying from your local machine, you can compile and send it for deployment from  the Buildship web app.

```bash
hh upload contracts/Greeter.sol --args '"hello","bar"'
```

It needs network selection to run, but it doesn't matter which you use. You can run with development network.

### Thanks

ERC721A for their mint-optimized ERC721 https://erc721a.org/
