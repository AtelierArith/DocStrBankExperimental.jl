```
ErrorException(msg)
```

通用错误类型。错误消息在 `.msg` 字段中，可能提供更具体的细节。

# 示例

```jldoctest
julia> ex = ErrorException("我做了一件坏事");

julia> ex.msg
"我做了一件坏事"
```
