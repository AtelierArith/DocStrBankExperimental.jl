```
approve(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

存储 `payload` 凭证以便在将来的身份验证中重用。仅在身份验证成功时调用。

`shred` 关键字控制是否应销毁凭证字段中的敏感信息。仅在测试期间设置为 `false`。
