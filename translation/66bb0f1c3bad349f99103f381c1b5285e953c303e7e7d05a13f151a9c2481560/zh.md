```
convert(T, x)
```

将 `x` 转换为类型 `T` 的值。

如果 `T` 是 [`Integer`](@ref) 类型，当 `x` 不能被 `T` 表示时，将引发 [`InexactError`](@ref)，例如如果 `x` 不是整数值，或者超出了 `T` 支持的范围。

# 示例

```jldoctest
julia> convert(Int, 3.0)
3

julia> convert(Int, 3.5)
ERROR: InexactError: Int64(3.5)
Stacktrace:
[...]
```

如果 `T` 是 [`AbstractFloat`](@ref) 类型，则它将返回最接近 `x` 的 `T` 可表示的值。对于确定最近值的目的，Inf 被视为比 `floatmax(T)` 大一个 ulp。

```jldoctest
julia> x = 1/3
0.3333333333333333

julia> convert(Float32, x)
0.33333334f0

julia> convert(BigFloat, x)
0.333333333333333314829616256247390992939472198486328125
```

如果 `T` 是集合类型，而 `x` 是一个集合，则 `convert(T, x)` 的结果可能与 `x` 的全部或部分别名。

```jldoctest
julia> x = Int[1, 2, 3];

julia> y = convert(Vector{Int}, x);

julia> y === x
true
```

另请参见: [`round`](@ref), [`trunc`](@ref), [`oftype`](@ref), [`reinterpret`](@ref). ```
