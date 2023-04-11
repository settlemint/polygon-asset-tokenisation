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
4. Click on Blockchain networks and add a `Polygon Testnet` network and a node (e.g. Your_Name_Network, Your_Name_Node)
5. Click on Storage and add a `IPFS (decentralised)` storage
6. Click on Private keys and add a `Accessible EC DSA P256` key
7. Click on Smart Contracts sets and add a `Empty` template (e.g. Your_Name_Asset_Tokenisation)

### Fund your Private key

1. In the SettleMint BPass Platform, head over to `Private keys` and copy `private key`
2. Head over to `https://faucet.polygon.technology/`
3. Under `Mumbai` Network, paste your `private key` and click `Submit`

### Set up your PolygonScan API key

1. Head over to `https://polygonscan.com/` and go to `API-KEYs`
2. Create your API key and copy it
3. Note down your API key

### Setting up and Deployment of your Smart Contract

1. In the SettleMint BPass Platform, head over to `Smart contract sets`
2. Click on your deployed smart contract set and go to the IDE tab and click `view in fullscreen mode`
3. Copy the template `AssetTokenisation.sol` found in `./Smart-Contracts` and paste it in the IDE's folder `./contracts`
4. In the folder `./deploy`, open the file named `00_deploy_example.ts` and in line 13, change the name of the contract depending on your file name

```javascript
  await deploy('AssetTokenisation', {
    from: deployer,
    args: [],
    log: true,
  });
```

4. In the root folder, open the file named `hardhat.config.ts` and in line 34, change the Solidity version to 0.8.13 and add in your PolygonScan API key

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

5. Deploy your Asset Tokenisation smart contract! 

```bash
pnpm run smartcontract:deploy:reset
```

6. Note down your deployed smart contract address

7. Open the `abi` folder, go to `AssetTokenisation.json` and copy the json contents

8. Note down your json contents

### Set up your SettleMint API key

1. In the SettleMint BPass Platform, click on your profile icon at the top right at click on `API keys`
2. Check all the boxes and generate your API key
3. Note down your API key

### Upload your Image to IPFS

1. In the SettleMint BPass Platform, head over to `Storage` and click into your deployed `IPFS (decentralised)` storage
2. Click on the `File Manager` tab and click on the `Import` button and choose `File`
3. Choose an image that represents your asset and upload your image
4. Click on the ellipsis at the far right and click `Set pinning` to pin your image
5. Click on the ellipsis at the far right again and click `Share link` to copy the link to your image
6. Note down your image uri.

### Find your JSON-RPC endpoint

1. In the SettleMint BPass Platform, click on `Blockchain nodes`, click on your deployed node and click on `Connect`
2. Note down your `JSON-RPC` endpoint.

### BUIDL session

1. Now, you are ready to BUIDL!
2. In the SettleMint BPass Platform, click on `Integration tools` and deploy an `Integration Studio` tool.
3. Click on your deployed `Integration Studio`, click on `Interface` and click `view in fullscreen mode`
4. At the top right dropdown box, click on `Import` and import the `flows.json` found in the `Integration-Studio` directory
5. Once imported, click on the `Blockchain APIs` tab and double click on the `Set Global Variables` module
6. Go to the `On Message` tab and input your noted down variables and click `Done`

```javascript
    settlemintKey: 'bpass-...',
    rpcEndpoint: 'https://...',
    privateKey: '0x...'
    contract: '0x...',
    abi: [

    ]
```

10. Now, click on `Deploy`
---
