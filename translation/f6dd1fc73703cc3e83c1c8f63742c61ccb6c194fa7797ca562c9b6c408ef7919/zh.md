```
uuid4([rng::AbstractRNG]) -> UUID
```

生成一个版本 4（随机或伪随机）全局唯一标识符（UUID），如 RFC 4122 所规定。

`uuid4` 使用的默认 rng 不是 `Random.default_rng()`，并且每次调用 `uuid4()` 而不带参数时都应返回一个唯一标识符。重要的是，即使在调用 `Random.seed!(seed)` 时，`uuid4` 的输出也不会重复。目前（截至 Julia 1.6），`uuid4` 使用 `Random.RandomDevice` 作为默认 rng。然而，这是一项可能在未来更改的实现细节。

!!! compat "Julia 1.6"
    截至 Julia 1.6，`uuid4` 的输出不依赖于 `Random.default_rng()`。


# 示例

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> uuid4(rng)
UUID("856e446e-0c6a-472a-9638-f7b8557cd282")
```
