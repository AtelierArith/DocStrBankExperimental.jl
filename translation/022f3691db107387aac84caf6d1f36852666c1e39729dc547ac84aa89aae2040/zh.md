```
ssh_known_hosts_files() :: Vector{String}
```

`ssh_known_hosts_files()` 函数返回一个 SSH 已知主机文件的路径向量，这些文件在建立 SSH 连接的远程服务器身份时应使用。默认情况下，此函数返回

```
[joinpath(ssh_dir(), "known_hosts"), bundled_known_hosts]
```

其中 `bundled_known_hosts` 是与此包捆绑的已知主机文件的副本的路径（包含 `github.com` 和 `gitlab.com` 的已知主机密钥）。然而，如果环境变量 `SSH_KNOWN_HOSTS_FILES` 被设置，则其值会根据 `:` 字符（在 Windows 上为 `;`）拆分为路径，并返回这个路径向量。如果这个向量的任何组件为空，则会扩展为默认的已知主机路径。

使用 `ssh_known_hosts_files()` 的包理想情况下应通过比较主机名和密钥类型来查找匹配条目，考虑到任何匹配文件中的第一个条目被视为主机的确定身份。如果调用者无法比较密钥类型（例如，因为它已被哈希），则必须通过在每个文件中查找主机的所有匹配条目来近似上述算法：如果一个文件中有任何主机的条目，则其中一个必须匹配；如果在早期文件中没有该主机的条目，调用者应仅继续搜索进一步的已知主机文件。
