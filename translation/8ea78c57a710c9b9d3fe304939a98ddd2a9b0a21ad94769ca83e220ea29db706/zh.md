```
LibGit2.split_cfg_entry(ce::LibGit2.ConfigEntry) -> Tuple{String,String,String,String}
```

将 `ConfigEntry` 拆分为以下部分：部分、子部分、名称和值。

# 示例

给定包含以下内容的 git 配置文件：

```
[credential "https://example.com"]
    username = me
```

`ConfigEntry` 看起来如下：

```julia-repl
julia> entry
ConfigEntry("credential.https://example.com.username", "me")

julia> LibGit2.split_cfg_entry(entry)
("credential", "https://example.com", "username", "me")
```

有关更多详细信息，请参阅 [git config 语法文档](https://git-scm.com/docs/git-config#_syntax)。
