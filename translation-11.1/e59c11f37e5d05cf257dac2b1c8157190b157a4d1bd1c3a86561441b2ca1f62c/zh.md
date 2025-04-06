```
@show exs...
```

将一个或多个表达式及其结果打印到 `stdout`，并返回最后一个结果。

另请参见: [`show`](@ref), [`@info`](@ref man-logging), [`println`](@ref).

# 示例

```jldoctest
julia> x = @show 1+2
1 + 2 = 3
3

julia> @show x^2 x/2;
x ^ 2 = 9
x / 2 = 1.5
```
