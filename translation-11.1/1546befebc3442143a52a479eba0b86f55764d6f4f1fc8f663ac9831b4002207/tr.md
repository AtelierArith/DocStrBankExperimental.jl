```
Threads.atomic_xor!(x::Atomic{T}, val::T) where T
```

Atomik olarak `x`'i `val` ile bit düzeyinde XOR (özel veya) işlemi yapar.

`x[] $= val` işlemini atomik olarak gerçekleştirir. **Eski** değeri döner.

Daha fazla ayrıntı için LLVM'nin `atomicrmw xor` talimatına bakın.

# Örnekler

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_xor!(x, 7)
5

julia> x[]
2
```
