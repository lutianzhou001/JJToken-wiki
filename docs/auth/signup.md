## 注册流程

注册流程是用户第一次进入APP的时候需要执行的流程


### 关键流程

```eval_rst
.. mermaid::

    sequenceDiagram
        participant user as Client
        participant client as Frontend
        participant server as Backend

        Note over user, client: 页面[输入账户]
        user->>client: 输入手机号
        user->>client: 点击[下一步]
        client->>server: <账户是否可用>
        server-->>client: <账户是否可用[是/否]>
        alt 账户已注册
            client-->>user: 提示已注册，停留在当前页
        else 账户未注册
            client->>client: 跳转至[下一步]
        end

        Note over user, client: 页面[输入密码]
        user->>client: 输入密码
        user->>client: 再次输入密码
        client->>client: 比对密码
        alt 比对不一致
            client-->>user: 提示不一致
        else 比对一致
            client->>client: 激活[发送验证码]
        user->>client: 点击[发送验证码]
        client->>server: <发送验证码[手机/邮箱]>
        server-->>client: <发送验证码[成功/失败]>
        alt 发送失败
            client-->>user: 提示错误，停留在本页
        else 发送成功
            client-->>user: 提示已发送验证码
        client->>client: 启动[验证码计时器]
        user->>client: 输入验证码
        user->>client: 点击[下一步]
        client->>server: <请求注册[邮箱/手机,验证码]>
        server-->>client: <请求注册[成功/失败原因]>
        alt 验证成功
            client-->>user: 提示注册成功
            client->>client: 跳转至[登录页]
        else 验证失败
            client-->>user: 提示验证码错误/发送过于频繁:停留在当前页
        end
      end
    end


```

### 接口定义


TODO: To be continued;


