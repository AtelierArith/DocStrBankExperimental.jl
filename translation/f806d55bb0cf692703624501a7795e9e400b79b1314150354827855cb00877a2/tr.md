```
replace(A, old_new::Pair...; [count::Integer])
```

Koleksiyonu `A`'nın bir kopyasını döndürür; burada, `old=>new` çiftlerinden her biri için, `old`'un tüm örnekleri `new` ile değiştirilir. Eşitlik [`isequal`](@ref) kullanılarak belirlenir. Eğer `count` belirtilmişse, o zaman toplamda en fazla `count` örneği değiştirilir.

Sonucun eleman tipi, `A`'nın eleman tipi ve çiftlerdeki `new` değerlerinin tiplerine dayanarak terfi kullanılarak seçilir (bkz. [`promote_type`](@ref)). Eğer `count` atlanırsa ve `A`'nın eleman tipi bir `Union` ise, sonuçtaki eleman tipi, farklı bir tipteki değerlerle değiştirilen tekil tipleri içermeyecektir: örneğin, `Union{T,Missing}` eğer `missing` bir değerle değiştirilirse `T` haline gelecektir.

Ayrıca bkz. [`replace!`](@ref), [`splice!`](@ref), [`delete!`](@ref), [`insert!`](@ref).

!!! compat "Julia 1.7"
    Bir `Tuple`'ın elemanlarını değiştirmek için 1.7 sürümü gereklidir.


# Örnekler

```jldoctest
julia> replace([1, 2, 1, 3], 1=>0, 2=>4, count=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace([1, missing], missing=>0)
2-element Vector{Int64}:
 1
 0
```
