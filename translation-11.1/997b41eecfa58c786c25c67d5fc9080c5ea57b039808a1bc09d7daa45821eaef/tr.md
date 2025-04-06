```
setdiff(s, itrs...)
```

`s` kümesindeki ancak `itrs` içindeki herhangi bir iterable'da olmayan elemanların kümesini oluşturur. Dizilerle sıralamayı korur.

Ayrıca bkz. [`setdiff!`](@ref), [`union`](@ref) ve [`intersect`](@ref).

# Örnekler

```jldoctest
julia> setdiff([1,2,3], [3,4,5])
2-element Vector{Int64}:
 1
 2
```
