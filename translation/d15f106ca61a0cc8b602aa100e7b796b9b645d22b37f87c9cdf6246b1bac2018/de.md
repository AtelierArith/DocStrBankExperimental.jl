```
dot(x, A, y)
```

Berechne das verallgemeinerte Skalarprodukt `dot(x, A*y)` zwischen zwei Vektoren `x` und `y`, ohne das Zwischenergebnis von `A*y` zu speichern. Wie beim zweiarugumentigen [`dot(_,_)`](@ref) wirkt dies rekursiv. Darüber hinaus wird für komplexe Vektoren der erste Vektor konjugiert.

!!! compat "Julia 1.4"
    Drei-argumentige `dot` erfordert mindestens Julia 1.4.


# Beispiele

```jldoctest
julia> dot([1; 1], [1 2; 3 4], [2; 3])
26

julia> dot(1:5, reshape(1:25, 5, 5), 2:6)
4850

julia> ⋅(1:5, reshape(1:25, 5, 5), 2:6) == dot(1:5, reshape(1:25, 5, 5), 2:6)
true
```
