```
@macroexpand [mod,] ex
```

Devuelve la expresión equivalente con todas las macros eliminadas (expandidas). Si se proporcionan dos argumentos, el primero es el módulo en el que se evalúa.

Hay diferencias entre `@macroexpand` y [`macroexpand`](@ref).

  * Mientras que [`macroexpand`](@ref) toma un argumento de palabra clave `recursive`, `@macroexpand` es siempre recursivo. Para una versión de macro no recursiva, consulte [`@macroexpand1`](@ref).
  * Mientras que [`macroexpand`](@ref) tiene un argumento `module` explícito, `@macroexpand` siempre expande con respecto al módulo en el que se llama.

Esto se ve mejor en el siguiente ejemplo:

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

Con `@macroexpand` la expresión se expande donde aparece `@macroexpand` en el código (módulo `M` en el ejemplo). Con `macroexpand` la expresión se expande en el módulo dado como primer argumento.

!!! compat "Julia 1.11"
    La forma de dos argumentos requiere al menos Julia 1.11.

