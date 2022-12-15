# 树图Contract Sponsor

在像以太坊与Conflux这样的公链中，用户与合约的交互当中，`gas`是避不开的一个问题。该机制为网络对抗DoS攻击等问题提供了保障。然而，该机制也提高了用户理解与合约交互的门槛，从而在一定程度上为项目方推进项目设置了障碍。若是存在项目方为用户与合约进行交互买单的行为，web2用户接触将更加容易接触web3项目，这将为项目方推进web3项目提供便利。

Conflux的gas机制与以太坊或绝大部分的公链基本一致，合约的部署与调用都是需要去消耗`gas`（燃气费），EVM中的每一次操作都是需要`gas`作为燃料来推动的，合约越复杂，所需要的gas也越高。用户可以对gasPrice进行配置，从而可以让自己的交易更快被打包。用户对gasLimit的配置也可以防止合约陷入死循环或是发生一些其他的异常情况。用户支付gas费所支付的费用，将被分配给矿工。

在Conflux中引入了[Collateral for storage（简称CFS）机制](https://segmentfault.com/a/1190000041282025), 作为使用存储的定价方式，相比Ethereum中的一次性存储费用，CFS机制会更加公平合理。这种机制需要锁定一笔资金，作为占用存储空间的抵押物。在相应的存储空间被释放或被他人覆盖前，抵押物都会被锁定，而被锁定的抵押物所产生的相应利息会直接分配给矿工，用于存储空间的维护。因此，Conflux的存储成本也取决于空间占用的时间长短。

Conflux中的`SponsorWhitelistControl`内置合约为合约的代付提供了可能。基于该内置合约，若项目方是合约的admin，他只需完成以下的步骤，则可以为自己的合约设置代付：

1. 项目方需要为合约的gas与collateral代付进行配置，该配置包括对应的代付的上限与用于代付的代币数量。
2. 项目方将允许代付的用户加入sponsor白名单。若是希望任何用户都可以调用该合约的话，则需要将零地址（0x0000000000000000000000000000000000000000）加入该白名单当中。
3. 若是项目方为合约代付寄存的代币不够了，需要及时补充。

{% hint style="info" %}
设置代付时，gas 代付的金额需要大于等于代付的上限 \* 1000
{% endhint %}

项目方只需通过为该合约进行设置代付，代付白名单中的用户在调用该合约时，可以不消耗自己的代币实现与合约的交互。

{% embed url="https://developer.confluxnetwork.org/conflux-rust/internal_contract/internal_contract/#sponsorwhitelistcontrol-contract" %}

## FAQs

### 哪一些角色可以去对合约的白名单或是赞助进行配置呢？

设置赞助不设要求，白名单需要合约的admin去进行配置

### 如何去换合约的赞助方呢？

更换合约的赞助方需要调用`setSponsorForGas(address contractAddr, uint upperBound)`

另外需要注意的是：

* 向`SponsorWhitelistControl` 合约转账的金额需要比当前的`sponsor_balance_for_gas` 高
* 新的gas上限需要大于等于旧的gas上限，除非旧的gas上限不够去调用合约
* 向`SponsorWhitelistControl` 合约，新转账的金额需要大于等于limit的1000倍
