```
Sampler(rng, x, repetition = Val(Inf))
```

返回一个采样器对象，可以用来从 `rng` 为 `x` 生成随机值。

当 `sp = Sampler(rng, x, repetition)` 时，`rand(rng, sp)` 将用于抽取随机值，并应相应地定义。

`repetition` 可以是 `Val(1)` 或 `Val(Inf)`，应作为决定预计算量的建议（如果适用）。

[`Random.SamplerType`](@ref) 和 [`Random.SamplerTrivial`](@ref) 是 *类型* 和 *值* 的默认回退。 [`Random.SamplerSimple`](@ref) 可用于存储预计算的值，而无需仅为此目的定义额外的类型。
