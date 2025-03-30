```
prevind(str::AbstractString, i::Integer, n::Integer=1) -> Int
```

  * 情况 `n == 1`

    如果 `i` 在 `s` 的范围内，返回编码在索引 `i` 之前的字符的起始索引。换句话说，如果 `i` 是一个字符的起始位置，返回前一个字符的起始位置；如果 `i` 不是一个字符的起始位置，则回退到字符的起始位置并返回该索引。如果 `i` 等于 `1`，返回 `0`。如果 `i` 等于 `ncodeunits(str)+1`，返回 `lastindex(str)`。否则抛出 `BoundsError`。
  * 情况 `n > 1`

    行为类似于将 `prevind` 应用 `n` 次，针对 `n==1`。唯一的区别是，如果 `n` 大到应用 `prevind` 会达到 `0`，那么每次剩余的迭代都会将返回值减少 `1`。这意味着在这种情况下，`prevind` 可以返回负值。
  * 情况 `n == 0`

    仅当 `i` 是 `str` 中的有效索引或等于 `ncodeunits(str)+1` 时返回 `i`。否则抛出 `StringIndexError` 或 `BoundsError`。

# 示例

```jldoctest
julia> prevind("α", 3)
1

julia> prevind("α", 1)
0

julia> prevind("α", 0)
ERROR: BoundsError: attempt to access 2-codeunit String at index [0]
[...]

julia> prevind("α", 2, 2)
0

julia> prevind("α", 2, 3)
-1
```
