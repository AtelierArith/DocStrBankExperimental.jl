```
unsafe_modify!(p::Ptr{T}, op, x, [order::Symbol]) -> Pair
```

Ces opérations effectuent de manière atomique les opérations pour obtenir et définir une adresse mémoire après avoir appliqué la fonction `op`. Si cela est pris en charge par le matériel (par exemple, l'incrémentation atomique), cela peut être optimisé vers l'instruction matérielle appropriée, sinon son exécution sera similaire à :

```
y = unsafe_load(p)
z = op(y, x)
unsafe_store!(p, z)
return y => z
```

Le préfixe `unsafe` sur cette fonction indique qu'aucune validation n'est effectuée sur le pointeur `p` pour s'assurer qu'il est valide. Comme en C, le programmeur est responsable de s'assurer que la mémoire référencée n'est pas libérée ou collectée par le ramasse-miettes lors de l'invocation de cette fonction. Une utilisation incorrecte peut provoquer un segfault dans votre programme.

!!! compat "Julia 1.10"
    Cette fonction nécessite au moins Julia 1.10.


Voir aussi : [`modifyproperty!`](@ref Base.modifyproperty!), [`atomic`](@ref)
