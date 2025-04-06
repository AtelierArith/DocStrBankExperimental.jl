```
nzrange(A::AbstractSparseMatrixCSC, col::Integer)
```

Retourne la plage d'indices des valeurs non nulles structurelles d'une colonne de matrice creuse. En conjonction avec [`nonzeros`](@ref) et [`rowvals`](@ref), cela permet d'itérer de manière pratique sur une matrice creuse :

```
A = sparse(I,J,V)
rows = rowvals(A)
vals = nonzeros(A)
m, n = size(A)
for j = 1:n
   for i in nzrange(A, j)
      row = rows[i]
      val = vals[i]
      # effectuer des tours de magie sur les matrices creuses...
   end
end
```

!!! avertissement
    Ajouter ou supprimer des éléments non nuls de la matrice peut invalider le `nzrange`, il ne faut pas modifier la matrice pendant l'itération.

