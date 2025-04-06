```
<<(B::BitVector, n) -> BitVector
```

左位移运算符，`B << n`。对于 `n >= 0`，结果是 `B` 的元素向后移动 `n` 个位置，用 `false` 值填充。如果 `n < 0`，元素向前移动。等价于 `B >> -n`。

# 示例

```jldoctest
julia> B = BitVector([true, false, true, false, false])
5-element BitVector:
 1
 0
 1
 0
 0

julia> B << 1
5-element BitVector:
 0
 1
 0
 0
 0

julia> B << -1
5-element BitVector:
 0
 1
 0
 1
 0
```
