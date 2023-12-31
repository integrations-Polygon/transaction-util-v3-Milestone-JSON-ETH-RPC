# **Transaction-util-v3**

**Transaction-util-v3** is a utility that utilize Polygon's powerfull tools such as **Polygon's gas station network API** to ensure that your transaction has the latest gas prices and etherjs **gas estimator** method to estimate your transaction **gasLimit** before sending it to the Polygon network in a robust manner. It also makes sure to check for your transaction block finality by using the newly added eth **finality tag** in **eth JSON RPC API** for the method **eth_getBlockByNumber** for the Polygon Network.

## **Getting started**

- Clone this repository

```bash
git clone https://github.com/integrations-Polygon/transaction-util-v3.git

```

- Navigate to `transaction-util-v3`

```bash
cd transaction-util-v3

```

- Install dependencies

```bash
npm install

```
or

```bash
yarn

```
- Create `.env` file

```bash
cp .env.example .env

```

- Configure environment variables in `.env`

```
INFURA_PROJECT_ID=<infura-project-id>
PRIVATE_KEY_MATIC=<private-key-matic>
EXPLORER_API_KEY_MATIC=<explorer-api-key-matic>

```

## **Usage**

Firstly, you would need to **deploy** a smart contract to test the **PIP-11 milestone finality**

### **Deploy your smart contract**

To deploy your smart contract, first you would need to freshly **compile** your smart contract by simply running this command

```bash
npx hardhat clean

```
and

```bash
npx hardhat compile

```
After that, to actually **deploy** the smart contract run this command

```bash
npx hardhat deploy --network matic

```

### **Verify your deployed smart contract (OPTIONAL)**

It is always a good practice to **verify** your smart contract for future debugging sessions by simple running this command

```bash
npx hardhat verify --network matic <deploy-contract-address> <if-any-arguments-seperated-by-space>

```

### **Start the script**

Start the **script** by running this command

```bash
npx hardhat run ./scripts/startScript.ts

```

The script will automatically try to mint one **ERC721 NFT** by properly fetch your latest nonce value for **nonce management**, fetch the latest gas prices from the **Polygon's gas station API** and also utilize the etherjs **gas estimator** method properly to estimate the transaction's gasLimit and mints your NFTs with these raw transaction data. Once the transaction has been added to a block, your block will be compared with the finalizedBlock fetched using the newly added eth **finality tag** in **eth JSON RPC API** for the method **eth_getBlockByNumber**

basically, querying the eth_getBlockByNumber method with defaultBlock parameter as **'finalized'** to get the finalized block number and compare it with your transaction block number 

### **Contributing**:

If you encounter any issues or have suggestions for improvements, please open an issue or submit a pull request. We welcome community contributions.
