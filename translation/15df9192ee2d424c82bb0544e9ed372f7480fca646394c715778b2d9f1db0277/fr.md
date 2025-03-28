```
unsafe_replace!(p::Ptr{T}, expected, desired,
               [success_order::Symbol[, fail_order::Symbol=success_order]]) -> (; old, success::Bool)
```

Ces opérations effectuent de manière atomique les opérations pour obtenir et conditionnellement définir une adresse mémoire à une valeur donnée. Si cela est pris en charge par le matériel, cela peut être optimisé pour l'instruction matérielle appropriée, sinon son exécution sera similaire à :

```
y = unsafe_load(p, fail_order)
ok = y === expected
if ok
    unsafe_store!(p, desired, success_order)
end
return (; old = y, success = ok)
```

Le préfixe `unsafe` sur cette fonction indique qu'aucune validation n'est effectuée sur le pointeur `p` pour s'assurer qu'il est valide. Comme en C, le programmeur est responsable de s'assurer que la mémoire référencée n'est pas libérée ou collectée par le ramasse-miettes lors de l'invocation de cette fonction. Une utilisation incorrecte peut provoquer un segfault dans votre programme.

!!! compat "Julia 1.10"
    Cette fonction nécessite au moins Julia 1.10.


Voir aussi : [`replaceproperty!`](@ref Base.replaceproperty!), [`atomic`](@ref)
