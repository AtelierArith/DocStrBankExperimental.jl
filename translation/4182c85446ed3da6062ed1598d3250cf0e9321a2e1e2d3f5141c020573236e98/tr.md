```
IdSet{T}([itr])
IdSet()
```

IdSet{T}() bir küme oluşturur (bkz. [`Set`](@ref)) ve `T` türündeki değerlerle eşitlik için `===` kullanır.

Aşağıdaki örnekte, değerlerin hepsi `isequal` olduğu için sıradan `Set` içinde üzerine yazılır. `IdSet` ise `===` ile karşılaştırma yapar ve böylece 3 farklı değeri korur.

# Örnekler

```jldoctest; filter = r"\n\s*(1|1\.0|true)"
julia> Set(Any[true, 1, 1.0])
Set{Any} with 1 element:
  1.0

julia> IdSet{Any}(Any[true, 1, 1.0])
IdSet{Any} with 3 elements:
  1.0
  1
  true
```
