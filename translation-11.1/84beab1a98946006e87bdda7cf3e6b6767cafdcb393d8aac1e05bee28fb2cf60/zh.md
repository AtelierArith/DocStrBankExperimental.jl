```
local
```

`local` 引入一个新的局部变量。有关更多信息，请参见 [manual section on variable scoping](@ref scope-of-variables)。

# 示例

```jldoctest
julia> function foo(n)
           x = 0
           for i = 1:n
               local x # 引入一个循环局部 x
               x = i
           end
           x
       end
foo (generic function with 1 method)

julia> foo(10)
0
```
