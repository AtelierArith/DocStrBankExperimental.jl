```
@macroexpand [mod,] ex
```

Geben Sie den entsprechenden Ausdruck mit allen entfernten (erweiterten) Makros zurück. Wenn zwei Argumente angegeben sind, ist das erste das Modul, das ausgewertet werden soll.

Es gibt Unterschiede zwischen `@macroexpand` und [`macroexpand`](@ref).

  * Während [`macroexpand`](@ref) ein Schlüsselwortargument `recursive` hat, ist `@macroexpand` immer rekursiv. Für eine nicht rekursive Makroversion siehe [`@macroexpand1`](@ref).
  * Während [`macroexpand`](@ref) ein explizites `module`-Argument hat, erweitert `@macroexpand` immer im Hinblick auf das Modul, in dem es aufgerufen wird.

Dies lässt sich am besten im folgenden Beispiel sehen:

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
@m (Makro mit 1 Methode)

julia> M.f()
(1, 1, 2)
```

Mit `@macroexpand` wird der Ausdruck dort erweitert, wo `@macroexpand` im Code erscheint (Modul `M` im Beispiel). Mit `macroexpand` wird der Ausdruck im Modul erweitert, das als erstes Argument angegeben ist.

!!! compat "Julia 1.11"
    Die Zwei-Argument-Form erfordert mindestens Julia 1.11.

