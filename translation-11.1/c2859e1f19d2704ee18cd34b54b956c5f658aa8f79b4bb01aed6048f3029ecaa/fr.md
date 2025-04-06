```
finalizer(f, x)
```

Enregistre une fonction `f(x)` à appeler lorsqu'il n'y a plus de références accessibles par le programme à `x`, et retourne `x`. Le type de `x` doit être un `mutable struct`, sinon la fonction lèvera une exception.

`f` ne doit pas provoquer de changement de tâche, ce qui exclut la plupart des opérations d'E/S telles que `println`. Utiliser la macro `@async` (pour différer le changement de contexte à l'extérieur du finaliseur) ou `ccall` pour invoquer directement des fonctions d'E/S en C peut être utile à des fins de débogage.

Notez qu'il n'y a pas d'âge de monde garanti pour l'exécution de `f`. Il peut être appelé dans l'âge de monde dans lequel le finaliseur a été enregistré ou dans un âge de monde ultérieur.

# Exemples

```julia
finalizer(my_mutable_struct) do x
    @async println("Finalizing $x.")
end

finalizer(my_mutable_struct) do x
    ccall(:jl_safe_printf, Cvoid, (Cstring, Cstring), "Finalizing %s.", repr(x))
end
```

Un finaliseur peut être enregistré lors de la construction de l'objet. Dans l'exemple suivant, notez que nous comptons implicitement sur le finaliseur retournant le `mutable struct` nouvellement créé `x`.

```julia
mutable struct MyMutableStruct
    bar
    function MyMutableStruct(bar)
        x = new(bar)
        f(t) = @async println("Finalizing $t.")
        finalizer(f, x)
    end
end
```
