```
Threads.atomic_add!(x::Atomic{T}, val::T) where T <: ArithmeticTypes
```

Atomik olarak `val` değerini `x`'e ekler.

`x[] += val` işlemini atomik olarak gerçekleştirir. **Eski** değeri döner. `Atomic{Bool}` için tanımlı değildir.

Daha fazla ayrıntı için LLVM'nin `atomicrmw add` talimatına bakın.

# Örnekler

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_add!(x, 2)
3

julia> x[]
5
```
