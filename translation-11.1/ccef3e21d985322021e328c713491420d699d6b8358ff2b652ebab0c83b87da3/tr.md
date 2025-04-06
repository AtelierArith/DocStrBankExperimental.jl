```
Threads.atomic_min!(x::Atomic{T}, val::T) where T
```

`x` ve `val`'in minimumunu atomik olarak `x`'e kaydedin

Atomik olarak `x[] = min(x[], val)` işlemini gerçekleştirir. **Eski** değeri döndürür.

Daha fazla ayrıntı için, LLVM'nin `atomicrmw min` talimatına bakın.

# Örnekler

```jldoctest
julia> x = Threads.Atomic{Int}(7)
Base.Threads.Atomic{Int64}(7)

julia> Threads.atomic_min!(x, 5)
7

julia> x[]
5
```
