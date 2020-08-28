## Coupons.sol



### 合约作用

Coupons主要指的是消费卡劵，是一种储值卡，不同的商户发行的Coupon不同。但是都可以完成基本的发行，增发，转账，销毁等功能。



### 合约方法



#### 获取卡劵信息

方法名： getInfo

| 输入参数 | 参数含义 | 类型 |
| -------- | -------- | ---- |
| 无       | N/A      | N/A  |



#### 获取某地址剩余的余额

方法名： getBalance

| 输入参数    | 参数含义                 | 类型    |
| ----------- | ------------------------ | ------- |
| userAddress | 需要获取卡劵的余额的地址 | address |



#### 获取某地址剩余JJToken的余额

方法名：getJJTokenBalance

| 输入参数    | 参数含义                  | 类型    |
| ----------- | ------------------------- | ------- |
| userAddress | 需要获取JJToken余额的地址 | address |



#### 设定分成比例（主要用于分成时候的清算结算）

方法名：setStorePercentage

| 输入参数         | 参数含义           | 类型    |
| ---------------- | ------------------ | ------- |
| _storePercentage | 商户占据的分成比例 | uint256 |



#### 提现

方法名： withdraw

| 输入参数 | 参数含义  | 类型    |
| -------- | --------- | ------- |
| amount   | 提现数量- | Uint256 |



#### 发行卡劵

方法名：mint

| 输入参数 | 参数含义       | 类型    |
| -------- | -------------- | ------- |
| staff    | 员工地址-      | address |
| amount   | 员工发行的数量 | uint256 |



#### 批量发行卡劵

方法名：batchMint

| 输入参数 | 参数含义           | 类型      |
| -------- | ------------------ | --------- |
| staff    | 员工地址-          | address[] |
| amount   | 每个员工发行的数量 | uint256   |



#### 销毁卡劵

| 输入参数 | 参数含义   | 类型      |
| -------- | ---------- | --------- |
| account  | 销毁地址-  | address[] |
| amount   | 销毁的数量 | uint256   |



#### 转账卡劵余额

方法名：couponTransfer

| 输入参数            | 参数含义     | 类型    |
| ------------------- | ------------ | ------- |
| recipient           | 收款方地址-  | Address |
| amount              | 转账数量     | uint256 |
| _orderId            | 订单编号     | string  |
| _orderDetailId      | 订单详情编号 | string  |
| _orderContent       | 订单内容     | string  |
| _orderDetailContent | 订单详情内容 | string  |



#### 退款

方法名：couponRefund

| 输入参数            | 参数含义     | 类型    |
| ------------------- | ------------ | ------- |
| recipient           | 收款方地址-  | Address |
| amount              | 转账数量     | uint256 |
| _orderId            | 订单编号     | string  |
| _orderDetailId      | 订单详情编号 | string  |
| _orderContent       | 订单内容     | string  |
| _orderDetailContent | 订单详情内容 | string  |



