```
givens(f::T, g::T, i1::Integer, i2::Integer) where {T} -> (G::Givens, r::T)
```

Calcule la rotation de Givens `G` et le scalaire `r` tels que pour tout vecteur `x` où

```
x[i1] = f
x[i2] = g
```

le résultat de la multiplication

```
y = G*x
```

a la propriété que

```
y[i1] = r
y[i2] = 0
```

Voir aussi [`LinearAlgebra.Givens`](@ref).
