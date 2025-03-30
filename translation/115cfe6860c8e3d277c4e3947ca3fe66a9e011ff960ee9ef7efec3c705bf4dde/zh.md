```
uuid1([rng::AbstractRNG]) -> UUID
```

生成一个版本 1（基于时间）的全局唯一标识符（UUID），如 RFC 4122 所规定。请注意，节点 ID 是随机生成的（不识别主机），根据 RFC 的第 4.5 节。

`uuid1` 使用的默认 rng 不是 `Random.default_rng()`，每次调用 `uuid1()` 而不带参数时，应该预期返回一个唯一标识符。重要的是，即使在调用 `Random.seed!(seed)` 时，`uuid1` 的输出也不会重复。目前（截至 Julia 1.6），`uuid1` 使用 `Random.RandomDevice` 作为默认 rng。然而，这是一项可能在未来更改的实现细节。

!!! compat "Julia 1.6"
    截至 Julia 1.6，`uuid1` 的输出不依赖于 `Random.default_rng()`。


# 示例

```jldoctest; filter = r"[a-z0-9]{8}-([a-z0-9]{4}-){3}[a-z0-9]{12}"
julia> using Random

julia> rng = MersenneTwister(1234);

julia> uuid1(rng)
UUID("cfc395e8-590f-11e8-1f13-43a2532b2fa8")
```
