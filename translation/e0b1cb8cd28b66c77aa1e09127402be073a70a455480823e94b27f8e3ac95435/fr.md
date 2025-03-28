```
Core.Intrinsics.atomic_pointerreplace(pointer::Ptr{T}, expected::Any, new::T, success_order::Symbol, failure_order::Symbol) --> (old, cmp)
```

!!! compat "Julia 1.7"
    Cette fonction nécessite Julia 1.7 ou une version ultérieure.


Voir [`unsafe_replace!`](@ref Base.unsafe_replace!).
