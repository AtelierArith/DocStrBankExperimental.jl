```
grad(f, args...; seed=1)
```

Find gradient of a callable `f` w.r.t. its arguments.

`grad()` returns two things: value of `f(args...)` and a tuple of grafients w.r.t. to its inputs (including the callable itself).

```jldoctest
using Yota   # hide

val, g = grad(x -> sum(x .+ 1), [1.0, 2.0, 3.0])

# output
(9.0, (ChainRulesCore.ZeroTangent(), [1.0, 1.0, 1.0]))
```

By default, `grad()` expects the callable to return a scalar. Vector-valued functions can be differentiated if a seed (starting value) is provided. Seed is equivalent to the vector in VJP notation.

```jldoctest
using Yota   # hide

val, g = grad(x -> 2x, [1.0, 2.0, 3.0]; seed=ones(3))

# output
([2.0, 4.0, 6.0], (ChainRulesCore.ZeroTangent(), [2.0, 2.0, 2.0]))
```

All gradients can be applied to original variables using `update!()` function.

See also: [gradtape](@ref)
