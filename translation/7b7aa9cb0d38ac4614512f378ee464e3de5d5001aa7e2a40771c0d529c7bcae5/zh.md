```
rem(x::Integer, T::Type{<:Integer}) -> T
mod(x::Integer, T::Type{<:Integer}) -> T
%(x::Integer, T::Type{<:Integer}) -> T
```

找到 `y::T` 使得 `x` ≡ `y` (mod n)，其中 n 是可表示在 `T` 中的整数数量，`y` 是 `[typemin(T),typemax(T)]` 中的一个整数。如果 `T` 可以表示任何整数（例如 `T == BigInt`），那么此操作对应于转换为 `T`。

# 示例

```jldoctest
julia> x = 129 % Int8
-127

julia> typeof(x)
Int8

julia> x = 129 % BigInt
129

julia> typeof(x)
BigInt
```
