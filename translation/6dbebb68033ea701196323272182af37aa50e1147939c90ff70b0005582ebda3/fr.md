```
lock(f::Function, lock)
```

Acquérir le `lock`, exécuter `f` avec le `lock` maintenu, et libérer le `lock` lorsque `f` retourne. Si le lock est déjà verrouillé par une autre tâche/fil, attendez qu'il devienne disponible.

Lorsque cette fonction retourne, le `lock` a été libéré, donc l'appelant ne doit pas tenter de le `unlock`.

Voir aussi : [`@lock`](@ref).

!!! compat "Julia 1.7"
    Utiliser un [`Channel`](@ref) comme deuxième argument nécessite Julia 1.7 ou version ultérieure.

