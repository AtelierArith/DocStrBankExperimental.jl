```
Core.Intrinsics.atomic_pointermodify(pointer::Ptr{T}, function::(old::T,arg::S)->T, arg::S, order::Symbol) --> old
```

!!! compat "Julia 1.7"
    Cette fonction nécessite Julia 1.7 ou une version ultérieure.


Voir [`unsafe_modify!`](@ref Base.unsafe_modify!).
