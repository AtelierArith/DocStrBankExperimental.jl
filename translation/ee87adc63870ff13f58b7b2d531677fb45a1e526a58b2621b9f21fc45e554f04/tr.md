```
replace!(A, eski_yeni::Pair...; [sayı::Integer])
```

Her `eski=>yeni` çifti için `eski_yeni` içinde, koleksiyon `A`'daki tüm `eski` örneklerini `yeni` ile değiştirin. Eşitlik [`isequal`](@ref) kullanılarak belirlenir. Eğer `sayı` belirtilmişse, o zaman toplamda en fazla `sayı` örneğini değiştirin. Ayrıca [`replace`](@ref replace(A, eski_yeni::Pair...))'ye de bakın.

# Örnekler

```jldoctest
julia> replace!([1, 2, 1, 3], 1=>0, 2=>4, sayı=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace!(Set([1, 2, 3]), 1=>0)
Set{Int64} with 3 elements:
  0
  2
  3
```
