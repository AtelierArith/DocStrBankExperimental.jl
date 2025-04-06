```
Experimental.show_error_hints(io, ex, args...)
```

Ruft alle Handler von [`Experimental.register_error_hint`](@ref) für den bestimmten Ausnahmetyp `typeof(ex)` auf. `args` muss alle anderen Argumente enthalten, die vom Handler für diesen Typ erwartet werden.

!!! compat "Julia 1.5"
    Benutzerdefinierte Fehlerhinweise sind seit Julia 1.5 verfügbar.


!!! warning
    Diese Schnittstelle ist experimentell und kann ohne Vorankündigung geändert oder entfernt werden.

