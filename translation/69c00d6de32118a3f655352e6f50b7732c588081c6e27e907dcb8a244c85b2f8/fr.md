```
setcpuaffinity(original_command::Cmd, cpus) -> command::Cmd
```

Définissez l'affinité CPU de la `command` par une liste d'ID de CPU (basée sur 1) `cpus`. Passer `cpus = nothing` signifie désactiver l'affinité CPU si la `original_command` en a une.

Cette fonction est prise en charge uniquement sous Linux et Windows. Elle n'est pas prise en charge sous macOS car libuv ne prend pas en charge la définition de l'affinité.

!!! compat "Julia 1.8"
    Cette fonction nécessite au moins Julia 1.8.


# Exemples

Sous Linux, le programme en ligne de commande `taskset` peut être utilisé pour voir comment `setcpuaffinity` fonctionne.

```julia
julia> run(setcpuaffinity(`sh -c 'taskset -p $$'`, [1, 2, 5]));
pid 2273's current affinity mask: 13
```

Notez que la valeur du masque `13` reflète que les premier, deuxième et cinquième bits (en comptant à partir de la position la moins significative) sont activés :

```julia
julia> 0b010011
0x13
```
