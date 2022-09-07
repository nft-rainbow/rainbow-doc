铸造NFT快速指南
======================

欢迎来到 NFTRainbow，使用我们的NFTRainbow-API, 您将可以在2分钟之内免费将任意文件铸造成为NFT，而且可以在多种区块链上进行。

本文将包含如下内容
----------------------
  - [为什么使用 NFTRainbow-API](#为什么使用-nftrainbow-api)
  - [NFTRainbow-API 能做什么](#nftrainbow-api-能做什么)
  - [准备工作](#准备工作)
  - [简单铸造 NFT](#简单铸造-nft)
  - [定制化铸造 NFT](#定制化铸造-nft)
  - [设置代付](#设置代付)

为什么使用 NFTRainbow-API
----------------------
1. 区块链技术栈很复杂，通常实现铸造和查询NFT需要掌握区块链相关知识，包括 Solidity、Web3.js、GraphQL、节点、IPFS、数据密集型应用程序等，学习曲线陡峭且需要大量时间，通常需要一个团队来涵盖所有技能。
2. 基础设施的建立和维护成本昂贵且耗时，通常团队的50%的工作量会花费在这上面，如果支持多种区块链则会让难度成倍上升。
3. 运行自己的节点很昂贵，使用第三方节点服务则受限于服务的可靠性和安全性。
4. 时间是宝贵的，当有一个商业机会时是否能抢在对手前面将影响整个项目的成败。

使用 NFTRainbow-API 将可以避免以上问题，让web2开发者无门槛使用，不需要学习web3技术栈，极大降低成本，提高开发效率。

NFTRainbow-API 能做什么
----------------------
可以将任何文件（通常是图片或视频），通过Web API的方式铸造成为NFT，比如艺术品或者数字收藏品，或者您能想到的任何可视化的东西。

这意味着您可以：
- 快速铸造 NFT 将其发布到区块链网络
- 无需学习智能合约开发即可测试新的 NFT 产品创意
- 在您的应用程序中通过调用 NFTRainbow-API 自动铸造 NFT
- 向指定用户钱包地址铸造 NFT 来宣传您的 NFT项目，比如向 CryptoPunk 或者 Bored Ape Yacht Club 拥有者地址铸造 NFT

NFTRainbow-API 提供了两种方式来铸造NFT
- [简单铸造](#简单铸造-nft)
- [定制化铸造](#定制化铸造-nft)

准备工作
----------------------
铸造NFT之前，您需要
1. [注册 NFTRainbow 账户](https://dev.nftrainbow.xyz/login)
2. [创建应用，应用通常对应一个产品](https://dev.nftrainbow.xyz/panels/apps)
3. 从[应用列表](https://dev.nftrainbow.xyz/panels/apps)进入刚创建的应用，点击“查看AppKey”，获取AppKey
4. [登录应用，获取JWT Token](https://docs.nftrainbow.xyz/api-reference/open-api/login#app-login)，下面的API将都需要使用该Token做身份验证

简单铸造 NFT
----------------------
简单铸造NFT，就是用最简单的方式来铸造NFT，您只需要提供
- NFT 名称
- NFT 描述
- NFT 文件 或 NFT 文件 URL；NFT 文件可以是任意类型的文件，包括 图片、音频、视频、文本、PDF、二进制文件等。通常艺术品类NFT都是使用图片、音频或视频文件。
- NFT 铸造目标链
- NFT 铸造目标地址

然后使用 [easymint-file](https://docs.nftrainbow.xyz/api-reference/open-api/mints#mint-nft-with-file) 或 [easymint-url](https://docs.nftrainbow.xyz/api-reference/open-api/mints#mint-nft-with-metadata) 铸造NFT即可。

当简单铸造 NFT 时，背后做了如下工作
1. 上传文件到存储服务器生成文件URL
2. 创建 NFT Metadata 文件并生成 Metadata URI
3. 调用 Easy mint NFT 合约铸造NFT

恭喜！您的第一个NFT铸造成功！

定制化铸造 NFT
----------------------
我们也提供了定制化方式铸造NFT，与简易铸造不同的是定制化铸造方式支持部署自己的NFT智能合约，在指定合约上铸币，并设置自定义的Metadata URI， 步骤如下：
1. 使用[部署API](https://docs.nftrainbow.xyz/api-reference/open-api/contract#deploy-contract)来部署一个单独的的合约
2. [创建自定义 Metadata 文件并上传](https://docs.nftrainbow.xyz/api-reference/open-api/metadata#create-nft-metadata)得到Metadata URI
3. 使用[定制化铸造NFT](https://docs.nftrainbow.xyz/api-reference/open-api/mints#mint-nft)铸造NFT，您需要提供
   - NFT 名称
   - NFT 描述
   - NFT Metadata URI
   - NFT 智能合约地址
   - NFT 铸造目标链
   - NFT 铸造目标地址

设置代付
----------------------
其中有的区块链支持代付机制，代付指由代付方支付合约调用所花费的gas，合约调用方不需要付费。所以代付使您可以完全免费的去铸造NFT，铸造花费的gas将由代付方来支付。

当前支持代付的网络有conflux
- 使用 conflux test 网络时，可以通过[代付API](https://docs.nftrainbow.xyz/api-reference/open-api/contract#set-sponsor)或 [confluxscan](https://testnet.confluxscan.io/sponsor) 来申请代付
- 使用 conflux 网络时，您可以通过 [confluxscan](https://confluxscan.io/sponsor) 申请代付，当有大额需求时请联系 conflux 官方。