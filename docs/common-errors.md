# Common Errors

## API常见错误

1. 输入参数错误
   1.  给定参数type错误

       输入参数没有按照给定形式来，如`chain_id, chain_type, contract_type` 等
   2.  合约地址或账户地址格式错误

       输入的合约地址或账户地址没有满足base32格式
   3.  合约地址或账户地址网络格式错误

       在`mainnet` 上，地址的前缀应为`cfx:`&#x20;

       在`testnet` 上，地址的前缀应为`cfxtest:`

## Mint失败常见错误

1. 输入参数错误可见与[API常见错误](common-errors.md#api-chang-jian-cuo-wu)的参数输入错误相同
2.  部署的合约没有设置代付

    对于通过rainbow部署的合约，需要设置合约代付。在根据调用[部署合约](../api-reference/open-api/contract.md#deploy-contract)获得获得的id 再去调用[查询合约详情](../api-reference/open-api/contract.md#query-detail-contract)得到合约地址后，对于测试网合约，可以直接调用[设置代付](../api-reference/open-api/contract.md#set-sponsor)的接口。对于主网合约，需要先对rainbow账户进行充值，[具体可见](../tutorials/guides/)
