## ws建立连接和断开流程（web端）

ws建立连接和断开流程（web端）

### 关键流程
```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend


        fe->>fe:  符合某触发订阅条件:如从invisible变为visible
        fe->>be: 请求当前深度,价格,kline
        be-->>fe: 返回当前深度,价格,kline
        fe->>be:  订阅深度,价格,k线(ws.send)
        be-->>fe:  订阅成功/失败

        alt 订阅成功
        par 推送orderBook
        be-->>fe:  推送orderBook
        fe-->>fe:  更新orderBook
        and 推送kline
        be-->>fe:  推送kline
        fe-->>fe:  更新kline
        and 推送最新交易
        be-->>fe:  推送最近交易
        fe-->>fe:  更新最近交易

        alt 限价买单的单价 >= price or 限价卖单的单价 <= price
        fe->>be: 请求pendingOrder
        be-->>fe: pending[order1,order2...]
        fe-->>fe: 更新我的订单
        fe->>be: 请求finishOrder
        be-->>fe: finish[order1,order2...]
        fe-->>fe: 更新历史订单
        fe->>be: 请求该币种余额[买入币种,卖出币种]
        be-->>fe: balance[买入币种,卖出币种]
        fe-->>fe: 更新买入币种和卖出币种的余额
        else 
        end
        end
        else 订阅失败
        fe->>be: 重新订阅(ws.send)
        end

```
