## 重新绑定谷歌验证码流程

重新绑定谷歌验证码，是用户通过邮箱/手机登陆后，删除原谷歌验证码并绑定新的谷歌验证的流程

### 关键流程


```eval_rst
.. mermaid::

    sequenceDiagram
        participant googleAuth as Googleauth
        participant ct as Client
        participant fe as Frontend
        participant be as Backend


        ct->>fe: 提交重置googleAuth的申请
        fe-->>ct: 提示将会取消原有google验证
        ct->>fe: 用户确认
        fe->>be: 提交重置googleAuth的申请
        be-->> fe: 返回需要的验证方式和googlekey
        fe-->> ct: 跳转到绑定googleAuth页面
        ct-->>googleAuth: 用户填入googlekey/扫描二维码

        par  两个验证流程
        ct ->be: google验证流程
        and
        ct ->be: 手机/邮箱验证流程
        end
        fe->>be : 提交两个流程的验证码


        be->>be: 验证googleAuth验证码和邮箱/手机验证码
        alt 验证成功
        be-->>fe: 绑定成功
        fe-->>ct: 跳转到安全中心页
        else 验证失败
        be-->>fe: 提示验证码不正确
        end


```
