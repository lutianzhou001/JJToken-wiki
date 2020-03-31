## 主页流程

加载交易主页流程

### 关键流程
```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend

        ct->>fe:  进入币币页面
        fe->>be:  <获取所有交易对，和交易对的价格信息>
        be-->>fe: <[交易对1,最新价1,24h之前价1,24量1],...>

        fe->>fe:  检查定时器
        alt 定时器已经存在
        fe->>fe:  关闭定时器
        fe->>fe:  启动定时器
        else 定时器不存在
        fe->>fe: 启动定时器
        end

        loop 定时器30s触发
        fe->>be:  <获取所有交易对，和交易对的价格信息>
        be-->>fe: <[交易对1,最新价1,24h之前价1,24量1],...>
        end

```
