```
Experimental.register_error_hint(handler, exceptiontype)
```

Registrieren Sie eine "Hinweis"-Funktion `handler(io, exception)`, die potenzielle Möglichkeiten vorschlagen kann, wie Benutzer Fehler umgehen können. `handler` sollte `exception` untersuchen, um festzustellen, ob die Bedingungen für einen Hinweis erfüllt sind, und falls ja, Ausgaben an `io` generieren. Pakete sollten `register_error_hint` innerhalb ihrer `__init__`-Funktion aufrufen.

Für spezifische Ausnahmetypen ist es erforderlich, dass `handler` zusätzliche Argumente akzeptiert:

  * `MethodError`: Stellen Sie `handler(io, exc::MethodError, argtypes, kwargs)` bereit, das die kombinierten Argumente in Positions- und Schlüsselwortargumente aufteilt.

Beim Ausgeben eines Hinweises sollte die Ausgabe typischerweise mit `\n` beginnen.

Wenn Sie benutzerdefinierte Ausnahmetypen definieren, kann Ihre `showerror`-Methode Hinweise unterstützen, indem sie [`Experimental.show_error_hints`](@ref) aufruft.

# Beispiele

```
julia> module Hinter

       only_int(x::Int)      = 1
       any_number(x::Number) = 2

       function __init__()
           Base.Experimental.register_error_hint(MethodError) do io, exc, argtypes, kwargs
               if exc.f == only_int
                    # Farbe ist nicht notwendig, dies dient nur dazu, zu zeigen, dass es möglich ist.
                    print(io, "\nMeinten Sie, ")
                    printstyled(io, "`any_number` zu rufen?", color=:cyan)
               end
           end
       end

       end
```

Wenn Sie dann `Hinter.only_int` mit etwas aufrufen, das kein `Int` ist (und damit einen `MethodError` auslöst), gibt es den Hinweis aus:

```
julia> Hinter.only_int(1.0)
ERROR: MethodError: no method matching only_int(::Float64)
Die Funktion `only_int` existiert, aber keine Methode ist für diese Kombination von Argumenttypen definiert.
Meinten Sie, `any_number` zu rufen?
Nächste Kandidaten sind:
    ...
```

!!! compat "Julia 1.5"
    Benutzerdefinierte Fehlerhinweise sind seit Julia 1.5 verfügbar.


!!! warning
    Diese Schnittstelle ist experimentell und kann ohne Vorankündigung geändert oder entfernt werden. Um sich gegen Änderungen abzusichern, sollten Sie alle Registrierungen in einen `if isdefined(Base.Experimental, :register_error_hint) ... end`-Block einfügen.

