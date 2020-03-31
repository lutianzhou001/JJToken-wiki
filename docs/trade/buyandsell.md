## 买入卖出流程

登陆后，用户买入卖出资产的流程

### 关键流程
```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend

        ct->>fe: 点击进入交易页面
        fe->>fe: 判断用户是否登陆
        alt 用户已登陆
        fe-->>ct: 显示“买入”或“卖出”
        fe-->>ct: 展示用户所持该资产数量
        else 用户未登陆
        fe-->>ct: 显示“请登录”
        fe-->>ct: 展示用户所持该资产数量为“-”
        end

        par 输入买入金额
        alt 限价买入/卖出
        opt 限价方法1
        ct->>fe: 点击orderBook
        end
        opt 限价方式2
        ct->>fe: 输入限价
        end
        else 市价买入
        end
        and 输入买入数量
        ct->>fe: 输入买入数量
        end

        ct->>fe: 点击买入/卖出
        fe->>fe: 校验
        alt 用户余额不足
        fe->>ct: 提示用户余额不足
        else 小于最小买入/卖出
        fe->>ct: 提示用户小于最小买入/卖出
        fe->>fe: 停留在本页面
        end
        fe->>be: <put_limit>
        be-->>fe: <put_limit>
        alt token已过期/错误
        be-->>fe: <买入失败[token已过期/token错误]>
        fe-->>ct: 登陆失效
        fe->>fe : 跳转到登陆页面
        else 余额不足
        be-->>fe: <买入失败[余额不足]>
        fe-->>ct: 余额不足
        fe->>fe: 停留在本页面
        end
        NOTE over fe,be:方案待定
        fe->>be: 请求该币种余额[买入币种,卖出币种]
        be-->>fe: balance[买入币种,卖出币种]
        fe-->>fe: 更新买入币种和卖出币种的余额

```
