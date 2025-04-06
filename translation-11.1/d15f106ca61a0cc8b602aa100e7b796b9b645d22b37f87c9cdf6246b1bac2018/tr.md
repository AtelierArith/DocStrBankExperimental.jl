```
dot(x, A, y)
```

İki vektör `x` ve `y` arasında, `A*y` ara sonucunu saklamadan genel bir nokta çarpımı `dot(x, A*y)` hesaplar. İki argümanlı [`dot(_,_)`](@ref) gibi, bu da özyinelemeli olarak çalışır. Ayrıca, karmaşık vektörler için, ilk vektör konjuge edilir.

!!! compat "Julia 1.4"
    Üç argümanlı `dot`, en az Julia 1.4 gerektirir.


# Örnekler

```jldoctest
julia> dot([1; 1], [1 2; 3 4], [2; 3])
26

julia> dot(1:5, reshape(1:25, 5, 5), 2:6)
4850

julia> ⋅(1:5, reshape(1:25, 5, 5), 2:6) == dot(1:5, reshape(1:25, 5, 5), 2:6)
true
```
