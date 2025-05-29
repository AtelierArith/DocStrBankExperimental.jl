```
withjacobian(f, args...)
```

値 `f(args...)` と [`jacobian`](@ref) を名前付きタプルとして返します。

```jldoctest; setup=:(using Zygote)
julia> withjacobian(cumsum, [1,2,3])
(val = [1, 3, 6], grad = ([1 0 0; 1 1 0; 1 1 1],))
```
