```
WeakKeyDict([itr])
```

`WeakKeyDict()` construit une table de hachage où les clés sont des références faibles à des objets qui peuvent être collectés par le ramasse-miettes même lorsqu'ils sont référencés dans une table de hachage.

Voir [`Dict`](@ref) pour plus d'aide. Notez que, contrairement à [`Dict`](@ref), `WeakKeyDict` ne convertit pas les clés lors de l'insertion, car cela impliquerait que l'objet clé n'était référencé nulle part avant l'insertion.

Voir aussi [`WeakRef`](@ref).
