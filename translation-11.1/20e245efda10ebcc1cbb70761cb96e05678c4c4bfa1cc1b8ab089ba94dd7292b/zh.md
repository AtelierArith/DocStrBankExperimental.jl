```
get!(f::Union{Function, Type}, collection, key)
```

返回给定键存储的值；如果该键没有映射，则存储 `key => f()`，并返回 `f()`。

这旨在使用 `do` 块语法调用。

# 示例

```jldoctest
julia> squares = Dict{Int, Int}();

julia> function get_square!(d, i)
           get!(d, i) do
               i^2
           end
       end
get_square! (generic function with 1 method)

julia> get_square!(squares, 2)
4

julia> squares
Dict{Int64, Int64} with 1 entry:
  2 => 4
```
