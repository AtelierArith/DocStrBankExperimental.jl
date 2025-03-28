```
@cfunction(callable, ReturnType, (ArgumentTypes...,)) -> Ptr{Cvoid}
@cfunction($callable, ReturnType, (ArgumentTypes...,)) -> CFunction
```

Générez un pointeur de fonction appelable en C à partir de la fonction Julia `callable` pour la signature de type donnée. Pour passer la valeur de retour à un `ccall`, utilisez le type d'argument `Ptr{Cvoid}` dans la signature.

Notez que le tuple de types d'argument doit être un tuple littéral, et non une variable ou une expression de type tuple (bien qu'il puisse inclure une expression splat). Et ces arguments seront évalués dans le scope global pendant le temps de compilation (et non différés jusqu'à l'exécution). Ajouter un '$' devant l'argument de fonction change cela pour créer plutôt une fermeture d'exécution sur la variable locale `callable` (ceci n'est pas supporté sur toutes les architectures).

Voir [section du manuel sur l'utilisation de ccall et cfunction](@ref Calling-C-and-Fortran-Code).

# Exemples

```julia-repl
julia> function foo(x::Int, y::Int)
           return x + y
       end

julia> @cfunction(foo, Int, (Int, Int))
Ptr{Cvoid} @0x000000001b82fcd0
```
