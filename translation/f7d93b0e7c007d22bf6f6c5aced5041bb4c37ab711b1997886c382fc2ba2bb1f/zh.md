```
nextind(str::AbstractString, i::Integer, n::Integer=1) -> Int
```

  * 情况 `n == 1`

    如果 `i` 在 `s` 的范围内，返回字符编码在索引 `i` 之后开始的字符的起始索引。换句话说，如果 `i` 是一个字符的起始位置，返回下一个字符的起始位置；如果 `i` 不是一个字符的起始位置，则向前移动直到找到一个字符的起始位置并返回该索引。如果 `i` 等于 `0`，返回 `1`。如果 `i` 在范围内但大于或等于 `lastindex(str)`，返回 `ncodeunits(str)+1`。否则抛出 `BoundsError`。
  * 情况 `n > 1`

    行为类似于将 `nextind` 应用 `n` 次，针对 `n==1`。唯一的区别是，如果 `n` 大到应用 `nextind` 会达到 `ncodeunits(str)+1`，那么每次剩余的迭代都会将返回值增加 `1`。这意味着在这种情况下，`nextind` 可以返回一个大于 `ncodeunits(str)+1` 的值。
  * 情况 `n == 0`

    仅当 `i` 是 `s` 中的有效索引或等于 `0` 时返回 `i`。否则抛出 `StringIndexError` 或 `BoundsError`。

# 示例

```jldoctest
julia> nextind("α", 0)
1

julia> nextind("α", 1)
3

julia> nextind("α", 3)
ERROR: BoundsError: attempt to access 2-codeunit String at index [3]
[...]

julia> nextind("α", 0, 2)
3

julia> nextind("α", 1, 2)
4
```
