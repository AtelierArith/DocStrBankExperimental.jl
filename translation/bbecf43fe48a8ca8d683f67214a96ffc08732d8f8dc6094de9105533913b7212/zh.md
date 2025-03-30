```
filter(f, d::AbstractDict)
```

返回 `d` 的副本，移除 `f` 返回 `false` 的元素。函数 `f` 接收 `key=>value` 对。

# 示例

```jldoctest
julia> d = Dict(1=>"a", 2=>"b")
Dict{Int64, String} with 2 entries:
  2 => "b"
  1 => "a"

julia> filter(p->isodd(p.first), d)
Dict{Int64, String} with 1 entry:
  1 => "a"
```
