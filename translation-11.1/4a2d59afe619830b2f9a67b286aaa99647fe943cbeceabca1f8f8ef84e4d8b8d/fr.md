```
mapfoldr(f, op, itr; [init])
```

Comme [`mapreduce`](@ref), mais avec une associativité à droite garantie, comme dans [`foldr`](@ref). Si fourni, l'argument clé `init` sera utilisé exactement une fois. En général, il sera nécessaire de fournir `init` pour travailler avec des collections vides.
