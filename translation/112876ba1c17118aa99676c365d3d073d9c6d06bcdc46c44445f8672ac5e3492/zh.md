```
ssh_pub_key_path() :: String
```

`ssh_pub_key_path()` 函数返回应用于 SSH 连接的 SSH 公钥文件的路径。如果设置了 `SSH_PUB_KEY_PATH` 环境变量，则返回该值。如果没有设置但设置了 `SSH_KEY_PATH`，则返回该路径并附加 `.pub` 后缀。如果两者都没有设置，则默认返回

```
joinpath(ssh_dir(), ssh_key_name() * ".pub")
```

此默认值又依赖于 `SSH_DIR` 和 `SSH_KEY_NAME` 环境变量。
