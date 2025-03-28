```
mapfoldl(f, op, itr; [init])
```

Comme [`mapreduce`](@ref), mais avec une associativité gauche garantie, comme dans [`foldl`](@ref). Si fourni, l'argument clé `init` sera utilisé exactement une fois. En général, il sera nécessaire de fournir `init` pour travailler avec des collections vides.
