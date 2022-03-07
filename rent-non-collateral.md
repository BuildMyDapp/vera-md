Rinkeby Contract address: 0x2401267f70dcDDEB90e525eb161D5C692b5d746B
#Instructions
- to interact with the contract functions [web3](https://github.com/ChainSafe/web3.js) & smartcontract should be loaded
-

## Call functions

- ### getLeasing (3 parameters):
nftAddress,
tokenId,
leaseId
```
let leasingDetails = await contract.methods.getLeasing(nftAddress, tokenId, leaseId).call();
 ```   
 
- ### getRenting (3 parameters):
nftAddress,
tokenId,
leaseId,
 ```
 let rentingDetails = await contract.methods.getRenting(nftAddress, tokenId, leaseId).call();
 ```
 
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




