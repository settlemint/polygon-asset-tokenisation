# polygon-asset-tokenisation

## Context

Polygon Asset Tokenisation Example powered by SettleMint

---

## Technical Details

---

## Get Started

1. Create an account on SettleMint [here](https://console.settlemint.com/)
2. Create an Organisation (e.g. Your_Name_Organisation)
3. Create an Application (e.g. Your_Name_Application)
4. Click on Blockchain networks and add a `Polygon Testnet` network and a node (e.g. Your_Name_Network, Your_Name_Node). Note: choose the smallest resources
5. Click on Storage and add a `IPFS (decentralised)` storage. Note: choose the smallest resources
6. Click on Private keys and add a `Accessible EC DSA P256` key
7. Click on Smart Contracts sets and add a `Empty` template (e.g. Your_Name_Asset_Tokenisation). Note: choose the smallest resources

### Fund your Private key

1. In the SettleMint BPass Platform, head over to `Private keys` and copy `private key`
2. Head over to `https://faucet.polygon.technology/`
3. Under `Mumbai` Network, paste your `private key` and click `Submit`
4. Note down your private key (notes/stickies/etc)

### Set up your PolygonScan API key

1. Head over to `https://polygonscan.com/` and go to `API-KEYs`
2. Create your API key and copy it
3. Note down your API key (notes/stickies/etc)

### Setting up and Deployment of your Smart Contract

1. In the SettleMint BPass Platform, head over to `Smart contract sets`
2. Click on your deployed smart contract set and go to the IDE tab and click `view in fullscreen mode`
3. Copy the template `AssetTokenisation.sol` found in `./Smart-Contracts` and paste it in the IDE's folder `./contracts`. Make sure your file name is the same as the contract name, e.g. `AssetTokenisation.sol` == `contract AssetTokenisation ...`
4. In the folder `./deploy`, open the file named `00_deploy_example.ts` and in line 13, change the name of the contract depending on your file name

```javascript
  await deploy('AssetTokenisation', {
    from: deployer,
    args: [],
    log: true,
  });
```

5. In the root folder, open the file named `hardhat.config.ts` and in line 34, change the Solidity version to 0.8.13 and add in your noted down PolygonScan API key

```js
const config: HardhatUserConfig = {
  abiExporter,
  solidity: {
    version: '0.8.13',
    settings: {
      optimizer: {
        enabled: true,
        runs: 200,
      },
      evmVersion: 'istanbul',
    },
  },
  etherscan: {
    apiKey: {
      polygon : 'xxx'
    }
  },
  namedAccounts,
  networks,
};
```

6. Deploy your Asset Tokenisation smart contract! 

```bash
pnpm run smartcontract:deploy:reset
```

7. Note down your deployed smart contract address (notes/stickies/etc)

8. Open the `abi` folder, go to `AssetTokenisation.json` and copy the json contents

8. Note down your json contents (notes/stickies/etc)

### Set up your SettleMint API key

1. In the SettleMint BPass Platform, click on your profile icon at the top right at click on `API keys`
2. Check all the boxes and generate your API key
3. Note down your API key (notes/stickies/etc)

### Upload your Image to IPFS

1. In the SettleMint BPass Platform, head over to `Storage` and click into your deployed `IPFS (decentralised)` storage
2. Click on the `File Manager` tab and click on the `Import` button and choose `File`
3. Choose an image that represents your asset and upload your image
4. Click on the ellipsis at the far right and click `Set pinning` to pin your image
5. Click on the ellipsis at the far right again and click `Share link` to copy the link to your image
6. Note down your image uri

### Find your JSON-RPC endpoint

1. In the SettleMint BPass Platform, click on `Blockchain nodes`, click on your deployed node and click on `Connect`
2. Note down your `JSON-RPC` endpoint

### BUIDL session

1. Now, you are ready to BUIDL!
2. In the SettleMint BPass Platform, click on `Integration tools` and deploy an `Integration Studio` tool
3. Click on your deployed `Integration Studio`, click on `Interface` and click `view in fullscreen mode`
4. At the top right dropdown box, click on `Import` and import the `flows.json` found in the `Integration-Studio` directory here in a `new flow`
5. Once imported, click on the `Asset Tokenisation` tab and click `Deploy` at the top right

#### 1. Initialise your global variables

1. Double click on the `Set Global Variables` module
2. Go to the `On Message` tab and input your noted down variables and click `Done`

```javascript
    'privateKey': '0x...',
    'contract': '0x...',
    'bpassKey': 'bpaas-...',
    'rpcEndpoint': 'https://...',
    'abi': []
```

3. Click on `Deploy` at the top right and click on the blue button next to the `inject` module, next to `Set Global Variables` module.
4. You can view the output at the debug window on the right side by clicking on the bug icon.

#### 2. Initialise your asset

1. Double click on the `inject` module next to the `Initialise Asset` module
2. Input your variables and click `Done`

```javascript
msg.assetName = ''
msg.assetSymbol = ''
msg.assetUri = ''
```

3. Click on `Deploy` at the top right and click on the blue button next to the `inject` module, next to `Initialise Asset` module.
4. You can view the output at the debug window on the right side by clicking on the bug icon.

#### 3. Get your maturity time

1. Click on the blue button next to the `inject` module, next to the `Current Time + 10 Minutes` module
2. You can view the output at the debug window on the right side by clicking on the bug icon. Take note of the `end` value. This will be used as the maturity time input for the next step.

#### 4. Create your asset

1. Double click on the inject module next to the `Create Asset` module
2. Input your variables and click `Done`

```javascript
msg.assetId = e.g. 1 
msg.maxSupply = e.g. 100 
msg.faceValue = e.g. 1000 
msg.maturityTime = <end value>
```

#### 4. View your created asset

1. Click on the blue button next to the `inject` module, next to the `View Asset` module
2. You can view the output at the debug window on the right side by clicking on the bug icon. 

#### 5. Mint your created asset

1. Double click on the inject module next to the `Mint Asset` module
2. Input your variables and click `Done`

```javascript
msg.assetId = e.g. 1 
msg.amounts = e.g. 10 
msg.recipient = e.g. recipient address 
```

3. Click on `Deploy` at the top right and click on the blue button next to the `inject` module, next to `Mint Asset` module.
4. You can view the output at the debug window on the right side by clicking on the bug icon.

#### 6. View your minted asset balance

1. Click on the blue button next to the `inject` module, next to the `View Balance` module
2. You can view the output at the debug window on the right side by clicking on the bug icon.

## Congratuations! You have minted your first asset on an Asset Tokenisaton Contract through SettleMint! 

CTA 

---
