# Web3 Services

## 简介

NFTRainbow 致力于推动 Web3 在各行各业应用, 简化 Web3 开发流程和体验. 为此我们不止提供 NFT 铸造相关服务, 还提供了一系列 Web3 服务, 来帮助开发者快速搭建 Web3 应用. 包括:

* 区块链 RPC 服务
* 区块链数据索引服务

以上服务都同时包含 Conflux Core 空间和 eSpace 空间, 并且同时支持主网和测试网.

## RPC 服务

NFTRainbow 自研了整套的 RPC 服务基础设施. 能够提供稳定可靠的 RPC 服务, 开发者无需自己搭建节点, 从而省去巨量的运维工作, 并专心开发应用. NFTRainbow RPC 服务具有以下优势:

* 节点自动扩容, 自动升级
* 完善的数据监控, 保证数据的实时性
* 基于 IP hash 路由, 保证数据一致性

### 定价

Rainbow RPC 服务提供灵活且有竞争力的定价方案, 不仅提供免费版服务, 还提供多档可选套餐. 除此之外还提供加油包模式, 能满足多种类型客户需求.

套餐定价如下:

| 套餐 | 请求量 | QPS | 价格  |
|---|---|---|---|
| 免费套餐  | 10w 次/天 | 50 R/S  | free |
| 基础套餐  | 20w 次/天 | 100 R/S  | 100 元/月 |
| VIP套餐  | 110w 次/天 | 100 R/S  | 1000 元/月 |
| 企业套餐  | 1000w 次/天 | 500 R/S  | 5000 元/月 |

加油包定价如下:

| 加油包 | 请求量 | 价格  |
|---|---|---|
| 加油包 1  | 300w 次| 200 元  |
| 加油包 2  | 1000w 次| 500 元  |

加油包请求次数不限制使用时间.

* [Conflux Core RPC 文档](https://doc.confluxnetwork.org/docs/core/build/json-rpc/json_rpc)
* [Conflux eSpace RPC 文档](https://ethereum.org/en/developers/docs/apis/json-rpc/)

## 区块链数据索引服务

区块链数据索引服务可对区块链历史数据进行索引并提供查询服务, 例如 NFT 转移历史, 账户 NFT 资产列表等, 目前该服务接口同 Scan API 完全兼容, 方便用户迁移.

套餐定价如下:

| 套餐 | 请求量 | QPS | 价格  |
|---|---|---|---|
| 免费套餐  | 10w 次/天 | 5 R/S  | free |
| 基础套餐  | 20w 次/天 | 10 R/S  | 100 元/月 |
| VIP套餐  | 50w 次/天 | 20 R/S  | 1000 元/月 |
| 企业套餐  | 500w 次/天 | 100 R/S  | 5000 元/月 |

加油包定价如下:

| 加油包 | 请求量 | 价格  |
|---|---|---|
| 加油包 1  | 200w 次| 200 元  |
| 加油包 2  | 600w 次| 500 元  |

加油包请求次数不限制使用时间.

接口详细文档 可参看 Scan 相关文档:

* [Conflux Core Scan API](https://api.confluxscan.net/doc)
* [Conflux eSpace Scan API](https://evmapi.confluxscan.net/doc)

## FAQs

### 如何获取服务访问 url 及 key?

可在 Rainbow Console 控制台的`Web3服务页面`查看或创建应用, 每个应用会分配一个访问 Web3 Service 的 key, 在应用详情可查看此 key, 及完整的服务 url

### 如何购买服务?

在 Console 控制台 `Web3服务 -> 我的服务` 页面, 有购买服务的入口, 点击后即可进入购买页面. 在购买页面可切用户当前的服务套餐, 也可购买加油包

### 套餐升级后, 还可以降级回来么?

可以的, 可以取消自动续订功能, 套餐到期后自动切换为免费版, 也可以直接进行套餐切换操作, 切换后立刻生效, 但不会返还费用.

### 套餐的额度是多个项目共用的么?

是的

### Web3服务中的`项目列表`跟我的项目中的`项目列表`是一样的么?

是的, 两者共用一套数据, 在不用的页面查看不同的项目信息

### 关于 burst