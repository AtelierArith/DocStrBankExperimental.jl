```
getiparams(block)
```

Returns the intrinsic parameters of node `block`, default is an empty tuple.

### Examples

```jldoctest; setup=:(using Yao)
julia> getiparams(Rx(0.1))
0.1
```
