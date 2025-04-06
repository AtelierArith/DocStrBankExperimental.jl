```
继续
```

跳过当前循环迭代的其余部分。

# 示例

```jldoctest
julia> for i = 1:6
           iseven(i) && continue
           println(i)
       end
1
3
5
```
