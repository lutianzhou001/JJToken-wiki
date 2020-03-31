## KYC认证流程

用户在进行KYC（ know your customer ）认证时执行的流程 

### 关键流程

```eval_rst
.. mermaid::

    sequenceDiagram
        participant user as Client
        participant client as Frontend
        participant server as Backend

        user->>client: 点击KYC验证
        alt 已验证
        client->>user: 显示已验证的结果页
        else 验证中
        client->>user: 显示验证中的结果页
        end

        client->>client: 跳转至验证页
        user->>client: 选择验证图片上传
        client->>client: 检测图片是否符合要求
        alt 不符合要求
        client-->>user: 提示不符合要求，重新上传
        else 符合要求
        client->>client: 激活[下一步]
        user->>client: 点击[下一步]
        client->>server: <KYC验证>
        server-->>client: <KYC验证结果[成功/失败原因/审核中]>
        alt 上传成功
        client-->>user: 提示上传成功，等待审核
        else 上传失败
        client-->>user: 提示上传失败，重新上传
        end
        end
```