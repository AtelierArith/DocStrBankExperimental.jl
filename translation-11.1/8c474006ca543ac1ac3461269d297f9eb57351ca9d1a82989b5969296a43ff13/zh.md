```
ssh_known_hosts_file() :: String
```

`ssh_known_hosts_file()` 函数返回一个 SSH 已知主机文件的单一路径，该文件在建立 SSH 连接的远程服务器身份时应使用。它返回 `ssh_known_hosts_files` 返回的第一个实际存在的路径。可以查看多个已知主机文件的调用者应使用 `ssh_known_hosts_files`，并在该函数文档中描述的所有返回文件中查找主机匹配。
