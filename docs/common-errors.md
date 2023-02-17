# Common Errors

## Mint 操作失败常见错误及原因

Rainbow 控制台铸造列表和 OpenAPI mints 列表接口均可以看到铸造的状态，如果失败的话，可以看到失败原因。以下是 NFT 铸造时可能遇到的一些错误，及原因，同时给出了可能的解决方法。

### NotEnoughCash

#### 错误详情

```text
estimate error: Can not estimate: transaction execution failed, all gas will be charged (
execution error: NotEnoughCash { required: 625000000000000000, got: 0, actual_gas_cost: 0, max_storage_limit_cost: 625000000000000000 }), 
data: NotEnoughCash { required: 625000000000000000, got: 0, actual_gas_cost: 0, max_storage_limit_cost: 625000000000000000 }
```

#### 原因及解决方法

此错误产生，是因为交易上链时无法支付足够的上链费用而失败。此种情况大概率是因为`合约未设置代付`，或`合约代付已用完`。

为合约设置或补充代付重新发送交易即可解决此问题。

#### 为什么合约有足够的代付，仍然铸造失败，返回此错误?

此种情况请检查:

1. 合约代付白名单是否正常打开（使用 Rainbow 部署的合约会默认打开白名单）。单独部署合约可自行检查是否打开
2. 合约燃气代付上限设置是否足够。如果交易燃气消耗较大，超过燃气代付上限，则交易不会被代付。通常批量 mint 交易所消耗燃气较大

备注：Rainbow 默认推荐设置燃气上限为 100w Gdrip，普通单 NFT 铸造燃气消耗量为  10-20w Gdrip. 如果需要进行 batch 铸造操作，建议设置一个较大的燃气上限比如 1000w Gdrip.

### ERC721: token already minted

#### 错误详情

```text
estimate error: Estimation isn't accurate: transaction is reverted: ERC721: token already minted.
 Innermost error is at CFX:TYPE.CONTRACT:ACA0P90602FKGS7CVRJ5AGS8830GT7P63PSMJ7G0NU: Vm reverted. 
 ERC721: token already minted., data: CFX:TYPE.CONTRACT:ACA0P90602FKGS7CVRJ5AGS8830GT7P63PSMJ7G0NU: Vm reverted. 
 ERC721: token already minted CFX:TYPE.CONTRACT:ACGVX1PDSWDZGKNTGRG0DV49XS2AC0B8RU06696HX1: Vm reverted. ERC721: token already minted
```

#### 原因及解决方法

在 721 类型合约中，一个 tokenId 只能进行一次铸造操作，如果某个 tokenId 重复进行铸造操作，则会失败，返回此错误。

在铸造 721 NFT 时，只需自行控制好 tokenId 不重复使用，即可避免此问题

### xxx discarded due to out of balance

#### 错误详情

```text
Invalid parameters: tx, data: "Transaction 0xdaba3ea56331e16e45fa0574d43072a76d7da43c473aa7be7a12649214d74ba3 is 
discarded due to out of balance, needs 13760882000000000 but account balance is 0"
```

#### 原因及解决方法

此错误亦是因为交易上链时无法支付足够的上链费用，在发送到区块链节点交易池时失败了。确切一点的话此错误最有可能是`交易的燃气消耗超过了合约燃气上限`。通常在 batch 铸造操作中可能会遇到此错误。

可通过提高合约燃气代付上限来解决此问题

### xxx exceeds the maximum value 15000000, the half of pivot block gas limit

#### 错误详情

```text
Invalid parameters: tx, data: "transaction gas 20436888 
exceeds the maximum value 15000000, the half of pivot block gas limit"
```

#### 原因及解决方法

在 Conflux 树图链，单笔交易允许的燃气用量为 1500w，如果超过则会报此错误。

降低交易燃气用量即可解决此错误，如果是在进行 batch 铸造操作，可降低 batch 铸造的 NFT 数量。如果合约燃气上限设置为 1000w，单次 batch 铸造量建议为 50

### AccessControl

#### 错误详情

```text
error: estimate error: Estimation isn't accurate: transaction is reverted: AccessControl: 
account 0x1d6a8330ef25759f92a02d0bf.... Innermost error is at CFXTEST:TYPE.CONTRACT:ACB7UNP488HY4PWC7TAHGMPKXRGKW7XS465P8G9C3U: 
Vm reverted. AccessControl: account 0x1d6a8330ef25759f92a02d0bf...., data: CFXTEST:TYPE.CONTRACT:ACB7UNP488HY4PWC7TAHGMPKXRGKW7XS465P8G9C3U: 
Vm reverted. AccessControl: account 0x1d6a8330ef25759f92a02d0bf...
```

#### 原因及解决方法

此错误表示交易发送方，没有铸造 NFT 的权限。通常此错误是因为合约部署时`没有打开管理员转移权限`，或者调用铸造接口时，`使用了错误的项目 appId&appSecret` （项目跟合约不匹配）。

此时检查合约设置，或 appId 与合约的对应关系，调整即可.

### NFT: URI different with previous

#### 错误详情

```text
error: estimate error: Estimation isn't accurate: transaction is reverted: 
NFT: URI different with previous. Innermost error is at CFX:TYPE.CONTRACT:ACA0E92WW1PPWJFWEYHVXBUEKRU16JNUKPE0EWSG0B: 
Vm reverted. NFT: URI different with previous., data: CFX:TYPE.CONTRACT:ACA0E92WW1PPWJFWEYHVXBUEKRU16JNUKPE0EWSG0B: 
Vm reverted. NFT: URI different with previous CFX:TYPE.CONTRACT:ACBHEEV04431G3HUPU18BW57K8E5K8TM26PGBV6S0Y: 
Vm reverted. NFT: URI different with previous
```

#### 原因及解决方法

此错误表示在铸造 NFT 时，NFT 的 Token `URI` 与之前的不一致，1155 NFT 单个 tokenId 可铸造多个（多次），但要求多次铸造时必须使用相同的 token_uri，否则会报此错误。

### ERC1155: transfer to non ERC1155Receiver implement

#### 错误详情

```text
error: estimate error: Estimation isn't accurate: transaction is reverted: ERC1155: transfer to non ERC1155Receiver implement.... 
Innermost error is at CFXTEST:TYPE.CONTRACT:ACDT6158XGRMEMPRMFFJN4DA5VRKH5M9CESGWBJK8Y: Vm reverted. ., 
data: CFXTEST:TYPE.CONTRACT:ACDT6158XGRMEMPRMFFJN4DA5VRKH5M9CESGWBJK8Y: Vm reverted.
CFXTEST:TYPE.CONTRACT:ACAKSW1DP0PK9R8N9ECRD0FR9ZAZKKTTB6TXJ1GKH1: Vm reverted.
CFXTEST:TYPE.CONTRACT:ACDT6158XGRMEMPRMFFJN4DA5VRKH5M9CESGWBJK8Y: Vm reverted. ERC1155: transfer to non ERC1155Receiver implement...
CFXTEST:TYPE.CONTRACT:ACAKSW1DP0PK9R8N9ECRD0FR9ZAZKKTTB6TXJ1GKH1: Vm reverted. ERC1155: transfer to non ERC1155Receiver implement...
```

#### 原因及解决方法

此错误表示在 NFT 铸造或转移时，`接收方`是一个合约地址，但没有实现 ERC1155Receiver 接口，即没有 `onERC1155Received` 函数。

此时更换接受地址即可。

### xxx discarded due to a too stale nonce

#### 错误详情

```text
error: Invalid parameters: tx, data: "Transaction 0x484dfc2fc6716833cc13b5903a0b12b0521769821a420afc6cecfd738e261772 is 
discarded due to a too stale nonce"
```

#### 原因及解决方法

此错误表示由于某种原因，发送交易所使用的 nonce 已经过期，需要重新获取 nonce 后再次发送交易。

### block_number is missing for best_hash

#### 错误详情

```text
error: failed to bulk fetch chain infos: Error processing request: block_number is missing for best_hash, data: <nil>
```

#### 原因及解决方法

此错误为偶发性错误，一般为网络问题导致，可稍后重试。

