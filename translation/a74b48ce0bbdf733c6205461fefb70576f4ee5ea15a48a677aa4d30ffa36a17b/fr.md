```
Printf.format(f::Printf.Format, args...) => String
Printf.format(io::IO, f::Printf.Format, args...)
```

Appliquez un objet de format printf `f` aux `args` fournis et renvoyez la chaîne formatée (1ère méthode), ou imprimez directement sur un objet `io` (2ème méthode). Voir [`@printf`](@ref) pour plus de détails sur le support de C `printf`.
