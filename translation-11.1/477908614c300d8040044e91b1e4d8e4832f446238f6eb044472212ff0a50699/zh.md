```
isreadable(io) -> Bool
```

如果指定的 IO 对象不可读，则返回 `false`。

# 示例

```jldoctest
julia> open("myfile.txt", "w") do io
           print(io, "Hello world!");
           isreadable(io)
       end
false

julia> open("myfile.txt", "r") do io
           isreadable(io)
       end
true

julia> rm("myfile.txt")
```
