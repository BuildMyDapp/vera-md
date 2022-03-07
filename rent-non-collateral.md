Rinkeby Contract address: 0x2401267f70dcDDEB90e525eb161D5C692b5d746B

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


- ### rentNFT (4 parameters):
nftAddresses[],
tokenIds[],
leasingIds[],
rentDurations[]

- ### cancelLeasing (3 parameters):
nftAddresses[],
tokenIds[],
leasingIds[]
    
- ### endRent (3 parameters):
nftAddresses[],
tokenIds[],
leasingIds[]


- ### setRentFee (1 parameters):
rentFee

- ### setBeneficiary (1 parameters):
newBeneficiaryAddress

# Web3 sample code

# Read Functions


 
 
 



# Write Functions

- ### lease
```
let receipt = await contract.methods.lease(token_addresses,token_ids,durations,dailyprices,paymentTypes).send({ from: accounts[0] });
```

- ### rentNFT
```
let receipt = await contract.methods.rentNFT(token_addresses, token_ids, leasingIds, rentDurations).send({ from: accounts[0] });
```
- ### cancelLeasing
```
let receipt = await contract.methods.cancelLeasing(token_addresses, token_ids, leasingIds).send({ from: accounts[0] });
```

- ### endRent 
```
let receipt = await contract.methods.endRent(token_addresses, token_ids, leasingIds).send({ from: accounts[0] });
```
