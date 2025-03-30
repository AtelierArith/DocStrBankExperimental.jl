```
Threads.atomic_xchg!(x::Atomic{T}, newval::T) where T
```

`x` içindeki değeri atomik olarak değiştirir.

`x` içindeki değeri `newval` ile atomik olarak değiştirir. **Eski** değeri döner.

Daha fazla ayrıntı için LLVM'nin `atomicrmw xchg` talimatına bakın.

# Örnekler

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_xchg!(x, 2)
3

julia> x[]
2
```
