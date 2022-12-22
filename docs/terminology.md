# Terminology

* **非同质化代币 (NFT):** 与比特币，以太坊这类同质化代币相对的，NFT是一类非同质化代币，每一个代币都是独一无二的存在。基于这样的特性，非同质化代币一般被用于数字藏品的发行。该NFT可作为数字藏品的唯一凭证，在保护其数字版权的基础上，实现真实可信的数字化发行、购买、收藏和使用。
* **智能合约：**运行在区块链上的代码。需要用户进行部署后，才能运行在区块链上，用户可以按编码规则对其进行编码，从而实现对应的业务逻辑。
* **交易：**合约的部署与NFT的发行都需要上链，对应的数据需要转为交易的格式，才能被区块链接受并上链。
* **燃气：**账户调用合约执行合约逻辑需要花费一定的燃气。燃气可以看作是合约执行的动力来源。账户需要为燃气的消耗支付燃气费。
* **存储：**区块链上的合约存储需要对应的空间，这部分空间用户需要为其买单。在Conflux中，存储押金的费用是每 `1024` 字节 `1` CFX。由于每个条目占用 `64` 字节，因此，每个条目的押金费用就是 `1/16` CFX. 每笔交易执行期间，新产生的押金费用会在交易执行结束的时统一收取。
* **ERC-721：**ERC-721是NFT的标准接口，广泛应用在数字藏品领域。该协议能够轻易实现数字藏品溯源，数字藏品的转移等其他功能。部署ERC721合约需要代币的名称、符号和 tokenURI。
* **ERC-1155：**ERC-1155在一定程度上融合了ERC-20和ERC-721的功能。其主要用途包括了发行同质化代币和非同质化代币。同质化代币即能像ERC-20一样发布各样的代币类型；另外，ERC-1155标准更是能够发行NFT，且能基于一个合约同时发行多个NFT。
* **Sponsor：**Sponsor机制为Conflux特有的代付机制。项目方通过为合约设置代付与白名单，可以使得白名单内的用户在不花费自身代币的基础上实现与合约的交互。
* **元数据：**元数据（Metadata）是所有 NFT 合约的重要组成部分，每个代币都有数据可供应用检索并用于显示 NFT 的内容。例如，视频 NFT 的元数据将是视频的长度和构成其各个帧的图像。个人资料图片 (PFP​​) 或数字艺术 NFT 的元数据将是特定的生成属性，它将定义 NFT 的稀有程度。元数据以json文件的形式存储在链下。
* **TokenURI：**每一个NFT都会有自己独一无二的tokenurI，该URI是一个链接，指向了一个json。该json中包含了元数据。
* **账户地址：**用户在区块链中都有一个自己的账户，该账户中保存着用户的token以及交易记录。该账户由一个独一无二的地址来进行表征，基于用户的助记词，通过密码学方法来进行生成。
* **POAP：**POAP 是英文单词 Proof of Attendance Protocol（出勤证明协议）的首字母缩写，是一个以 ERC-721 为标准，由以太坊开发者社区构建的开源协议。POAP 旨在创造一种可靠的记录生活经历的新方式。只要活动方支持 POAP，POAP 收集者就可以在参加活动后，获得一个区块链上的独特徽章作为纪念。