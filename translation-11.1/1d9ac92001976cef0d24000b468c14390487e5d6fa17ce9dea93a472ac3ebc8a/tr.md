```
@atomic var
@atomic order ex
```

`var` veya `ex` atomik olarak gerçekleştirilecektir, eğer `ex` desteklenen bir ifade ise. Eğer `order` belirtilmemişse, varsayılan olarak :sequentially_consistent kullanılır.

```
@atomic a.b.x = new
@atomic a.b.x += addend
@atomic :release a.b.x = new
@atomic :acquire_release a.b.x += addend
```

Sağda ifade edilen depolama işlemini atomik olarak gerçekleştir ve yeni değeri döndür.

`=` ile bu işlem, `setproperty!(a.b, :x, new)` çağrısına dönüşür. Herhangi bir operatör ile de bu işlem, `modifyproperty!(a.b, :x, +, addend)[2]` çağrısına dönüşür.

```
@atomic a.b.x max arg2
@atomic a.b.x + arg2
@atomic max(a.b.x, arg2)
@atomic :acquire_release max(a.b.x, arg2)
@atomic :acquire_release a.b.x + arg2
@atomic :acquire_release a.b.x max arg2
```

Sağda ifade edilen ikili işlemi atomik olarak gerçekleştir. Sonucu ilk argümandaki alana depola ve `(eski, yeni)` değerlerini döndür.

Bu işlem, `modifyproperty!(a.b, :x, func, arg2)` çağrısına dönüşür.

Daha fazla ayrıntı için kılavuzdaki [Alan başına atomikler](@ref man-atomics) bölümüne bakın.

# Örnekler

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomic a.x # a'nın x alanını, sıralı tutarlılıkla al
1

julia> @atomic :sequentially_consistent a.x = 2 # a'nın x alanını, sıralı tutarlılıkla ayarla
2

julia> @atomic a.x += 1 # a'nın x alanını, sıralı tutarlılıkla artır
3

julia> @atomic a.x + 1 # a'nın x alanını, sıralı tutarlılıkla artır
3 => 4

julia> @atomic a.x # a'nın x alanını, sıralı tutarlılıkla al
4

julia> @atomic max(a.x, 10) # a'nın x alanını maksimum değere, sıralı tutarlılıkla değiştir
4 => 10

julia> @atomic a.x max 5 # yine a'nın x alanını maksimum değere, sıralı tutarlılıkla değiştir
10 => 10
```

!!! compat "Julia 1.7"
    Bu işlevsellik en az Julia 1.7'yi gerektirir.


```
