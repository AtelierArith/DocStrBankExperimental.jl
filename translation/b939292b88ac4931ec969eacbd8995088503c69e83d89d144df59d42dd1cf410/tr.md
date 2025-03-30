```
eigmax(A; permute::Bool=true, scale::Bool=true)
```

`A`'nın en büyük özdeğerini döndürür. `permute=true` seçeneği, matrisin üst üçgensel hale daha yakın hale gelmesi için permütasyon yapar ve `scale=true` seçeneği, satır ve sütunların norm açısından daha eşit hale gelmesi için matrisin köşegen elemanlarıyla ölçeklenmesini sağlar. `A`'nın özdeğerleri karmaşık ise, bu yöntem başarısız olacaktır, çünkü karmaşık sayılar sıralanamaz.

# Örnekler

```jldoctest
julia> A = [0 im; -im 0]
2×2 Matrix{Complex{Int64}}:
 0+0im  0+1im
 0-1im  0+0im

julia> eigmax(A)
1.0

julia> A = [0 im; -1 0]
2×2 Matrix{Complex{Int64}}:
  0+0im  0+1im
 -1+0im  0+0im

julia> eigmax(A)
HATA: DomainError with Complex{Int64}[0+0im 0+1im; -1+0im 0+0im]:
`A` karmaşık özdeğerlere sahip olamaz.
Stacktrace:
[...]
```
