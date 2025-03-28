```
__init__
```

La fonction `__init__()` dans un module s'exécute immédiatement *après* que le module soit chargé à l'exécution pour la première fois. Elle est appelée une fois, après que toutes les autres instructions dans le module ont été exécutées. Comme elle est appelée après l'importation complète du module, les fonctions `__init__` des sous-modules seront exécutées en premier. Deux utilisations typiques de `__init__` sont l'appel de fonctions d'initialisation à l'exécution de bibliothèques C externes et l'initialisation de constantes globales qui impliquent des pointeurs retournés par des bibliothèques externes. Voir la [section du manuel sur les modules](@ref modules) pour plus de détails.

# Exemples

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```
