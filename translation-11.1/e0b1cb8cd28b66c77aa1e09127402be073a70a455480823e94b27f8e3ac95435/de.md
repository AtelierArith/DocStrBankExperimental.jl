```
Core.Intrinsics.atomic_pointerreplace(pointer::Ptr{T}, expected::Any, new::T, success_order::Symbol, failure_order::Symbol) --> (old, cmp)
```

!!! compat "Julia 1.7"
    Diese Funktion erfordert Julia 1.7 oder höher.


Siehe [`unsafe_replace!`](@ref Base.unsafe_replace!).
