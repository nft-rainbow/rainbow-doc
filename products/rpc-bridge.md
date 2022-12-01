RPC-Bridge
=============

## 简介

Conflux 是一个采用创新树图结构的高性能公链，但其原生空间（Core Space）的 RPC，与以太坊不兼容，有一组专有的 RPC 方法组成，并且账户地址格式也不同。由此导致以太坊生态的大部分开发工具，SDK，服务无法直接使用，大大增加的开发者学习成本，及项目迁移成本。为解决此问题 [Conflux RPC Bridge](https://github.com/conflux-fans/rpc-bridge) 服务应用而生，该服务可将 Conflux 的大部分方法映射为以太坊的 RPC 方法，最终目标是使得开发者可以直接使用以太坊的开发工具，SDK，服务，而无需修改代码。

## Rainbow RPC Bridge Service

NFTRainbow 使用开源代码，搭建了一个公共的 RPC Bridge 服务，供开发者使用。该服务的地址为：

| 网络 | Chain ID | 地址  |
|---|---|---|
| 主网  | 1029  | https://cfx2eth.nftrainbow.cn  |
|  测试网 | 1 |  https://cfx2ethtest.nftrainbow.cn |

## 兼容性

目前该服务实现了以太坊核心 RPC 方法的适配，但并不完全兼容，具体兼容性查看 [RPC-bridge 服务兼容性介绍](https://github.com/conflux-fans/rpc-bridge#methods)

### 地址说明

Conflux 使用 base32 编码的地址，而以太坊使用 hex40 地址，两者可以互相转换，Conflux 各语言的 SDK 都提供了地址转换的方法，ConfluxScan 也提供了[地址转换的页面工具](https://confluxscan.net/address-converter)。

另外需要注意的是 Conflux 地址转换为 hex40 格式后，前缀只有 `0x1`, `0x8` 两种，其他前缀的地址都不是 Conflux 合法地址。使用 RPC Bridge 服务接受资产时，一定要注意地址的前缀，确定是合法有效地址。

通过私钥计算地址时，请使用 Conflux 的 SDK，以太坊生态 SDK 或工具生成的地址，可能不是 Conflux 的合法地址。

### eth_sendRawTransaction

RPC Bridge 服务，直接将 `eth_sendRawTransaction` 方法适配为了 `cfx_sendRawTransaction`。但 [Conflux Core 的交易字段与编码签名算法](https://developer.confluxnetwork.org/sending-tx/en/transaction_explain)与以太坊不同，因此以太坊原生 SDK，工具，钱包构造的交易无法使用本服务发送。需要配合 Conflux 定制化的相关签名模块使用。

## 使用场景

### 使用 TheGraph 服务索引 Conflux Core 数据

TheGraph 是一个开源以太坊链上数据索引服务和工具。目前 RPC-Bridge 支持 使用 graph-node 索引 Conflux Core 合约数据：

1. 需要自建 graph-node 服务，并将 ethereum RPC 配置为 RPC Bridge 服务地址。
2. 将 Conflux Core 合约地址转换为 hex40 格式，修改子图 subgraph.yaml 文件中的合约地址。

### 使用 web3.py|brownie + conflux-web3py-signer 与 Core 交互

[conflux-web3py-signer](https://github.com/conflux-fans/conflux-web3py-signer) 是一个专门为 web3.py 开发的 Conflux 交易签名插件，与 web3.py 或 brownie 配合使用，可通过 RPC Bridge 服务与 Conflux Core 交互。

### web3.js

RPC Bridge 服务可支持 web3.js 读取 Conflux Core 数据，但无法使用 web3.js 发送交易。交易的发送同样需要使用 Conflux 定制化的签名插件，目前开发中。

### ethers.js

RPC Bridge 服务可支持 ethers.js 读取 Conflux Core 数据，但无法使用 web3.js 发送交易。交易的发送同样需要使用 Conflux 定制化的签名插件，目前开发中。

### truffle

理论上 truffle 配合 Conflux 专门的交易签名模块，通过 RPC Bridge 服务也可进行 Conflux Core 的合约应用开发。目前开发中。

## FAQs

### 该服务能直接添加到 MetaMask 网络中么？

不行，因为 Conflux Core 的交易签名算法与以太坊不同，MetaMask 无法直接使用。

### 该服务收费么？

目前不收费，免费对外提供，但是后续可能会收费。