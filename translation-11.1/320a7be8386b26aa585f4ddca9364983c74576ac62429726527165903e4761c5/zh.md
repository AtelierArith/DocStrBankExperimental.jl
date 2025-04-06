```
fetch(c::Channel)
```

等待并返回（不移除）`Channel` 中第一个可用的项目。注意：`fetch` 在无缓冲（0大小）`Channel` 上不受支持。

# 示例

缓冲通道：

```jldoctest
julia> c = Channel(3) do ch
           foreach(i -> put!(ch, i), 1:3)
       end;

julia> fetch(c)
1

julia> collect(c)  # 项目未被移除
3-element Vector{Any}:
 1
 2
 3
```
