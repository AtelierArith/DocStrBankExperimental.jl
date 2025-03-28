```
unsafe_store!(p::Ptr{T}, x, i::Integer=1)
unsafe_store!(p::Ptr{T}, x, order::Symbol)
unsafe_store!(p::Ptr{T}, x, i::Integer, order::Symbol)
```

Stocke une valeur de type `T` à l'adresse du `i`-ème élément (indexé à partir de 1) commençant à `p`. Cela équivaut à l'expression C `p[i-1] = x`. En option, un ordre de mémoire atomique peut être fourni.

Le préfixe `unsafe` sur cette fonction indique qu'aucune validation n'est effectuée sur le pointeur `p` pour s'assurer qu'il est valide. Comme en C, le programmeur est responsable de s'assurer que la mémoire référencée n'est pas libérée ou collectée par le ramasse-miettes pendant l'invocation de cette fonction. Une utilisation incorrecte peut provoquer un segfault dans votre programme. Contrairement à C, stocker une région de mémoire allouée comme un type différent peut être valide à condition que les types soient compatibles.

!!! compat "Julia 1.10"
    L'argument `order` est disponible depuis Julia 1.10.


Voir aussi : [`atomic`](@ref)
