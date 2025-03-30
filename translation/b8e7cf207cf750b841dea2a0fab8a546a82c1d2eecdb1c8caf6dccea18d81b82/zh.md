```
uuid_version(u::UUID) -> Int
```

检查给定的 UUID 并返回其版本（参见 [RFC 4122](https://www.ietf.org/rfc/rfc4122)）。

# 示例

```jldoctest
julia> uuid_version(uuid4())
4
```
