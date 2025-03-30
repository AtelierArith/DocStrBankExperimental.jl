```
credential_callback(...) -> Cint
```

一个 LibGit2 凭证回调函数，提供与连接协议相关的不同凭证获取功能。`payload_ptr` 需要包含一个 `LibGit2.CredentialPayload` 对象，该对象将跟踪状态和设置。

`allowed_types` 包含一个 `LibGit2.Consts.GIT_CREDTYPE` 值的位掩码，指定应尝试哪些身份验证方法。

凭证身份验证按以下顺序进行（如果支持）：

  * SSH 代理
  * SSH 私钥/公钥对
  * 用户名/密码明文

如果用户被提示输入凭证，他们可以通过输入 `^D`（同时按下控制键和 `d` 键）来中止提示。

**注意**：由于 `libgit2` 身份验证过程的特性，当身份验证失败时，此函数会再次被调用，而没有任何指示身份验证是否成功。为了避免因重复使用相同的错误凭证而导致的无限循环，我们将使用有效负载跟踪状态。

有关更多详细信息，请参阅 LibGit2 关于 [对服务器进行身份验证](https://libgit2.org/docs/guides/authentication/) 的指南。
