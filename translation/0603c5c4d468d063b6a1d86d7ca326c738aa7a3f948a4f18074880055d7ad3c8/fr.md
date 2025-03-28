```
fonction
```

Les fonctions sont définies avec le mot-clé `function` :

```julia
function add(a, b)
    return a + b
end
```

Ou la notation courte :

```julia
add(a, b) = a + b
```

L'utilisation du mot-clé [`return`](@ref) est exactement la même que dans d'autres langages, mais est souvent optionnelle. Une fonction sans une instruction `return` explicite renverra la dernière expression dans le corps de la fonction.
