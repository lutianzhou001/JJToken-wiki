## 取消订阅流程

取消订阅流程

### 关键流程
```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend

        fe->>fe: 监听各个子组件的visual属性
        opt 某子组件visual属性为false
        fe->>be: 取消相应的订阅
        end
        opt 取消不成功
        fe->>be: 重新取消相应的订阅
        end

```
