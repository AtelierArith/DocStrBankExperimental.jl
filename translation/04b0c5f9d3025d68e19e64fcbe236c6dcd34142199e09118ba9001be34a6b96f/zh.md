```
filter!(f, d::AbstractDict)
```

更新 `d`，移除 `f` 为 `false` 的元素。函数 `f` 接收 `key=>value` 对。

# 示例

```jldoctest
julia> d = Dict(1=>"a", 2=>"b", 3=>"c")
Dict{Int64, String} with 3 entries:
  2 => "b"
  3 => "c"
  1 => "a"

julia> filter!(p->isodd(p.first), d)
Dict{Int64, String} with 2 entries:
  3 => "c"
  1 => "a"
```
