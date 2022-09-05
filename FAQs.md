# FAQs

## 目前 NFTRainbow 支持哪些链?

* 树图链

将来计划会支持：

* 主流EVM 兼容链
* 主流联盟链

## 如何获取访问 API 的 AppSecret ？

注册 [NFTRainbow 平台账号](https://console.nftrainbow.xyz/)，并填写用户实名信息，官方审核通过后，可创建自己的应用，从应用详情管理页面获取 AppId 和 AppSecret。

## AppId, AppSecret 调用登录接口失败？

返回错误 ”KYC required“, 是因为未填写实名信息，填写完成通过审核后才可能访问接口。

## 如何收费的？

目前 树图链 NFT Easy mint 操作，以及合约部署都是免费的。合约部署后，需自行为合约设置代付，Mint 操作也是免费的。

## 树图链如何给合约设置代付？

树图链测试环境 NFTRainbow 提供了免费的 [Sponsor 设置接口](https://docs.nftrainbow.xyz/api-reference/open-api/contract#set-sponsor).

树图链主网需要自己获取并设置代付，也可以联系 Conflux 基金会购买。

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
