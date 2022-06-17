# ## Trustified Network is a platform to Sell Digital Services Globally and Accept Crypto Payments without paying Hefty Commissions.

## Inspiration

“Trust” is a key factor for successful transactions between parties. To ensure trust, we involve third party freelancing platforms or middlemen and pay hefty commissions which highly affect the overall profit margins of parties involved in a transaction.

## What it does

Trustified.network is a smart contract assured Escrow Agreement and Payment platform which helps individuals and businesses to grow globally and increase profit margins in four simple steps:

1) List Products, Services, or subscription packages.
2) Create Escrow agreements with personalized terms as per customers.
3) Send/Receive crypto payments in a reliable and secure way without paying hefty commissions to third parties.  
 

# Deploy Smart contracts Boba Network 
 
https://github.com/Trustified-work/Trustified-boba-network/edit/master/hardhat.config.js

```javascript
require("dotenv").config({ path: "./.env" });
require("@nomiclabs/hardhat-ethers");
require("@nomiclabs/hardhat-etherscan");

const privateKey = process.env.REACT_APP_PRIVATE_KEY;
const projectId = process.env.REACT_APP_ROPSTEN_KEY; 


module.exports = {
  networks: {
    hardhat: {}, 
    boba_rinkeby: {
      url: `https://rinkeby.boba.network`,
      accounts: [privateKey],
    }, 
  },

  solidity: {
    version: "0.8.0",
    settings: {
      optimizer: {
        enabled: true,
        runs: 200,
      },
    },
  },
};



```

# contract Address

**BOBA Address** : 0x30393dFc041aE17ceD39522c6Ce2f125D31667CF 

## IPFS/Filecoin : We are Using Web3.Storage, to permanently store all the details of user invoices and subscription services.

```javascript

import { Web3Storage } from "web3.storage";

function getAccessToken() { 
    return process.env.REACT_APP_WEB3_STORAGE_API_KEY;
}

function makeStorageClient() {
    return new Web3Storage({ token: getAccessToken() });
  }

  function makeFileObjects(data) {  
    const blob = new Blob([JSON.stringify(data)], {
      type: "application/json",
    }); 

    const files = [new File([blob], "Invoice_Details.json")];
    return files;
  } 

```


## Chainlink : We have used Chainlink 1) Price Feed 2) Chainlink VRF

https://github.com/Trustified-work/Trustified-boba-network/edit/master/src/modal/CreateInvoiceModal.js

```javascript

 window.ethereum.enable();
  const provider = new ethers.providers.Web3Provider(window.ethereum);
  const signer = provider.getSigner();
  const priceFeed = new ethers.Contract(
    chainLinkPriceFeed,
    chainlinkABI,
    signer
  );
  const randomNumberCon = new ethers.Contract(
    RandomNumberGeneratorContract,
    chainlinkVRFABI.abi,
    signer
  );

 await randomNumberCon.getRandomNumber(1000);
        const randNo = await randomNumberCon.getRandom();
        setLoading(true);
        const formData = {
          invoiceNumber: parseInt(randNo._hex, 16),
          created: values.cdate,
          dueDate: values.ddate,
          description: values.description,
          quantity: values.quantity,
          price: values.price,
          token: selectedToken,
          network: values.network,
          name: values.name,
          address: values.address,
          taxName: values.taxName,
          taxPercentage: values.taxPercentage,
          note: values.note,
        };
        const files = makeFileObjects(formData);
        await storage(files, formData);

```



# Homepage
![Screenshot 2022-06-17 at 6 58 13 PM](https://user-images.githubusercontent.com/3678906/174307988-9cc2630c-9c60-4d71-b367-cd93ca21b8fe.png)


 

# Escrow Agreement 

![Screenshot 2022-06-17 at 6 58 43 PM](https://user-images.githubusercontent.com/3678906/174308065-faef9688-4674-400b-9a42-374a3f3fcffb.png)

 



# Login With Unstoppable, coinbase wallet, Wallet connect , Metamask
![Screenshot 2022-06-17 at 7 02 28 PM](https://user-images.githubusercontent.com/3678906/174308574-ebb547ce-0637-41d4-8d1e-d9235e27e907.png)

 
# Crypto Payment  

![Screenshot 2022-06-17 at 6 58 53 PM](https://user-images.githubusercontent.com/3678906/174308119-1bdeec27-5323-43f9-aa19-77105817ab0a.png)

# Smart Contract event Notifications 
 
![Screenshot 2022-06-17 at 7 02 12 PM](https://user-images.githubusercontent.com/3678906/174308524-d7049d51-e4dc-4c0b-af5e-0768d159e35a.png)

# Invoice  
![Screenshot 2022-06-17 at 6 59 12 PM](https://user-images.githubusercontent.com/3678906/174308311-850e0eb7-d6c6-4230-8635-33658b2068e3.png)

# Invoice Details 
![Screenshot 2022-06-17 at 6 59 23 PM](https://user-images.githubusercontent.com/3678906/174308331-b5bfbb27-630d-4cac-8a43-c2e46b8bbeeb.png)







