```
thisind(s::AbstractString, i::Integer) -> Int
```

如果 `i` 在 `s` 的范围内，返回字符编码代码单元 `i` 所在字符的起始索引。换句话说，如果 `i` 是字符的起始位置，返回 `i`；如果 `i` 不是字符的起始位置，则回退到字符的起始位置并返回该索引。如果 `i` 等于 0 或 `ncodeunits(s)+1`，则返回 `i`。在所有其他情况下抛出 `BoundsError`。

# 示例

```jldoctest
julia> thisind("α", 0)
0

julia> thisind("α", 1)
1

julia> thisind("α", 2)
1

julia> thisind("α", 3)
3

julia> thisind("α", 4)
ERROR: BoundsError: attempt to access 2-codeunit String at index [4]
[...]

julia> thisind("α", -1)
ERROR: BoundsError: attempt to access 2-codeunit String at index [-1]
[...]
```
