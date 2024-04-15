# Croath

Hi 👋 guys, you can call me 小鱼. I'm interested in Etheruem Protocol learning. I have expierence in backend/frontend/smart-contract dev.

 - Twitter/X: <https://twitter.com/cr0ath>
 - GitHub: <https://github.com/croath>
 - Telegram: <https://t.me/croath>

## Notes

### 2024.4.3

刚刚入门。

### 2024.4.8

学习资料：

 - https://epf.wiki/#/eps/week0
 - https://epf.wiki/#/eps/week1

读了 week0 和 week1 的前导资料和学习内容，大部分都是已经了解的知识。PoS 之后没太关注过节点架构，所以主要学习了 [node architecture](https://ethereum.org/en/developers/docs/nodes-and-clients/node-architecture/)，明天准备把整个[章节](https://ethereum.org/en/developers/docs/nodes-and-clients/)都看完，方便之后进行 week2 的学习。[以太坊白皮书](https://ethereum.org/en/whitepaper/#ethereum-whitepaper)也开始重看，刚好配合 week2 的内容同步学习，希望三天内能够看完。

### 2024.4.9

学习资料：

 - https://ethereum.org/en/developers/docs/evm/opcodes/
 - https://soliditylang.org/blog/2024/01/26/transient-storage/

学习了 evm 中的基本 opcode 和相应的 gas 计算方式，深入研究了 `TSTORE` 和 `TLOAD` 的使用方法以及相应对 transient storage 操作的方法，研究了关于重入攻击保护的应用例子代码。

### 2024.4.10

学习资料：

 - https://ethereum.org/en/developers/docs/gas/

以前的 gas fee 计算方式比较了解，这次学习了 1559 之后的新 gas fee 计算方式。但是文档也有不全面的地方，例如文档中说：

```
Every block has a base fee which acts as a reserve price. To be eligible for inclusion in a block the offered price per gas must at least equal the base fee. The base fee is calculated independently of the current block and is instead determined by the blocks before it - making transaction fees more predictable for users. When the block is created this base fee is "burned", removing it from circulation.

The base fee is calculated by a formula that compares the size of the previous block (the amount of gas used for all the transactions) with the target size. The base fee will increase by a maximum of 12.5% per block if the target block size is exceeded. This exponential growth makes it economically non-viable for block size to remain high indefinitely.
```

这里对 base fee 的 target size 和 12.5% 的提升数字描述还是比较模糊的，具体的解释应该是：

```
在 Ethereum 的 Gas 费用模型中，"target block size" 是指开发者和网络共识设定的一个理想的区块大小，用于平衡网络的吞吐量和区块生产速度。这个目标区块大小通常是区块容量上限（或者说是"gas limit"）的一半。这种做法的目的是为了让网络自动调整交易费用，以响应网络拥堵情况。

至于为什么会有最多12.5%的增长率，这个数字是基于对网络安全性、可用性和费用可预测性之间权衡的结果。通过限制每个区块基础费用的最大增长率，Ethereum 尝试在交易费用的可预测性和对网络拥堵的响应之间找到平衡点。这个比率被设计为既足够快，可以在网络使用量急剧上升时迅速调整费用，又足够慢，以避免因为短期的使用量波动导致的费用剧烈变化，从而保持网络的经济安全性和用户费用的可预测性。

简而言之，"target block size" 是一个设计上的决定，用于指导基础费用的自动调整机制，以维护网络的高效和公平使用。而12.5%的增长上限是经过计算和权衡后认为既可以有效应对网络拥堵，又不会引起费用的剧烈波动，从而保证了网络的稳定和用户体验。

以太坊（Ethereum）网络的目标区块大小是由网络的“gas limit”决定的，具体而言，目标区块大小通常被设定为一个区块 gas 上限的一半。以太坊的区块 gas 上限是动态调整的，由矿工（或在以太坊 2.0之后，是验证者）投票决定。这意味着目标区块大小并非一个静态数字，而是随着区块 gas 上限的调整而变化。

至于12.5%的增长率上限，这个数字是在以太坊EIP-1559提案中固定设定的，不是动态调整的。EIP-1559是一次重大的网络升级，旨在改善以太坊的费用市场机制。其中引入的基础费用（base fee）机制，就包括了这个最大12.5%的调整率。这意味着，如果一个区块的使用超过了目标区块大小，下一个区块的基础费用会最多增加12.5%。相反，如果区块使用量低于目标大小，基础费用会相应减少，但减少的比例也受到一定的限制，以确保网络费用的平稳变化。

这个12.5%的上限是设计上的决策，目的是防止在短时间内因为网络拥堵导致的交易费用剧烈波动，从而增加费用的可预测性，同时保持网络的安全性和稳定性。
```

单区块 gas 上限目前是 30m，不过 V 曾经在一次 reddit AMA 中提议提升 33.3% 到 40m。这一提议遭受了很多反对意见，比方说很多 node runners 表示这样会大幅增加运营成本，社交媒体上也曾有很多人表示这样的提议很不负责，如果 40 不够是要改成 80 吗，那不如直接改成超大。目前还没有增加 gas 上限的新投票。相应的投票实际上不是实时的、动态的，一般来说不会经常变化，但是理论上确实发生在每次出块的过程中。

### 2024.4.11

学习资料：

 - https://ethereum.org/en/developers/docs/data-structures-and-encoding/patricia-merkle-trie/

学习了 Merkle-Patricia 的基本原理，以及相对基本的 Merkle tree 的改善。相应的算法和代码均已学习。

### 2024.4.12

学习资料：

 - https://epf.wiki/#/eps/week2
 - https://cs251.stanford.edu/lectures/lecture7.pdf
 - https://www.youtube.com/watch?v=7sxBjSfmROc
 - https://epf.wiki/#/eps/week3
 - https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/


 > 注：[视频 An Overview of the Ethereum Excecution Layer - Dan Boneh](https://www.youtube.com/watch?v=7sxBjSfmROc) 中 5:40 左右对交易执行和同步区块的顺序解释有误，视频下的讨论也没有结论，tx 在用户端不是先进入 consensus layer 的。正确的顺序是：  
 > 1. 交易的提交：用户提交的交易首先进入到执行层（Execution Layer）。在执行层，交易被放入交易池（mempool）中等待被处理。这是因为执行层负责管理以太坊的状态和执行交易（包括智能合约的执行）。
 > 2. 区块的提议：共识层（Consensus Layer）根据权益证明（PoS）机制选出一个验证者（validator）来提议新的区块。这个验证者会从执行层的交易池中选择交易来构建新的区块。
 > 3. 新区块的处理：验证者在共识层提议新的区块后，通过 `notify_new_payload` 函数将这个新区块（或称为payload）发送给执行层。执行层接收到新区块后，会对其中的交易进行处理和验证，包括执行智能合约、更新状态等。
 > 4. 区块的确认：一旦执行层完成了对新区块的处理并验证无误，共识层就会最终确定这个区块，并将其加入到区块链中。这样，交易就被确认了。

### 2024.4.13

学习资料：

 - https://ethos.dev/beacon-chain

The Beacon Chain:

1. 一个 slot 是 12s，一个 epoch 有 32 个 slots，也就是 12s *32 = 384s = 6.4mins
2. 一个 slot 一般有一个 block，但是由于 validator 下线等原因也可以是空的
3. Validator 的最大 balance 是 32E，但是 staking 可以很多
4. 每一个 slot 都至少有一个 committee，每一个 committee 至少有 128 个 validators，一个 epoch 里每个 slot 的 commitee 中 validator 的数量是均等的，最开始就平均分配好的
5. RANDAO 根据 validator 的 balance 权重选择 proposer，proposer 可能也是该 slot 的 committee 成员，这种情况发生的概率是 1/32
6. 每个 epoch 的第一个 slot 是 checkpoint，如果 epoch 空置，checkpoint 向下一个 epoch 顺延
7. 一个 checkpoint 经过两个 epochs 会被 finalized

### 2024.4.14

学习资料：

 - https://ethos.dev/beacon-chain

接上次内容，同样是讨论 The Beacon Chain。

对于 validators 的奖惩制度主要分为六类：

1. 见证人奖励（不展开）
2. 见证人惩罚
    > 不证实 block 或者证实的 block 没有被 finalized，产生处罚
3. 日常的不在线处罚
    > 是赢得奖励的 75% 程度的处罚。例如可以获得 10% 的 APY，表现十分差的（但诚实不作恶的） validator 最多获得 -7.5% APY 的处罚，一年有 10% 时间不在线的 validator 差不多有 -0.75% APY 的处罚。
4. 削减和举报者奖励
    > 连续 8192 个 epochs 不在线的 validator 会被削减 1/32(0.5E) 的 balance，注意这里是 balance 不是 staking。如果一批 validators 同时不在线惩罚将上升，公式是 `validator_balance*3*fraction_of_validators_slashed`,如果 1/3 的 validators 同时不在线，那么第三个参数就是 1/3，公式的结算结果将是 32E，那么这批同时下线的 validators 每个人的所有 balance(32E)就全部被罚没了。与此同时，举报他人不在线可以得到奖励。
5. 提案人奖励（不展开）
6. 不作为惩罚
    > 触发条件：当网络中无法达到足够的共识，即连续四个Epoch（大约51.2分钟）都没有区块达到终结性时，不活跃泄露机制会被触发。
    >
    > 惩罚方式：一旦触发，所有验证者开始遭受不活跃泄露惩罚，这种惩罚是以二次方方式增加的，也就是说惩罚随时间的增长而迅速增大。
    >
    > 目的：这种设计的目的是在网络中出现大规模不活跃或者故障时，通过削弱不活跃验证者的影响力，快速恢复网络的正常运作。当大量验证者不活跃时，这个机制通过逐渐减少他们的抵押份额，最终使得剩余活跃的验证者能够构成网络所需的2/3多数，恢复区块的终结性。
    >
    > 影响：在不活跃泄露期间，所有验证者的见证人（attester）奖励被设置为零，但是他们仍然可以获得提案者（proposer）和告密者（whistleblower）奖励。
    >
    > 示例效果：如果50%的验证者离线，根据不活跃泄露机制的设计，大约在18天后，网络将会自动恢复到能够再次达到区块终结性的状态，因为不活跃的验证者会被逐渐排除出去。

### 2024.4.15

学习资料：

 - https://epf.wiki/#/eps/week5
 - https://ethereum.org/en/roadmap/
 - https://domothy.com/roadmap/
 - https://ethereum.org/en/community/research/#active-areas-of-ethereum-research

#### Roadmap:

The Merge:

已经完成：

  - Beacon chain
  - PoW -> PoS
  - Staking 提现

计划中：

 - Secret leader election (SLE)
 - Single Slot Finality
 - Quantum-safe aggregation-friendly signatures

The Surge:

已经完成：

 - 4844 Proto-Danksharding

计划中：

 - Rollup scaling

### 2024.4.16

学习资料：

 - https://domothy.com/blobspace/
 - https://members.delphidigital.io/reports/the-hitchhikers-guide-to-ethereum
 - https://www.youtube.com/watch?v=UClaoL12W00
 - https://blog.bingx.com/blockchain-en/what-are-sequencers-in-ethereum-network/
 - https://epf.wiki/#/eps/week6-dev