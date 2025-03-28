```
Threads.atomic_cas!(x::Atomic{T}, cmp::T, newval::T) where T
```

Compare et définit `x` de manière atomique

Compare atomiquement la valeur dans `x` avec `cmp`. Si elles sont égales, écrit `newval` dans `x`. Sinon, laisse `x` non modifié. Renvoie l'ancienne valeur dans `x`. En comparant la valeur renvoyée à `cmp` (via `===`), on sait si `x` a été modifié et contient maintenant la nouvelle valeur `newval`.

Pour plus de détails, voir l'instruction `cmpxchg` de LLVM.

Cette fonction peut être utilisée pour implémenter des sémantiques transactionnelles. Avant la transaction, on enregistre la valeur dans `x`. Après la transaction, la nouvelle valeur n'est stockée que si `x` n'a pas été modifié entre-temps.

# Exemples

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 4, 2);

julia> x
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 3, 2);

julia> x
Base.Threads.Atomic{Int64}(2)
```
