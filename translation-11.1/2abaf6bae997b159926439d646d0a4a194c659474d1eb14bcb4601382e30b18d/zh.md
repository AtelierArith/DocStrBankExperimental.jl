```
cis(x)
```

通过使用欧拉公式：$\cos(x) + i \sin(x) = \exp(i x)$，提供了比 `exp(im*x)` 更高效的方法。

另请参见 [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref), [`angle`](@ref)。

# 示例

```jldoctest
julia> cis(π) ≈ -1
true
```
