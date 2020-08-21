## Roles.sol



### 合约作用

增删改查不同角色的地址，方便管理员管理



### 合约方法



#### 增加一个Store

方法名： appendStore

| 输入参数         | 参数含义       | 类型    |
| ---------------- | -------------- | ------- |
| _newStoreName    | 商户名称       | string  |
| _newStoreId      | 商户Id         | string  |
| _newStoreAddress | 商户区块链地址 | address |



#### 增加一个企业

方法名： appendEnterprise

| 输入参数              | 参数含义       | 类型    |
| --------------------- | -------------- | ------- |
| _newEnterpriseName    | 企业名称       | string  |
| _newEnterpriseId      | 企业Id         | string  |
| _newEnterpriseAddress | 企业区块链地址 | address |



### 查询一个商户的Address

方法名：getStoreById

| 输入参数 | 参数含义 | 类型   |
| -------- | -------- | ------ |
| _storeId | 商户Id   | string |



### 查询一个企业的Address

方法名：getEnterpriseById

| 输入参数      | 参数含义 | 类型   |
| ------------- | -------- | ------ |
| _enterpriseId | 企业Id   | string |



### 查询商户数量

方法名： storesCount

| 输入参数 | 参数含义 | 类型 |
| -------- | -------- | ---- |
| 无       | -        | -    |



###查询某一个商户

方法名： veryStore

| 输入参数 | 参数含义                   | 类型 |
| -------- | -------------------------- | ---- |
| index    | （商户在商户数组中的下标） | uint |



### 查询某个企业

方法名： veryEnterprise

| 输入参数 | 参数含义                   | 类型 |
| -------- | -------------------------- | ---- |
| index    | （企业在商户数组中的下标） | uint |



### 更新某个商户

方法名：updateStore

| 输入参数         | 参数含义         | 类型    |
| ---------------- | ---------------- | ------- |
| _newStoreName    | 商户新名称       | string  |
| _StoreId         | 商户Id           | string  |
| _newStoreAddress | 商户新区块链地址 | address |



###更新某个企业

方法名：updateEnterprise

| 输入参数              | 参数含义         | 类型    |
| --------------------- | ---------------- | ------- |
| _newEnterpriseName    | 企业新名称       | string  |
| _enterpriseId         | 企业Id           | string  |
| _newEnterpriseAddress | 企业新区块链地址 | address |



### 删除某个商户

方法名： deleteStore

| 输入参数 | 参数含义           | 类型   |
| -------- | ------------------ | ------ |
| _storeId | 需要删除的商户的Id | string |





### 删除某个企业

方法名： deleteEnterprise

| 输入参数      | 参数含义           | 类型   |
| ------------- | ------------------ | ------ |
| _enterpriseId | 需要删除的企业的Id | string |



### 设置平台费用地址

方法名：setFeeAddress

| 输入参数       | 参数含义       | 类型   |
| -------------- | -------------- | ------ |
| _newFeeAddress | 新的feeAddress | string |



### 设置管理员地址

方法名：setAdmin

| 输入参数  | 参数含义       | 类型   |
| --------- | -------------- | ------ |
| _newAdmin | 新的管理员地址 | string |





