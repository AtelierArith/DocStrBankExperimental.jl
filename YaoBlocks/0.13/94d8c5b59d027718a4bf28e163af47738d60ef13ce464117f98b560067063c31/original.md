```
PSwap = PutBlock{2,2,RotationGate{2,T,G}} where {G<:ConstGate.SWAPGate}
PSwap(n::Int, locs::Tuple{Int,Int}, θ::Real)
```

Parametrized swap gate that swaps two qubits with a phase, defined as

$$
{\rm SWAP}(θ) = e^{-iθ{\rm SWAP}/2}
$$
