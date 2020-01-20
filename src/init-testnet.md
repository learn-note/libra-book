[TOC]

## Libra 本地测试网搭建

[参考文档 >>](https://developers.libra.org/docs/my-first-transaction)

verify date: 2020.01.03

### 启动测试网

#### 1> 环境

```
macOS 10.15.2
```

#### 2> 下载代码


```
git clone https://github.com/libra/libra.git
```

#### 3> 切换到测试网分支

```
git checkout testnet

```

#### 4> 编译构建依赖项

```
cd libra
./scripts/dev_setup.sh
```

#### 5> 启动并连接到本地网络（当前公网测试网异常，故文档使用本地测试网络)


```
cargo run -p libra-swarm -- -s -n 4

```

#### 6> 查询当前账户情况(当前无账户)

```
libra% a la
No user accounts
Faucet account address: 000000000000000000000000000000000000000000000000000000000a550c18, sequence_number: 1, status: Persisted
```

#### 7> 创建第一个账户

```
libra% a c
>> Creating/retrieving next account from wallet
Created/retrieved account #0 address a64349b5586d0277cb4cbe0eb3ef36e8bdb62fbe4dbefcaf60c417ee13301ce0
```

#### 8> 创建第二个账户


```
libra% a c
>> Creating/retrieving next account from wallet
Created/retrieved account #1 address 8e001662a517b13a77e23935fd2bd27a57adaaa8960ac0c90918eb9cc769e711
```

#### 9> 查询当前账户情况(当前有两个测试账户)


```
libra% a la
User account index: 0, address: a64349b5586d0277cb4cbe0eb3ef36e8bdb62fbe4dbefcaf60c417ee13301ce0, sequence number: 0, status: Local
User account index: 1, address: 8e001662a517b13a77e23935fd2bd27a57adaaa8960ac0c90918eb9cc769e711, sequence number: 0, status: Local
Faucet account address: 000000000000000000000000000000000000000000000000000000000a550c18, sequence_number: 1, status: Persisted
```

#### 10> 使用第一个(0 号) 帐号去挖矿，目标 110 libra

```
libra% a m 0 110
>> Minting coins
Mint request submitted
```

#### 11> 使用第二个(1 号) 帐号去挖矿，目标 52 libra

```
libra% a m 1 52
>> Minting coins
Mint request submitted
```

#### 12> 查询第一个账户余额（无余额)

```
libra%  q b 0
Balance is: 110.000000
```

#### 13> 查询第二个账户余额（无余额)

```
libra% q b 1
Balance is: 52.000000
```



#### 14> 关注合约序号


```
libra% q s 0
>> Getting current sequence number
Sequence number is: 0
libra% q s 1
>> Getting current sequence number
Sequence number is: 0

```
#### 15> 执行转账 0 号账户转账到 1号


```
libra% t 0  1 10
>> Transferring
Transaction submitted to validator
To query for transaction status, run: query txn_acc_seq 0 0 <fetch_events=true|false>

```

#### 16> 关注合约序号, 已出现递增


```
libra% q s 0
>> Getting current sequence number
Sequence number is: 1
libra% q s 1
>> Getting current sequence number
Sequence number is: 0

```

#### 17> 查询余额，确认转账成功

```
libra% q b 0
Balance is: 100.000000
libra% q b 1
Balance is: 62.000000
```


## Donate

```
BTC - 1HeHGwV2VQjnjMu5KhgCc8omQAvWskhjzt
ETH - 0xd2fe0ed0d4dfb072220570098f0e32594ba5a700
```
