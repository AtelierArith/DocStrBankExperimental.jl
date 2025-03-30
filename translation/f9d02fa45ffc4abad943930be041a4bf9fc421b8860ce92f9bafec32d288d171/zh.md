```
bitrand([rng=default_rng()], [dims...])
```

生成一个随机布尔值的 `BitArray`。

# 示例

```jldoctest
julia> bitrand(Xoshiro(123), 10)
10-element BitVector:
 0
 1
 0
 1
 0
 1
 0
 0
 1
 1
```
