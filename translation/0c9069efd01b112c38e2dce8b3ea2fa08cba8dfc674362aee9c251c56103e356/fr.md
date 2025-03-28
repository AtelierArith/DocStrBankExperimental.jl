```
normalize!(a::AbstractArray, p::Real=2)
```

Normalisez le tableau `a` sur place de sorte que sa norme `p` soit égale à l'unité, c'est-à-dire `norm(a, p) == 1`. Voir aussi [`normalize`](@ref) et [`norm`](@ref).
