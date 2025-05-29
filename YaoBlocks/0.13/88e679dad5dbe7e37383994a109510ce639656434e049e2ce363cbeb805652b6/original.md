```
kron(blocks...) -> f(n)
kron(itr) -> f(n)
```

Return a lambda, which will take the total number of qubits as input.

### Examples

If you don't know the number of qubit yet, or you are just too lazy, it is fine.

```jldoctest; setup=:(using Yao)
julia> kron(put(1=>X) for _ in 1:2)
(n -> kron(n, ((n  ->  put(n, 1 => X)), (n  ->  put(n, 1 => X)))...))

julia> kron(X for _ in 1:2)
nqubits: 2
kron
├─ 1=>X
└─ 2=>X

julia> kron(1=>X, 3=>Y)
(n -> kron(n, (1 => X, 3 => Y)...))
```
