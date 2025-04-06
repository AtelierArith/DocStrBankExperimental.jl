```
Threads.atomic_cas!(x::Atomic{T}, cmp::T, newval::T) where T
```

Atomik olarak `x`'i karşılaştır ve ayarla

`x`'deki değeri `cmp` ile atomik olarak karşılaştırır. Eğer eşitse, `newval`'i `x`'e yazar. Aksi takdirde, `x`'i değiştirmeden bırakır. `x`'deki eski değeri döner. Dönen değeri `cmp` ile karşılaştırarak (`===` aracılığıyla) `x`'in değiştirilip değiştirilmediğini ve artık yeni değer `newval`'i tutup tutmadığını bilirsiniz.

Daha fazla ayrıntı için, LLVM'nin `cmpxchg` talimatına bakın.

Bu fonksiyon, işlemci semantiğini uygulamak için kullanılabilir. İşlemden önce, `x`'deki değeri kaydedersiniz. İşlemden sonra, yeni değer yalnızca `x` o sırada değiştirilmemişse saklanır.

# Örnekler

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 4, 2);

julia> x
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 3, 2);

julia> x
Base.Threads.Atomic{Int64}(2)
```
