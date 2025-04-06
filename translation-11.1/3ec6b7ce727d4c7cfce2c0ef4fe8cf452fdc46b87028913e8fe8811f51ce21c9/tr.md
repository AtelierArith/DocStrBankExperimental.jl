```
mergewith!(combine, d::AbstractDict, others::AbstractDict...) -> d
mergewith!(combine)
merge!(combine, d::AbstractDict, others::AbstractDict...) -> d
```

Diğer koleksiyonlardan çiftlerle koleksiyonu güncelleyin. Aynı anahtara sahip değerler, birleştirici fonksiyon kullanılarak birleştirilecektir. Curry'li form `mergewith!(combine)` fonksiyonu `(args...) -> mergewith!(combine, args...)` döndürür.

`merge!(combine::Union{Function,Type}, args...)` metodu, `mergewith!(combine, args...)`'in bir takma adı olarak geriye dönük uyumluluk için hala mevcuttur.

!!! uyumluluk "Julia 1.5"
    `mergewith!` Julia 1.5 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> mergewith!(+, d1, d2);

julia> d1
Dict{Int64, Int64} with 3 entries:
  4 => 5
  3 => 4
  1 => 6

julia> mergewith!(-, d1, d1);

julia> d1
Dict{Int64, Int64} with 3 entries:
  4 => 0
  3 => 0
  1 => 0

julia> foldl(mergewith!(+), [d1, d2]; init=Dict{Int64, Int64}())
Dict{Int64, Int64} with 3 entries:
  4 => 5
  3 => 0
  1 => 4
```
