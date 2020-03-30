## 登陆流程

登陆流程是用户注册好后 APP 后执行的登陆流程

### 关键流程

```eval_rst
.. mermaid::

    sequenceDiagram
        participant user as Client
        participant client as Frontend
        participant server as Backend

        alt 当前时间>JWT过期时间
        client->>user: 显示用户未登陆
        else 当前时间<=JWT过期时间
        alt 当前时间<最后登陆时间+免登陆时间
        client->>user: 显示用户已登陆
        else 当前时间>=最后登陆时间+免登陆时间
        client->>user: 显示未登陆
        client->>user: 呼出手势/人脸/指纹登陆
        end
        end

        Note over user, client: 账户密码登录
        opt 账户密码登录
        user->>client: 输入账户（手机号/邮箱）
        user->>client: 输入密码
        user->>client: 点击[登录]
        client->>server: <登陆请求[用户名,密码]>
        server->>server: 验证账户密码
        alt 错误
        server-->>client: <登陆请求[失败,失败原因]>
        client-->>user: 提示错误
        else 正确
        server-->>client: <登陆请求[成功]>,<验证方式>
        client->>client: 跳转至输入验证码的页面
        user->>client: 输入验证码
        client->>server: 提交验证码
        server->>server: 验证
        alt 错误
            server-->>client: <验证错误[错误原因]>
            client-->>user: 提示错误
        else 正确
            server-->>client: <验证正确，ACCESSTOKEN>
            client-->>user: 提示登录成功
            par	登录成功的操作
                client->>client: 跳转至首页
            and
                client->>client: 本地存储账户信息
                client->>client: 更新最后一次登陆时间
            end
        end
        end
        end

```
