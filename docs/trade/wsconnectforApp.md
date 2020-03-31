## ws建立连接和断开流程（app端）

ws建立连接和断开流程（app端）

### 关键流程
```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend


        fe->>fe:  符合某触发订阅条件
        fe->>be:  订阅深度,价格
        be-->>fe:  订阅成功/失败

        alt 订阅成功
        loop 订阅成功
        be-->>fe:  推送orderBook
        fe-->>fe:  更新orderBook
        be-->>fe:  推送最近交易
        fe-->>fe:  更新最新交易
        end
        else 订阅失败
        fe->>be: 订阅深度,价格
        end


        ct->>fe: 用户点击k线图
        fe->>fe: 跳转到k线页面
        fe->>be:  订阅深度,价格,kline
        be-->>fe:  订阅成功/失败
        alt 订阅成功
        loop 订阅成功
        be-->>fe:  推送orderBook
        fe-->>fe:  更新orderBook
        be-->>fe:  推送kline
        fe-->>fe:  更新kline
        be-->>fe:  推送最近交易
        fe-->>fe:  更新最新交易
        end
        else 订阅失败
        fe->>be: 订阅深度,价格
        end

```
