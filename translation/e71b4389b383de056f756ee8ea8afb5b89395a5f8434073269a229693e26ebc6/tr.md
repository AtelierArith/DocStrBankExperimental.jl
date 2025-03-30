```
@view A[inds...]
```

İndeksleme ifadesi `A[inds...]`'i eşdeğer [`view`](@ref) çağrısına dönüştürün.

Bu yalnızca tek bir indeksleme ifadesine doğrudan uygulanabilir ve `A[begin, 2:end-1]` gibi özel `begin` veya `end` indeksleme sözdizimlerini içeren ifadeler için özellikle yararlıdır (çünkü bunlar normal [`view`](@ref) işlevi tarafından desteklenmez).

`@view`'in bir normal atamanın hedefi olarak kullanılamayacağını (örneğin, `@view(A[1, 2:end]) = ...`), ayrıca süslemesiz [indeksli atama](@ref man-indexed-assignment) (`A[1, 2:end] = ...`) veya yayılmış indeksli atamanın (`A[1, 2:end] .= ...`) bir kopya oluşturmayacağını unutmayın. Ancak, `@view(A[1, 2:end]) .+= 1` gibi *güncelleme* işlemleri için yararlı olabilir çünkü bu, `@view(A[1, 2:end]) .= @view(A[1, 2:end]) + 1` için basit bir sözdizimidir ve sağdaki indeksleme ifadesi `@view` olmadan bir kopya oluşturacaktır.

Ayrıca, skalar olmayan indeksleme için bir kod bloğunun tamamını görünümler kullanacak şekilde değiştirmek için [`@views`](@ref) ile de bakabilirsiniz.

!!! compat "Julia 1.5"
    Bir indeksleme ifadesinde ilk indeksi belirtmek için `begin` kullanmak en az Julia 1.5 gerektirir.


# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = @view A[:, 1]
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 0
 0

julia> A
2×2 Matrix{Int64}:
 0  2
 0  4
```
