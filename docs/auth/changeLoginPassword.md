## 修改登陆密码流程

用户在登陆状态下修改登陆密码的流程

### 关键流程

```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend

        ct->> fe: 修改登陆密码
        fe->> fe: 进入修改页面
        ct->> fe: 输入原密码
        ct->> fe: 输入修改后密码
        ct->> fe: 确认修改后密码
        alt 密码不一致
        fe-->> ct: 提示前后输入不一致
        else 密码一致
        fe->> be: <修改登陆密码[原密码,新密码]>
        end
        be->> be: 校验
        alt 校验成功
        be-->>fe : <修改成功>
        fe->>fe : 退出登陆
        else 校验失败
        be-->>fe:  <修改失败[原密码不正确]>
        fe-->>ct:  提示修改失败
        end

```
