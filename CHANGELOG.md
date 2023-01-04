# CHANGELOG

## 2023.1.1

1. 接入微信支付
2. 正式开启服务商用
3. 控制台增加自助代付设置功能

## 2022.8.24

拓展 API 接口和合约能力：

### 合约功能扩展

1. 支持 ERC-2981
2. 合约支持可配置：burn，transfer
3. 支持 NFT metadata 可更新
4. 采用 Minimal proxy 模式，优化 NFT Factory 合约

### API

1. 增加 Contract，NFT 详情接口
2. 增加支持 NFT 转移接口
3. 增加 NFT 批量铸造，转移接口

### DiscorBot

基于 NFTRainbow 服务开发一款 [DiscordBot](https://github.com/nft-rainbow/discordBot)，可用于社区 NFT 空投，抽奖等活动，方便社区运营者，提高社区活跃度。

未来该机器人会不断扩展功能，支持活动规则自定义；优化使用体验；拓展适用平台，包括 Telegram，DoDo，Fanbook 等。

## 2022.8.1

完成核心功能开发上线，包括：

1. 实现 NFTRainbow 基础功能：EasyMint，合约部署，资源托管，自定义 Mint，数据查询等 API
2. 核心模块交易上链模块，支持树图链
3. 控制台管理端开发

## 2022.9.6

1. 修改了metadata, transfers, mints的response与parameters的字段
2. 将transfer改为了transfers