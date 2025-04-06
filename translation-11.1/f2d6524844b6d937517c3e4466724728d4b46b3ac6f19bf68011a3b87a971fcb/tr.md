```
Threads.atomic_or!(x::Atomic{T}, val::T) where T
```

`x` ile `val`'ı atomik olarak bitwise-or yapar.

`x[] |= val` işlemini atomik olarak gerçekleştirir. **Eski** değeri döner.

Daha fazla ayrıntı için LLVM'nin `atomicrmw or` talimatına bakın.

# Örnekler

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_or!(x, 7)
5

julia> x[]
7
```
