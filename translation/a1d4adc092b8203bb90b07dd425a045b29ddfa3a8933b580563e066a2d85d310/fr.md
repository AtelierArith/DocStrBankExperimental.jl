```
Experimental.register_error_hint(handler, exceptiontype)
```

Enregistrez une fonction de "sugestion" `handler(io, exception)` qui peut suggérer des moyens potentiels pour les utilisateurs de contourner les erreurs. `handler` doit examiner `exception` pour voir si les conditions appropriées pour une suggestion sont remplies, et si c'est le cas, générer une sortie vers `io`. Les packages doivent appeler `register_error_hint` depuis leur fonction `__init__`.

Pour des types d'exception spécifiques, `handler` doit accepter des arguments supplémentaires :

  * `MethodError` : fournir `handler(io, exc::MethodError, argtypes, kwargs)`, qui divise les arguments combinés en arguments positionnels et en arguments de mot-clé.

Lors de l'émission d'une suggestion, la sortie doit généralement commencer par `\n`.

Si vous définissez des types d'exception personnalisés, votre méthode `showerror` peut prendre en charge les suggestions en appelant [`Experimental.show_error_hints`](@ref).

# Exemples

```
julia> module Hinter

       only_int(x::Int)      = 1
       any_number(x::Number) = 2

       function __init__()
           Base.Experimental.register_error_hint(MethodError) do io, exc, argtypes, kwargs
               if exc.f == only_int
                    # La couleur n'est pas nécessaire, c'est juste pour montrer que c'est possible.
                    print(io, "\nVouliez-vous appeler ")
                    printstyled(io, "`any_number`?", color=:cyan)
               end
           end
       end

       end
```

Alors si vous appelez `Hinter.only_int` sur quelque chose qui n'est pas un `Int` (déclenchant ainsi un `MethodError`), cela émet la suggestion :

```
julia> Hinter.only_int(1.0)
ERROR: MethodError: no method matching only_int(::Float64)
La fonction `only_int` existe, mais aucune méthode n'est définie pour cette combinaison de types d'arguments.
Vouliez-vous appeler `any_number` ?
Les candidats les plus proches sont :
    ...
```

!!! compat "Julia 1.5"
    Les suggestions d'erreurs personnalisées sont disponibles depuis Julia 1.5.


!!! warning
    Cette interface est expérimentale et sujette à des changements ou à une suppression sans préavis. Pour vous protéger contre les changements, envisagez de mettre toutes les inscriptions à l'intérieur d'un bloc `if isdefined(Base.Experimental, :register_error_hint) ... end`.

