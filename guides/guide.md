Rainbow-NFT-API guide
=====================

Rainbow-NFT is a project for web2 developer to quickly create NFT contracts and mint nfts through Rainbow-NFT-API. It helps you imporve efficient and resouce. Beacause:
1. You need not to learn about blockchain, contracts, wallets and so on.
2. You need not to run blockchain nodes.
3. You need not to maintain database.

So, let's begin!

Register
--------------------
Firstly, user need [register](Regsiter) an account.
```sh
curl --location --request POST 'http://localhost:8080/dashboard/register' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email": "test@email.com",
    "password": "psd"
}'
```

Login
--------------------
Then, [login](Login) with your email and password
```sh
curl --location --request POST 'http://localhost:8080/dashboard/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email": "test@email.com",
    "password": "psd"
}'
```

the API will return the JWT token for authentication account
```json
{
    "code": 0,
    "data": {
        "expire": "2022-07-26T18:43:22.268354+08:00",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NTg4MzIyMDIsImp3dF91aWQiOjQsIm9yaWdfaWF0IjoxNjU4ODI4NjAyfQ.UjFDSO_PYE-JHqXX5HT_r5h0x7KgMrJhmwBTn-Tj67Q"
    }
}
```

the JWT token will be expired in 1 hour, please refresh token in 1 hour

### Refresh Token


```sh
curl --location --request GET 'http://localhost:8080/dashboard/refresh_token' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NTg4MzIyMDIsImp3dF91aWQiOjQsIm9yaWdfaWF0IjoxNjU4ODI4NjAyfQ.UjFDSO_PYE-JHqXX5HT_r5h0x7KgMrJhmwBTn-Tj67Q'
```

KYC
--------------------
User need KYC to enable accessing permissions of nft operate APIs

```sh
curl --location --request POST 'http://localhost:8080/dashboard/users/kyc' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NTg4MzMzNDgsImp3dF91aWQiOjQsIm9yaWdfaWF0IjoxNjU4ODI5NzQ4fQ.INv6XenVrad5kUforxBNZ6g31l0bA5Qx3KT2U0RPHkA' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id_name": "name_kyc",
    "id_no": "1",
    "id_image": "image_kyc"
}'
```

We will check KYC manually currently, after KYC pass, user will have accessing persmission of NFT operate APIs.


Create Application
--------------------
Once verified, you’ll need to create projects and will return API-KEY for authenticate your requests for your application.

```sh
curl --location --request POST 'http://localhost:8080/dashboard/apps' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NTg4MzMzNDgsImp3dF91aWQiOjQsIm9yaWdfaWF0IjoxNjU4ODI5NzQ4fQ.INv6XenVrad5kUforxBNZ6g31l0bA5Qx3KT2U0RPHkA' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chain":"conflux_test",
    "name": "app1",
    "intro": "app1111"
}'

```

the field `app_id` and `app_secret` of response is the API-KEY for authentication of using NFT operate APIs.
```json
{
    "code": 0,
    "data": {
        "id": 4,
        "created_at": "2022-07-26T18:51:04.352+08:00",
        "updated_at": "2022-07-26T18:51:04.352+08:00",
        "deleted_at": null,
        "chain_type": 1,
        "app_id": "oyXa5lcc",
        "app_secret": "7uy8nKs3xxBSXjDb",
        "name": "app1",
        "intro": "app1111",
        "user_id": 4
    }
}
```

Mints
--------------------
Before use NFT operate APIs, user should login by API-KEY to authenticate application

### Login API-KEY
```sh
curl --location --request POST 'http://localhost:8080/v1/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "app_id": "oyXa5lcc",
    "app_secret": "7uy8nKs3xxBSXjDb"
}'
```

the API will return the JWT token for authentication application

```json
{
    "code": 0,
    "data": {
        "expire": "2022-08-25T18:55:07.420368+08:00",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjE0MjQ5MDcsImp3dF91aWQiOjQsIm9yaWdfaWF0IjoxNjU4ODMyOTA3fQ.cRhk7aOcei8eWHO9156gMzjG-azYpuK7abDlccLcHxs"
    }
}
```

the JWT token will be expired in 1 hour, please refresh token in 1 hour

### Easy mint

We provide an easy way to mint NFT by our EASY-MINT contracts, And user could specify `chain` which means block chain type , nft `name`, nft `description`, `mint_to_address` for speicify nft receiver address.

We provide two APIs for easy minting, one is easy mint with uploading file to be NFT image.
#### Easy mint with file
```sh
curl --location --request POST 'http://localhost:8080/v1/mints/easy/files' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjEzMzg1MDQsImp3dF91aWQiOjMsIm9yaWdfaWF0IjoxNjU4NzQ2NTA0fQ.NxLKZoqnWkrtew6CFHwho4WhbWIxlFAgLY7sVAF055w' \
--form 'file=@"/Users/dayong/Desktop/throll.png"' \
--form 'chain="conflux_test"' \
--form 'name="throll"' \
--form 'description="throll description"' \
--form 'mint_to_address="cfxtest:aatk708nbb7573bkwumsu00h0r1rtkcdz2chwhttzk"'
```

The response is the minted NFT information. Please query mint status by [Query mint](#query-mint)

#### Easy mint with URL
Another is mint with specifying image URL.
```sh
curl --location --request POST 'http://localhost:8080/v1/mints/easy/urls' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjEzMzg1MDQsImp3dF91aWQiOjMsIm9yaWdfaWF0IjoxNjU4NzQ2NTA0fQ.NxLKZoqnWkrtew6CFHwho4WhbWIxlFAgLY7sVAF055w' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chain": "conflux_test",
    "name": "123",
    "description": "123",
    "mint_to_address": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
    "file_url": "https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png"
}'
```

### Query mint
After mint, user could query mint status
```sh
curl --location --request GET 'http://localhost:8080/v1/mints?page=1&limit=10' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjEzMzg1MDQsImp3dF91aWQiOjMsIm9yaWdfaWF0IjoxNjU4NzQ2NTA0fQ.NxLKZoqnWkrtew6CFHwho4WhbWIxlFAgLY7sVAF055w'
```
The fields `status` of response could speicify if mint success, `1` represnets success and others failed. If failed, the fields `error` is the error reason.

### Custom mint

Custom mint allows user to deploy a indepent NFT contract and custom mint NFT by specifing contract address and tokenURI.

#### Deploy Custom NFT Contract
If you have not deployed a custom NFT contract, deploy one as follow.
```sh
curl --location --request POST 'http://localhost:8080/v1/contracts' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjEzMzg1MDQsImp3dF91aWQiOjMsIm9yaWdfaWF0IjoxNjU4NzQ2NTA0fQ.NxLKZoqnWkrtew6CFHwho4WhbWIxlFAgLY7sVAF055w' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chain": "conflux_test",
    "name": "NFT-name",
    "symbol": "ENFT",
    "owner_address": "cfxtest:aatk708nbb7573bkwumsu00h0r1rtkcdz2chwhttzk",
    "type": "erc721",
    "base_uri": ""
}'
```

The response is the deployed NFT contract information. Please query mint status by [Query contract](#query-contract)
#### Query Contract
After deployed, you could query deploy status
```sh
curl --location --request GET 'http://localhost:8080/v1/contracts?page=1&limit=10' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjEzMzg1MDQsImp3dF91aWQiOjMsIm9yaWdfaWF0IjoxNjU4NzQ2NTA0fQ.NxLKZoqnWkrtew6CFHwho4WhbWIxlFAgLY7sVAF055w'
```
The fields `status` of response could speicify if deployed success, `1` represnets success and others failed. If sucess, the field `address` is the contract address deployed. If failed, the fields `error` is the error reason.

#### Custom mint

After deployed custom NFT contract, you can custom mint as follow.
If you don't have a metadata uri online, you could create one by [create metadata](#create-metadata)

```sh
curl --location --request POST 'http://localhost:8080/v1/mints' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjEzMzg1MDQsImp3dF91aWQiOjMsIm9yaWdfaWF0IjoxNjU4NzQ2NTA0fQ.NxLKZoqnWkrtew6CFHwho4WhbWIxlFAgLY7sVAF055w' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chain": "conflux_test",
    "name": "123",
    "description": "123",
    "mint_to_address": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
    "contract_address": "cfxtest:acf8m2gzrv8pnfsjbne2d28m4h2ycj569uupgys473",
    "metadata_uri": "https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png"
}'
```
The response is the minted NFT information. Please query mint status by [Query mint](#query-mint)

Metadata
--------------------
Every NFT could set metadata independently. Normally metadata is a JSON description, see details from [spec ERC721](https://eips.ethereum.org/EIPS/eip-721) and [spec ERC1155](https://eips.ethereum.org/EIPS/eip-1155)

Basicly, it includes property `Image` and `Description`.

### Upload File
So, you should set the image url, if the image is offline, you could upload the image as follow.

```sh
curl --location --request POST 'http://localhost:8080/v1/metadata/files' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjEzMzg1MDQsImp3dF91aWQiOjMsIm9yaWdfaWF0IjoxNjU4NzQ2NTA0fQ.NxLKZoqnWkrtew6CFHwho4WhbWIxlFAgLY7sVAF055w' \
--form 'file=@"/Users/dayong/Desktop/throll.png"'
```
The field `file_url` of response is the file url. You could use it be NFT image url.
```json
{
    "code": 0,
    "data": {
        "file_url": "http://localhost:8080/assets/file/3/nft/02c95850aacd060da60f6fe500ff5bb06d67663682bef8fd490dedf0a0e7b2a7.png",
        "file_size": 1954237,
        "file_type": "png",
        "file_name": "02c95850aacd060da60f6fe500ff5bb06d67663682bef8fd490dedf0a0e7b2a7"
    }
}
```

### Query File
You could query files related your application as follow.
```sh
curl --location --request GET 'http://localhost:8080/v1/metadata/files' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjEzMzg1MDQsImp3dF91aWQiOjMsIm9yaWdfaWF0IjoxNjU4NzQ2NTA0fQ.NxLKZoqnWkrtew6CFHwho4WhbWIxlFAgLY7sVAF055w'
```

### Create metadata

Then you can create metadata with image url generated above. Please refers metadata JSON schema from [spec ERC721](https://eips.ethereum.org/EIPS/eip-721) and [spec ERC1155](https://eips.ethereum.org/EIPS/eip-1155)

```sh
curl --location --request POST 'http://localhost:8080/v1/metadata/' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjEzMzg1MDQsImp3dF91aWQiOjMsIm9yaWdfaWF0IjoxNjU4NzQ2NTA0fQ.NxLKZoqnWkrtew6CFHwho4WhbWIxlFAgLY7sVAF055w' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "test", 
    "description": "this is a test metadata", 
    "external_link": "https://www.google.com/search", 
    "image": "http://localhost:8080/assets/file/3/nft/02c95850aacd060da60f6fe500ff5bb06d67663682bef8fd490dedf0a0e7b2a7.png", 
    "attributes": [
        {
            "attribute_name": "eyes", 
            "trait_type": "test trait", 
            "display_type": "", 
            "value": "big"
        }, 
        {
            "attribute_name": "mouse", 
            "trait_type": "test hey hey", 
            "display_type": "", 
            "value": "big"
        }
    ], 
}'
```

The filed `metadata_uri` of response is the generated metadata uri, which could use for [custome mints](#custom-mint-1).

```json
{
    "code": 0,
    "data": {
        "metadata_uri": "http://localhost:8080/assets/metadata/3/nft/b86b99ed6218845757ff6e7ae9a8d5f2571642379be15712a0be30027f6158e9.json"
    }
}
```

### Query metadata
After create metadata, you could query metadata as follow.
```sh
curl --location --request GET 'http://localhost:8080/v1/metadata/:metadata_id' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjEzMzg1MDQsImp3dF91aWQiOjMsIm9yaWdfaWF0IjoxNjU4NzQ2NTA0fQ.NxLKZoqnWkrtew6CFHwho4WhbWIxlFAgLY7sVAF055w'
```

### List metadata
You also could list all metadata related to current application.
```sh
curl --location --request GET 'http://localhost:8080/v1/metadata/' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjEzMzg1MDQsImp3dF91aWQiOjMsIm9yaWdfaWF0IjoxNjU4NzQ2NTA0fQ.NxLKZoqnWkrtew6CFHwho4WhbWIxlFAgLY7sVAF055w' \
--header 'Content-Type: application/x-www-form-urlencoded'
```