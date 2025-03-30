```
while
```

`while` 循环重复评估条件表达式，并在表达式保持为真时继续评估 while 循环的主体。如果在第一次到达 while 循环时条件表达式为假，则主体永远不会被评估。

# 示例

```jldoctest
julia> i = 1
1

julia> while i < 5
           println(i)
           global i += 1
       end
1
2
3
4
```
