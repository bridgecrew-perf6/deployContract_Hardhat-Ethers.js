# Deploy Basic Contract with Rinkeby Testnet and Hardhat Test

### 1. Create Project Structure

npm init -y
npm install --save-dev hardhat
npm install @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers dotenv

Create .env file. dotenv installs a package that allows us to use sensitive data as environment variables in our project. Rinkeby private key as a variable

npx hardhat -> Create basic sample project and select y to everything

### 2. Create Config files

hardhat.config.js

### 3. Add A Smart Contract File

We'll be deploying a generic faucet contract on Rinkeby - anyone will be able to send and withdraw some ether, just like the typical faucets we use to acquire Rinkeby - when they are working! The Faucet contract is quite simple; it allows anyone to call the withdraw method and specify an amount lower than .1 ETH at a time. The receive fallback function will handle any ETH deposited into the Faucet and add it to the contract balance.

1. cd into your contracts folder and run touch Faucet.sol
2. create faucet.sol
3. save files to your contracts folder

### 4. Add scripts

The Faucet contract is quite simple; it allows anyone to call the withdraw method and specify an amount lower than .1 ETH at a time. The receive fallback function will handle any ETH deposited into the Faucet and add it to the contract balance.We will need one script:deployment script.

1. In your scripts directory, run touch deploy.js
2. Create script (Remember, we are using our Alchemy key as always - but imported from our .env file using process.env)

### 5. Deloy to Rinkeby

First, compile the Faucet.sol with Hardhat so that all the necessary artifacts are created...

1. npx hardhat compile
   You should now see an artifacts folder pop up in your project directory - search through it to spot your contracts abi and bytecode!
2. npx hardhat run scripts/deploy.js --network rinkeby
   Notice we used the --network flag above? This is where our changes in hardhat.config.js come in, we are telling Hardhat to run this command in our predefined network which is Rinkeby.
3. You should now see your newly-deployed contract address as terminal output - nice!
4. Copy-paste that address into https://rinkeby.etherscan.io/ and check out your contract in live deployment form

## Hardhat Commands

This project demonstrates a basic Hardhat use case. It comes with a sample contract, a test for that contract, a sample script that deploys that contract, and an example of a task implementation, which simply lists the available accounts.

Try running some of the following tasks:

```shell
npx hardhat accounts
npx hardhat compile
npx hardhat clean
npx hardhat test
npx hardhat node
node scripts/sample-script.js
npx hardhat help
```
