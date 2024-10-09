# About
This is my first solidity project, all done with the help of foundry.

## Requirements
- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - You'll know you did it right if you can run `git --version` and you see a response like `git version x.x.x`
- [foundry](https://getfoundry.sh/)
  - You'll know you did it right if you can run `forge --version` and you see a response like `forge x.x.x`

## Quickstart
```
git clone https://github.com/robivagner/foundry-fund-me
cd foundry-fund-me
make
```

# Usage

## Deploy
```
forge script script/DeployFundMe.s.sol
```

## Testing

If you want to do unit testing
```
forge test
```

If you want to do forked testing on the sepolia chain for example(the $SEPOLIA_RPC_URL is a enviromental variable check the deployment paragraph to see how it's done)

```
forge test --fork-url $SEPOLIA_RPC_URL
```

### Test coverage

To see the test coverage percentage

```
forge coverage
```

# Deployment to a testnet or mainnet

1. Setup environment variables

You'll want to set your `SEPOLIA_RPC_URL` and `PRIVATE_KEY` as environment variables. You can add them to a `.env` file, like this

```
SEPOLIA_RPC_URL=EXAMPLE_URL
PRIVATE_KEY=EXAMPLE_PRIVATE_KEY
ETHERSCAN_API_KEY=EXAMPLE_ETHERSCAN_API_KEY
```

Then you can type:

```
source .env
```

to use them in the command line after you saved the .env file.


!!PLEASE do NOT put your actual private key in the .env file it is NOT good practice. 
!!EITHER put the private key of a wallet u won't have actual money in OR search ways to use encrypted methods like the methods of [dapptools](https://github.com/dapphub/dapptools/blob/master/src/ethsign/README.md) keystore file.

2. Get testnet ETH

Head over to [faucets.chain.link](https://faucets.chain.link/) and get some testnet ETH. You should see the ETH show up in your metamask.

3. Deploy

```
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY
```

To get the etherscan api key go to their [site](https://etherscan.io/), sign in, hover over your name and go to api keys. 
Then u can click add, give it a name, copy the API key token and put it in an enviromental variable in the .env file like shown above.

## Scripts

After deploying to a testnet or local net, you can run the scripts. 

```
forge script script/Interactions.s.sol:FundFundMe --rpc-url sepolia  --private-key $PRIVATE_KEY  --broadcast
forge script script/Interactions.s.sol:WithdrawFundMe --rpc-url sepolia  --private-key $PRIVATE_KEY  --broadcast
```

## Estimate gas

You can estimate how much gas things cost by running:

```
forge snapshot
```

And you'll see an output file called `.gas-snapshot`

# Thank you!

This is the start of my journey of becoming a smart contract developer, thank you for walking by!