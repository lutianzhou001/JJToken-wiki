## JJToken.sol



### 合约作用

这是通用Token的主合约，通用Token是在整个系统流转的稳定Token，同时，也可以实现和法币之间的自由兑换。



### 合约方法



#### 查询JJToken的余额

方法名： jjBalance

| 输入参数    | 参数含义       | 类型    |
| ----------- | -------------- | ------- |
| userAddress | 需要查询的地址 | address |



#### 给企业发行JJToken

方法名： jjMint

| 输入参数   | 参数含义              | 类型    |
| ---------- | --------------------- | ------- |
| enterprise | 企业区块链地址        | string  |
| amount     | 需要发行的JJToken数量 | uint256 |



#### 销毁一定数量的JJToken

方法名：jjBurn

| 输入参数 | 参数含义       | 类型    |
| -------- | -------------- | ------- |
| account  | 需要销毁的地址 | address |
| amount   | 需要销毁的数量 | uint256 |



#### 授权给合约使用自己的JJToken

方法名：jjApproveTo

| 输入参数     | 参数含义 | 类型    |
| ------------ | -------- | ------- |
| tokenAddress | 合约地址 | address |
| amount       | 授权数量 | uint256 |



#### 转账JJToken（主要用户企业向商家购买卡券）

方法名： jjTransfer

| 输入参数  | 参数含义 | 类型    |
| --------- | -------- | ------- |
| recipient | 接受人-  | address |
| amount    | 数量     | Uint256 |


