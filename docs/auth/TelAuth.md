## 短信验证流程

用户在忘记密码，修改密码等不同场景下需要短信验证的过程

### 关键流程

```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend

        ct->> fe: 点击发送
        fe->> be: <发送短信[手机号码]>
        alt 发送太频繁
        be-->>fe: <发送失败[失败原因]>
        else 成功
        be-->>fe: <发送成功>
        end

```
