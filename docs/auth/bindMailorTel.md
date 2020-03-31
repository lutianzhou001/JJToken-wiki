## 通过邮箱/手机登陆的客户绑定手机/邮箱的流程

用户通过邮箱/手机登陆，在登陆状态，用户希望通过绑定手机/邮箱增加账户安全性的过程

### 关键流程


```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend


        ct->>fe: 用户提交绑定邮箱/手机的申请
        fe->>be: <绑定邮箱/手机>
        be-->>fe: <验证方式>


        par 开始验证
        fe->>ct: 跳转到绑定页面
        ct->>fe: 用户填入邮箱/手机

        and 验证
        alt 需要google验证码
        ct->be: google验证流程
        else 需要手机/邮箱验证码
        ct->be: 手机/邮箱验证流程
        end
        end
        fe->>be: <绑定邮箱/手机[用户名,两个验证码]>

        be->>be: 验证
        alt 验证成功
        be-->> fe:  <绑定成功>
        fe-->>ct: 跳转安全中心
        else 验证失败
        be-->> fe: <绑定失败[失败原因]>
        fe-->> fe: 停留在此页面
        end

```
