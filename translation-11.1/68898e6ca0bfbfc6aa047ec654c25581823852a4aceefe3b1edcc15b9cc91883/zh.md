```
message(c::GitCommit, raw::Bool=false)
```

返回描述在提交 `c` 中所做更改的提交信息。如果 `raw` 为 `false`，则返回稍微“清理过”的信息（去除了任何前导换行符）。如果 `raw` 为 `true`，则信息不会去除任何此类换行符。
