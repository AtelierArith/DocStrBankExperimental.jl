```
flatten(iter)
```

Bir iteratörün iteratörler ürettiği durumlarda, bu iteratörlerin elemanlarını üreten bir iteratör döndürün. Başka bir deyişle, argüman iteratörünün elemanları birleştirilir.

# Örnekler

```jldoctest
julia> collect(Iterators.flatten((1:2, 8:9)))
4-element Vector{Int64}:
 1
 2
 8
 9

julia> [(x,y) for x in 0:1 for y in 'a':'c']  # Iterators.flatten içeren jeneratörleri toplar
6-element Vector{Tuple{Int64, Char}}:
 (0, 'a')
 (0, 'b')
 (0, 'c')
 (1, 'a')
 (1, 'b')
 (1, 'c')
```
