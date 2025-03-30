```
Threads.atomic_and!(x::Atomic{T}, val::T) where T
```

Atomik olarak `x` ile `val`'i bit düzeyinde ve işlemi yapar.

`x[] &= val` işlemini atomik olarak gerçekleştirir. **Eski** değeri döner.

Daha fazla ayrıntı için, LLVM'nin `atomicrmw and` talimatına bakın.

# Örnekler

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_and!(x, 2)
3

julia> x[]
2
```
