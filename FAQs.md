# FAQs

## 目前 NFTRainbow 支持哪些链?

* 树图链

将来计划会支持：

* 主流EVM 兼容链

## 如何获取访问 API 的 AppSecret ？

注册 [NFTRainbow 平台账号](https://console.nftrainbow.xyz/)，并填写用户实名信息，官方审核通过后，可创建自己的应用，从应用详情管理页面获取 AppId 和 AppSecret。

## AppId, AppSecret 调用登录接口失败？

返回错误 ”KYC required“, 是因为未填写实名信息，填写完成通过审核后才可能访问接口。

## 如何收费的？

收费规则[参看详情](./docs/price.md)

## 树图链如何给合约设置代付？

在 NFTRainbow 控制台，`智能合约页面` 有树图代付设置入口，该功能可用于给合约设置代付，测试网免费设置，主网需要按量收取费用

## 为什么 Mint 接口调用后，接口返回的数据中没有 tokenId，哈希等信息？

当前 NFTRainbow 所有的上链操作都是异步进行的，接口调用后无法立刻获取 tokenId，可使用 Mint 详情接口，查看藏品铸造状态。
成功上链后可以获取藏品铸造的 TokenId，哈希等信息。失败的会会返回失败的原因。

## 我是一个 Web2 平台或应用，藏品铸造时目标账号怎么获取？

目前藏品铸造地址为所选择区块链的账户地址，账户需要由应用自己创建托管，或使用托管类的钱包服务产品如 [Anyweb](https://anyweb.cc/)，当然也可以使用完全去中心化钱包账户地址。

未来 NFTRainbow 也会提供账号解决方案，届时将可直接使用手机号邮箱等作为接受账号。

## NFTRainbow 的产品资源是存放于什么地方？

我们提供多种存储方式选择比如：云对象存储服务，云服务器，IPFS 等，用户可根据自己的产品或应用选择。

## 自定义 Mint 功能，mint 的 token id 为什么不连续？

CustomMint 接口，支持参数指定 tokenId，若不指定则会随机生成；接口调用方可根据自身需求控制 tokenId 自增，从而实现连续。

## NFT 支持的文件格式有哪些？

目前支持 图片，视频，音频 三大类文件，具体支持的格式如下：

* 图片：.ico .svg .tif .tiff .jpg, .jpeg, .png, .gif, .bmp, .webp
* 视频：.mp4, .avi .mpeg .ogv .ts .webm .3gp .2gp
* 音频：.aac .mid .midi .mp3 .oga .opus .wav .weba .cda

## Easy Mint 跟自定义 Mint 的区别？

Easy mint 主要作用是方便 Rainbow 用户快速体验铸造功能，直接使用事先部署好的合约进行铸造。此种方式用户无需部署合约，因此操作比较简单。`但此种方式铸造的 NFT 无法通过转移接口转移`。

自定义 Mint 是用户自己部署合约，然后使用自定义 Mint 接口进行铸造。此种方式用户需要部署合约，因此操作比较复杂。但此种方式铸造的 NFT 可以通过转移接口转移。

## ERC721 和 ERC1155 的区别？

ERC721 是最初的 NFT 标准，每个 NFT 都是唯一，不可替代的。每个 NFT 都有唯一的 tokenId，且只有一个，不可分割。

ERC1155 是多代币标准，一个合约中可以有多种 NFT，每种 NFT 可以有多个。TokenId 相同的 NFT 之间是等价的。

## 文件上传的大小限制？

目前文件大小限制为 10M