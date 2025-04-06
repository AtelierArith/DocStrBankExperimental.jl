```
reject(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

丢弃 `payload` 凭证，以防在未来的身份验证中被重新使用。仅在身份验证失败时调用。

`shred` 关键字控制是否应销毁凭证字段中的敏感信息。仅在测试期间设置为 `false`。
