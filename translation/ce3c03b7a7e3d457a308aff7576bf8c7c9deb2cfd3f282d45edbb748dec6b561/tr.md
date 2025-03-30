```
@boundscheck(blk)
```

İfadenin `blk` olarak sınır kontrol bloğu olarak işaretlenmesini sağlar, böylece [`@inbounds`](@ref) tarafından göz ardı edilmesine izin verir.

!!! not
    `@boundscheck` ifadesinin yazıldığı fonksiyon, `@inbounds`'ın etkili olabilmesi için çağıranına inline edilmelidir.


# Örnekler

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> @inline function g(A, i)
           @boundscheck checkbounds(A, i)
           return "accessing ($A)[$i]"
       end;

julia> f1() = return g(1:2, -1);

julia> f2() = @inbounds return g(1:2, -1);

julia> f1()
HATA: BoundsError: 2 elemanlı UnitRange{Int64} dizisinde [-1] indeksine erişim denemesi
Stacktrace:
 [1] throw_boundserror(::UnitRange{Int64}, ::Tuple{Int64}) at ./abstractarray.jl:455
 [2] checkbounds at ./abstractarray.jl:420 [inline]
 [3] g at ./none:2 [inline]
 [4] f1() at ./none:1
 [5] üst düzey kapsam

julia> f2()
"accessing (1:2)[-1]"
```

!!! uyarı     `@boundscheck` notasyonu, bir kütüphane yazarı olarak, *diğer kodların* sınır kontrollerinizi [`@inbounds`](@ref) ile kaldırmasına izin vermek için opt-in yapmanızı sağlar. Orada belirtildiği gibi, çağıran, `@inbounds` kullanmadan önce erişimlerinin geçerli olduğunu doğrulamak için erişebilecekleri bilgileri kullanmalıdır. Örneğin, [`AbstractArray`](@ref) alt sınıflarınıza indeksleme yaparken, indeksleri [`axes`](@ref) ile karşılaştırarak kontrol etmek gerekir. Bu nedenle, `@boundscheck` notasyonları, davranışının doğru olduğundan emin olduktan sonra yalnızca bir [`getindex`](@ref) veya [`setindex!`](@ref) uygulamasına eklenmelidir.
