```
IdDict([itr])
```

`IdDict{K,V}()` 使用 [`objectid`](@ref) 作为哈希，`===` 作为相等性构造一个哈希表，键的类型为 `K`，值的类型为 `V`。有关更多帮助，请参见 [`Dict`](@ref) 和 [`IdSet`](@ref) 的集合版本。

在下面的示例中，`Dict` 的键都是 `isequal`，因此它们被哈希为相同的值，从而被覆盖。`IdDict` 通过对象 ID 进行哈希，因此保留了 3 个不同的键。

# 示例

```julia-repl
julia> Dict(true => "yes", 1 => "no", 1.0 => "maybe")
Dict{Real, String} with 1 entry:
  1.0 => "maybe"

julia> IdDict(true => "yes", 1 => "no", 1.0 => "maybe")
IdDict{Any, String} with 3 entries:
  true => "yes"
  1.0  => "maybe"
  1    => "no"
```
