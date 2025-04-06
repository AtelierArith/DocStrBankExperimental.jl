```
for outer
```

在 `for` 循环中重用现有的局部变量进行迭代。

有关更多信息，请参见[变量作用域手册部分](@ref scope-of-variables)。

另请参见[`for`](@ref)。

# 示例

```jldoctest
julia> function f()
           i = 0
           for i = 1:3
               # empty
           end
           return i
       end;

julia> f()
0
```

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # empty
           end
           return i
       end;

julia> f()
3
```

```jldoctest
julia> i = 0 # 全局变量
       for outer i = 1:3
       end
ERROR: syntax: no outer local variable declaration exists for "for outer"
[...]
```
