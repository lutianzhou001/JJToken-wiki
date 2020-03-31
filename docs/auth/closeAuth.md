
## 关闭验证流程

用户在登陆状态下，关闭某个验证流程的过程

### 关键流程


```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend


        ct->>fe: 向前端提交关闭邮箱/手机/googleAuth申请


        fe->>be:  <关闭验证请求[用户名，关闭验证方式]>
        be-->>fe: <验证方式>

        opt 验证
        ct->be: google验证
        ct->be: 手机/邮箱验证
        end

        fe->>be: <关闭验证请求[用户名,两个验证码]>
        be->>be: 验证两个验证码


        alt 校验成功
        be-->>fe: <关闭成功>
        fe-->>fe: 更新本地数据库:关闭验证
        fe-->>ct: 返回到安全中心页面
        else 校验不成功
        be-->>fe: <关闭不成功，验证码错误>
        end

```
