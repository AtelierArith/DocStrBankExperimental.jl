```
chown(path::AbstractString, owner::Integer, group::Integer=-1)
```

将 `path` 的所有者和/或组更改为 `owner` 和/或 `group`。如果输入的 `owner` 或 `group` 的值为 `-1`，则相应的 ID 将不会更改。目前仅支持整数类型的 `owner` 和 `group`。返回 `path`。
