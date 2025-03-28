```
finalement
```

Exécutez du code lorsqu'un bloc de code donné se termine, peu importe comment il se termine. Par exemple, voici comment nous pouvons garantir qu'un fichier ouvert est fermé :

```julia
f = open("file")
try
    operate_on_file(f)
finally
    close(f)
end
```

Lorsque le contrôle quitte le bloc [`try`](@ref) (par exemple, en raison d'un [`return`](@ref), ou simplement en se terminant normalement), [`close(f)`](@ref) sera exécuté. Si le bloc `try` se termine en raison d'une exception, l'exception continuera à se propager. Un bloc `catch` peut également être combiné avec `try` et `finally`. Dans ce cas, le bloc `finally` s'exécutera après que `catch` ait géré l'erreur.
