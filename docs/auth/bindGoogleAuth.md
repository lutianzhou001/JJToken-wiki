## 绑定谷歌验证码流程

绑定谷歌验证码，是用户通过邮箱/手机登陆后，绑定谷歌二次认证的过程

### 关键流程


```eval_rst
.. mermaid::

    sequenceDiagram
        participant googleAuth as Googleauth
        participant ct as Client
        participant fe as Frontend
        participant be as Backend


        ct->>fe: 提交绑定googleAuth的申请
        fe->>be: <绑定googleAuth[用户名]>
        alt 还未绑定
        be-->> fe: googlekey,<验证方式>
        fe-->> ct: 跳转到绑定googleAuth页面
        ct->>googleAuth: 用户填入googlekey/扫描二维码

        par  两个验证流程
        ct ->be: google验证流程
        and
        ct ->be: 手机/邮箱验证流程
        end

        fe->>be: <绑定googleAuth验证码[两个验证码]>
        be->>be: 验证googleAuth验证码和邮箱/手机验证码
        alt 验证成功
        be-->>fe: <绑定googleAuth验证码[成功]>
        fe-->>ct: 跳转到安全中心页
        else 验证失败
        be-->>fe: <绑定googleAuth验证码[失败]>
        end
        else 已经绑定
        be-->>fe: <绑定googleAuth验证码[已经绑定]>
        fe->>ct: 已经绑定
        end


```
