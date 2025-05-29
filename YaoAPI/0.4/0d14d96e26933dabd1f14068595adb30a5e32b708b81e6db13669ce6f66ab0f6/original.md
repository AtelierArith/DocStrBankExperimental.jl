```
dispatch!(x::AbstractBlock, collection)
```

Dispatch parameters in collection to block tree `x`.

### Arguments

  * `x`: the block to dispatch parameters on.
  * `collection`: a collection of parameters, e.g a list of numbers,   also supports `:zero` and `:random`, here `:random` is equivalent   to `rand(nparameters(x))`.

!!! note
    it will try to dispatch the parameters in collection first.


### Examples

```jldoctest; setup=:(using Yao)
julia> dispatch!(chain(Rx(0.1), Rz(0.1)), [0.2, 0.3])
nqubits: 1
chain
├─ rot(X, 0.2)
└─ rot(Z, 0.3)

julia> dispatch!(chain(Rx(0.1), Rz(0.2)), :zero)
nqubits: 1
chain
├─ rot(X, 0.0)
└─ rot(Z, 0.0)
```
