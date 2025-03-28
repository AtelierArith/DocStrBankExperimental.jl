```
@macroexpand [mod,] ex
```

Renvoie l'expression équivalente avec toutes les macros supprimées (développées). Si deux arguments sont fournis, le premier est le module à évaluer.

Il existe des différences entre `@macroexpand` et [`macroexpand`](@ref).

  * Alors que [`macroexpand`](@ref) prend un argument clé `recursive`, `@macroexpand` est toujours récursif. Pour une version non récursive des macros, voir [`@macroexpand1`](@ref).
  * Alors que [`macroexpand`](@ref) a un argument `module` explicite, `@macroexpand` se développe toujours par rapport au module dans lequel il est appelé.

Ceci est mieux illustré dans l'exemple suivant :

```julia-repl
julia> module M
           macro m()
               1
           end
           function f()
               (@macroexpand(@m),
                macroexpand(M, :(@m)),
                macroexpand(Main, :(@m))
               )
           end
       end
M

julia> macro m()
           2
       end
@m (macro with 1 method)

julia> M.f()
(1, 1, 2)
```

Avec `@macroexpand`, l'expression se développe là où `@macroexpand` apparaît dans le code (module `M` dans l'exemple). Avec `macroexpand`, l'expression se développe dans le module donné comme premier argument.

!!! compat "Julia 1.11"
    La forme à deux arguments nécessite au moins Julia 1.11.

