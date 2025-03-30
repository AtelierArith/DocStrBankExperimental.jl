```
randn!([rng=default_rng()], A::AbstractArray) -> A
```

用正态分布（均值为0，标准差为1）的随机数填充数组 `A`。另请参见 [`rand`](@ref) 函数。

# 示例

```jldoctest
julia> randn!(Xoshiro(123), zeros(5))
5-element Vector{Float64}:
 -0.6457306721039767
 -1.4632513788889214
 -1.6236037455860806
 -0.21766510678354617
  0.4922456865251828
```
