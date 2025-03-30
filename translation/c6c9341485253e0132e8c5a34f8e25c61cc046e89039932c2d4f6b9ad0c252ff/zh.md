```
ssh_key_name() :: String
```

`ssh_key_name()` 函数返回 SSH 在建立连接时应使用的密钥文件的基本名称。通常没有理由直接调用此函数，库通常应使用 `ssh_key_path` 和 `ssh_pub_key_path` 函数来获取完整路径。如果环境变量 `SSH_KEY_NAME` 被设置，则此函数返回该值；否则默认返回 `id_rsa`。
