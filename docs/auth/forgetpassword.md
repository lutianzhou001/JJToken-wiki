## 忘记密码流程

忘记密码是用户忘记密码后要进行的流程

### 关键流程

```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend


        ct->> fe: 用户点击忘记密码
        fe->> ct: 修改密码界面
        ct->> fe: 用户输入邮箱/手机


        fe ->> be: <忘记密码[邮箱/手机]>
        alt 找到该邮箱或手机
        be->> be: 检查绑定信息
        be-->>fe: <验证方式>
        fe-->>ct: 跳转输入新密码和验证码界面
        ct->>fe: 用户填入新密码
        ct->>fe: 用户确认新密码


        alt 需要google验证码
        ct->be: google验证流程
        else 需要手机/邮箱验证码
        ct->be: 手机/邮箱验证流程
        end
        fe->>be: <提交[用户名,验证方式,验证码，新密码]>


        else 找不到该邮箱或者手机
        be-->> fe: <找不到该用户>
        fe-->> ct: 返回用户不存在
        end

        be->>be: 验证并修改密码
        alt 验证成功
        be-->> fe: 修改成功
        fe-->>ct: 跳转登陆页
        else 验证失败
        be-->> fe: 验证失败，并留在此页
        end

```
