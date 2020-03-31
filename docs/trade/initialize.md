## 初始化流程

初始化流程。

### 关键流程
```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend

        fe-->>fe: 更新相应页面
        fe->>be: 检查ws链路
        alt 已经连接
        fe->>be: 断开ws链接
        be-->>fe: 断开成功
        else 暂未连接
        fe->>be: 请求（http/ws）最新交易数据,kline数据,orderBook数据
        be-->>fe: 最新交易数据,kline数据,orderBook数据
        fe->>be: 建立ws连接
        be-->>fe: 建立成功
        loop 开始pingpong
        alt 收到close消息
        NOTE over be,fe: 重试失败后间隔加长再重试
        else 未收到close消息
        fe->>be: 每隔20s ping一次
        alt 有pong回复
        be-->>fe: 返回pingpong
        else 无pong回复
        NOTE over be,fe: 发送三次ping后无回复
        fe->>be: 断开ws链接
        be-->>fe: 断开成功
        fe->>be: 建立ws连接
        be-->>fe: 建立成功
        end
        end
        end
        end
```
