```
Threads.atomic_sub!(x::Atomic{T}, val::T) where T <: ArithmeticTypes
```

`val`'ı `x`'ten atomik olarak çıkarır.

`x[] -= val` işlemini atomik olarak gerçekleştirir. **Eski** değeri döner. `Atomic{Bool}` için tanımlı değildir.

Daha fazla ayrıntı için LLVM'nin `atomicrmw sub` talimatına bakın.

# Örnekler

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_sub!(x, 2)
3

julia> x[]
1
```
