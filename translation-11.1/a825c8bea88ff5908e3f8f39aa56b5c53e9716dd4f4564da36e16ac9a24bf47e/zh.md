```
for
```

`for` 循环在遍历一系列值时重复评估一组语句。

迭代变量始终是一个新变量，即使在封闭作用域中存在同名变量。使用 [`outer`](@ref) 来重用现有的局部变量进行迭代。

# 示例

```jldoctest
julia> for i in [1, 4, 0]
           println(i)
       end
1
4
0
```
