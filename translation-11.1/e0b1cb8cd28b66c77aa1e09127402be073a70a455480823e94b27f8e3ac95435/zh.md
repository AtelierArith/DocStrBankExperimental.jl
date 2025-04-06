```
Core.Intrinsics.atomic_pointerreplace(pointer::Ptr{T}, expected::Any, new::T, success_order::Symbol, failure_order::Symbol) --> (old, cmp)
```

!!! compat "Julia 1.7"
    此函数需要 Julia 1.7 或更高版本。


请参见 [`unsafe_replace!`](@ref Base.unsafe_replace!)。
