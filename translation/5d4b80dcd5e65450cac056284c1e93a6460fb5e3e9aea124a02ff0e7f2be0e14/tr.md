```
Threads.atomic_max!(x::Atomic{T}, val::T) where T
```

`x` ve `val`'in maksimumunu atomik olarak `x`'e kaydedin

Atomik olarak `x[] = max(x[], val)` işlemini gerçekleştirir. **Eski** değeri döndürür.

Daha fazla ayrıntı için, LLVM'nin `atomicrmw max` talimatına bakın.

# Örnekler

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_max!(x, 7)
5

julia> x[]
7
```
