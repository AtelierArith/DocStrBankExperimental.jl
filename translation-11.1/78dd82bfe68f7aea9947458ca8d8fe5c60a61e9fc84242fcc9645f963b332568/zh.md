```
IPv6(host::Integer) -> IPv6
```

从格式为[`Integer`](@ref)的IP地址`host`返回一个IPv6对象。

# 示例

```jldoctest
julia> IPv6(3223256218)
ip"::c01e:fc9a"
```
