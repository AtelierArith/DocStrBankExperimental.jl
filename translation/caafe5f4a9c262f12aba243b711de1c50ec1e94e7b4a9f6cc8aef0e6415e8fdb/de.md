```
Core.Intrinsics.atomic_pointermodify(pointer::Ptr{T}, function::(old::T,arg::S)->T, arg::S, order::Symbol) --> old
```

!!! compat "Julia 1.7"
    Diese Funktion erfordert Julia 1.7 oder später.


Siehe [`unsafe_modify!`](@ref Base.unsafe_modify!).
