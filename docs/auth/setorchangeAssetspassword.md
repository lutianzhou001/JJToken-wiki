
## 设置或重置交易密码流程

用户在登陆状态下设置或者充值交易密码的流程

### 关键流程

```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend

        ct->>fe: 提交设置/修改交易密码

        fe->>be: <修改交易密码>
        be->>fe: <验证方式>
        fe->>fe: 跳转到修改密码页面


        par 修改交易密码
        ct->>fe: 输入两次交易密码
        and 验证
        alt 需要google验证码
        ct->be: google验证流程
        else 需要手机验证码
        ct->be: 手机验证流程
        else 需要邮箱验证码
        ct->be: 邮箱验证流程
        end
        fe->>be : <修改交易密码[新交易密码,验证码]>
        end
        be->>be: 校验
        alt 成功
        be-->>fe: <修改交易密码成功>
        fe->>fe: 返回安全中心
        else 失败
        be-->>fe: <修改交易密码失败[验证码错误]>
        fe->>fe: 停留在本页面
        end

```
