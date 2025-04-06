```
iswritable(io) -> Bool
```

如果指定的 IO 对象不可写，则返回 `false`。

# 示例

```jldoctest
julia> open("myfile.txt", "w") do io
           print(io, "Hello world!");
           iswritable(io)
       end
true

julia> open("myfile.txt", "r") do io
           iswritable(io)
       end
false

julia> rm("myfile.txt")
```
