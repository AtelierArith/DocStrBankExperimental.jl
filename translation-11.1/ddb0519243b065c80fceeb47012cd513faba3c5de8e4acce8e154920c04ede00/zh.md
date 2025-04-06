```
global
```

`global x` 使得当前作用域及其内部作用域中的 `x` 引用同名的全局变量。有关更多信息，请参见 [manual section on variable scoping](@ref scope-of-variables)。

# 示例

```jldoctest
julia> z = 3
3

julia> function foo()
           global z = 6 # 使用在 foo 外部定义的 z 变量
       end
foo (generic function with 1 method)

julia> foo()
6

julia> z
6
```
