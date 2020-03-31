## 重新定谷歌验证码流程

重新绑定谷歌验证码，是用户通过邮箱/手机登陆后，删除原谷歌验证码并绑定新的谷歌验证的流程

### 关键流程


```eval_rst
.. mermaid::

  sequenceDiagram
    participant user as Client
    participant client as Frontend
    participant server as Backend

    user->>client: 开启/重新设置
    client-->>user: 提示密码验证
    user->>client: 输入密码
    client->>server: <验证登陆密码[用户名,登陆密码]>
    server->>client: <验证登陆密码[成功，失败]>

    alt 失败
    client-->>user: 提示验证失败
    end

    alt 生物识别

    alt FaceID可用
    client->>client: 唤起FaceID识别
    alt 成功
      client-->>user: 提示设置成功
      client->>client: 更新用户数据库FaceID启用
      client->>client: 返回安全中心
    else 失败
      client-->>user: 提示设置失败
      client->>client: 返回安全中心
    end

    else TouchID可用
    client->>client: 唤起TouchID
    alt 成功
      client-->>user: 提示设置成功
      client->>client: 更新用户数据库TouchID启用
      client->>client: 返回安全中心
    else 失败
      client-->>user: 提示设置失败
      client->>client: 返回安全中心
    end
    end

    else 手势识别

    client->>client: 跳转至绘制手势页面
    user->>client: 绘制手势
    client->>client: 记录手势，重置手势
    client-->>user: 再次绘制
    user->>client: 绘制手势
    client->>client: 比对手势
    alt 不一致
      client-->>user: 提示不一致
      client->>client: 重置手势绘制
    else 一致
      client->>client: 本地记录手势密码
      client-->>user: 提示设置成功
      client->>client: 更新用户数据库手势启用
      client->>client: 返回安全中心
    end
    end
    
```
