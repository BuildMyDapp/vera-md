

### What is Vera RentNFT

RentNFT is an smart contract for ERC-721 and ERC-1155 leasing and renting. Users can lease the NFT and earn rent on them. The main contract of rentNFT is contracts/vRent. This contract allows users to lease ERC-721 and ERC-1155 NFTs in one single transaction.

# Instructions
- To interact with the contract functions [web3](https://github.com/ChainSafe/web3.js) & [smart contract](https://www.ibm.com/topics/smart-contracts) should be loaded

### Integration Steps

## Step 1 
Web3 function 
- ### lease (5 parameters):
```nftAddresses[]```,
```tokenIds[]```,
```maxLeaseDurations[]```,
```dailyLeasePrices[]```,
```nftPrices[]```,
```paymentTokens[]```

```
let receipt = await contract.methods.lease(token_addresses,token_ids,durations,dailyprices,nftPrices,paymentTypes).send({ from: accounts[0] });

```
API Body JSON
   {
          owner_address: user_address,
          lend_id,
          token_id,
          token_address,
          max_duration,
          duration: duration,
          payment_type: type,
          nft_price,
          daily_rent_price,
          contract_address,
          transaction_hash,
          type,
          application_address: ContractUtility.getRentalContractAddress(protocol),
          nft: {
            description,
            name,
            image,
            token_id,
            token_address,
            token_uri
            token_standard, //it can be ERC1155 or ERC721
            permalink,
            contract_collection: {
              address: token_address,
              name: name
            }
          }
        }



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
```nftAddresses[]```,
```tokenIds[]```,
```maxLeaseDurations[]```,
```dailyLeasePrices[]```,
```nftPrices[]```,
```paymentTokens[]```

```
let receipt = await contract.methods.lease(token_addresses,token_ids,durations,dailyprices,nftPrices,paymentTypes).send({ from: accounts[0] });
```

- ### rentNFT (4 parameters):
```nftAddresses[]```,
```tokenIds[] ```,
```leasingIds[] ```,
```rentDurations[] ```
```
let receipt = await contract.methods.rentNFT(token_addresses, token_ids, leasingIds, rentDurations).send({ from: accounts[0] });
```

- ### cancelLeasing (3 parameters):
```nftAddresses[]```,
```tokenIds[]```,
```leasingIds[]```
 ```
let receipt = await contract.methods.cancelLeasing(token_addresses, token_ids, leasingIds).send({ from: accounts[0] });
```
- ### endRent (3 parameters):
```nftAddresses[]```,
```tokenIds[]```,
```leasingIds[]```
```
let receipt = await contract.methods.endRent(token_addresses, token_ids, leasingIds).send({ from: accounts[0] });
```

- ### setRentFee (1 parameters):
```rentFee```
```
let receipt = await contract.methods.setRentFee(rentFee).send({ from: accounts[0] });
```

- ### setBeneficiary (1 parameters):
```newBeneficiaryAddress```
```
let receipt = await contract.methods.setBeneficiary(newBeneficiaryAddress).send({ from: accounts[0] });
```


# Integration Steps

- contract cycle start from ``lease`` function, where user need to lease the NFT with these required parameters  ```nftAddresses[], tokenIds[], maxLeaseDurations[], dailyLeasePrices[], nftPrices[],paymentTokens[]```
- after leasing the NFT user will get leasing Id from ```getLeasingId``` function
- after leasing the NFT owner can cancel the lease by calling ```cancelLeasing``` function, with these required paramters ```nftAddresses[], tokenIds[], leasingIds[]```
- user can rent the leased nft by interacting with ```rentNFT``` function, to rent any NFT user need to provide ```getLeasingId``` of that specific nft with these requred pararmeters ```nftAddresses[] ,tokenIds[], leasingIds[], rentDurations[] ```
- after renting the NFT user can end the rent by calling the ```endRent``` function, with these required paramaters ```nftAddresses[], tokenIds[], leasingIds[]```


