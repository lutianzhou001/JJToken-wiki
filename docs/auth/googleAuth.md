## 谷歌验证流程

用户在忘记密码，修改密码等不同场景下需要google验证的过程

### 关键流程


```eval_rst
.. mermaid::

    sequenceDiagram
        participant ct as Client
        participant fe as Frontend
        participant be as Backend


        opt google验证码
        ct->> fe: 填入google验证码
        fe->> be: 提交google验证码
        end


```
