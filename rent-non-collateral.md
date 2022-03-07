Rinkeby Contract address: 0x2401267f70dcDDEB90e525eb161D5C692b5d746B

## Call functions

- ### getLeasing (3 parameters):
nftAddress,
tokenId,
leaseId
    
- ### getRenting (3 parameters):
nftAddress,
tokenId,
leaseId,

- ### getLeasingId (no parameter):

- ### rentFee (no parameter):


## Write functions

- ### cancelLeasing (3 parameters):
nftAddresses[],
tokenIds[],
leasingIds[]
    
- ### endRent (3 parameters):
nftAddresses[],
tokenIds[],
leasingIds[]


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

- ### setRentFee (1 parameters):
rentFee

- ### setBeneficiary (1 parameters):
newBeneficiaryAddress

# Web3 sample code

- ### getLeasing
```
let leasing = await contract.methods.getLeasing(nftAddress, tokenId, leaseId).call();
 ```
 
 - ### getLeasingId
```
let leasingId = await contract.methods.getleasingId().call();
```
