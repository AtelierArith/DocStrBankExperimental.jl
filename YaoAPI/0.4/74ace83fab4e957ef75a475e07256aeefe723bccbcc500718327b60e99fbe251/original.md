```
setiparams!(block, itr)
setiparams!(block, params...)
```

Set the parameters of `block`.

### Examples

```jldoctest; setup=:(using Yao)
julia> setiparams!(Rx(0.1), 0.2)
rot(X, 0.2)
```
