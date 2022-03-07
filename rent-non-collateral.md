
#Instructions
- To interact with the contract functions [web3](https://github.com/ChainSafe/web3.js) & [smartcontract](https://www.ibm.com/topics/smart-contracts) should be loaded
-

## Call functions

- ### getLeasingId (no parameter):
```
let leasingId = await contract.methods.getleasingId().call();
```

- ### rentFee (no parameter):
```
let rentFee = await contract.methods.rentFee().call();
```

## Write functions

- ### lease (5 parameters):
nftAddresses[],
tokenIds[],
maxLeaseDurations[],
dailyLeasePrices[],
paymentTokens[]
```
let receipt = await contract.methods.lease(token_addresses,token_ids,durations,dailyprices,paymentTypes).send({ from: accounts[0] });
```

- ### rentNFT (4 parameters):
nftAddresses[],
tokenIds[],
leasingIds[],
rentDurations[]
```
let receipt = await contract.methods.rentNFT(token_addresses, token_ids, leasingIds, rentDurations).send({ from: accounts[0] });
```

- ### cancelLeasing (3 parameters):
nftAddresses[],
tokenIds[],
leasingIds[]
 ```
let receipt = await contract.methods.cancelLeasing(token_addresses, token_ids, leasingIds).send({ from: accounts[0] });
```
- ### endRent (3 parameters):
nftAddresses[],
tokenIds[],
leasingIds[]
```
let receipt = await contract.methods.endRent(token_addresses, token_ids, leasingIds).send({ from: accounts[0] });
```

- ### setRentFee (1 parameters):
rentFee
```
let receipt = await contract.methods.setRentFee(rentFee).send({ from: accounts[0] });
```

- ### setBeneficiary (1 parameters):
newBeneficiaryAddress
```
let receipt = await contract.methods.setRentFee(newBeneficiaryAddress).send({ from: accounts[0] });
```




