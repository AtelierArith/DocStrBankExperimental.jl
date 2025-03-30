```
ssh_key_path() :: String
```

`ssh_key_path()` 函数返回应用于 SSH 连接的 SSH 私钥文件的路径。如果设置了 `SSH_KEY_PATH` 环境变量，则返回该值。否则，它默认返回

```
joinpath(ssh_dir(), ssh_key_name())
```

这个默认值又依赖于 `SSH_DIR` 和 `SSH_KEY_NAME` 环境变量。
