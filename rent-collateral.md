

# What is Vera RentNFT

RentNFT is an smart contract for ERC-721 and ERC-1155 leasing and renting. Users can lease the NFT and earn rent on them. The main contract of rentNFT is contracts/vRent. This contract allows users to lease ERC-721 and ERC-1155 NFTs in one single transaction.

# Instructions
- To interact with the contract functions [web3](https://github.com/ChainSafe/web3.js) & [smart contract](https://www.ibm.com/topics/smart-contracts) should be loaded

## Integration Steps

![image](https://user-images.githubusercontent.com/38735197/162038147-5e18ace0-9fae-437e-b0ec-97dfc1e5cdf6.png)


## Step 1 
### Web3 function 
 to lease the NFT we have `lease` function in smartcontract where we need to pass 5 given parameters
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
after leasing NFT we need to get leasing id to for our off-chain data
**getLeasingId (no parameter)** returns leasing id 
```
let leasingId = await contract.methods.getleasingId().call();
```
to save NFT off-chain data we need these required parameters
API Body JSON
 ### Note: this off-chain data parameters are required as per platform requirments, because this data is saving on off-chain so it does not have any relation with smart contract
 ```  {
          owner_address: user_address,
          lend_id, //get from getLeasingId function 
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
          nft: { //NFT metadata
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
```

## Step 2 
to stop lending we have `cancelLeasing` function in smartcontract


- ### cancelLeasing (3 parameters):
```nftAddresses[]```,
```tokenIds[]```,
```leasingIds[]```
 ```
let receipt = await contract.methods.cancelLeasing(token_addresses, token_ids, leasingIds).send({ from: accounts[0] });
```

## Call functions



- ### rentFee (no parameter):
```
let rentFee = await contract.methods.rentFee().call();
```

## Write functions



- ### rentNFT (4 parameters):
```nftAddresses[]```,
```tokenIds[] ```,
```leasingIds[] ```,
```rentDurations[] ```
```
let receipt = await contract.methods.rentNFT(token_addresses, token_ids, leasingIds, rentDurations).send({ from: accounts[0] });
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


