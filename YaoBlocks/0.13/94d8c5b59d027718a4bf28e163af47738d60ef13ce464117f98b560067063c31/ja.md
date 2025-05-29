```
PSwap = PutBlock{2,2,RotationGate{2,T,G}} where {G<:ConstGate.SWAPGate}
PSwap(n::Int, locs::Tuple{Int,Int}, θ::Real)
```

位相を持つ2つの量子ビットをスワップするパラメータ化されたスワップゲートで、次のように定義されます。

$$
{\rm SWAP}(θ) = e^{-iθ{\rm SWAP}/2}
$$
