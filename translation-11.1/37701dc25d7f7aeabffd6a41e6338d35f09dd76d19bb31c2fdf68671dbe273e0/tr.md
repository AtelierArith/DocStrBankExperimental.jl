```
Threads.atomic_nand!(x::Atomic{T}, val::T) where T
```

Atomik olarak `x`'i `val` ile bitwise-nand (not-and) yapar.

`x[] = ~(x[] & val)` işlemini atomik olarak gerçekleştirir. **Eski** değeri döner.

Daha fazla ayrıntı için, LLVM'nin `atomicrmw nand` talimatına bakın.

# Örnekler

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_nand!(x, 2)
3

julia> x[]
-3
```
