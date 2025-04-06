```
ENV
```

Verweis auf das Singleton `EnvDict`, das eine Dictionary-Schnittstelle zu Systemumgebungsvariablen bereitstellt.

(Unter Windows sind Systemumgebungsvariablen nicht groß-/kleinschreibungssensitiv, und `ENV` konvertiert entsprechend alle Schlüssel in Großbuchstaben zur Anzeige, Iteration und Kopie. Tragfähiger Code sollte sich nicht auf die Fähigkeit verlassen, Variablen durch Groß- und Kleinschreibung zu unterscheiden, und sollte vorsichtig sein, dass das Setzen einer scheinbar kleingeschriebenen Variablen zu einem Großbuchstaben-`ENV`-Schlüssel führen kann.)

!!! warning
    Die Veränderung der Umgebung ist nicht threadsicher.


# Beispiele

```julia-repl
julia> ENV
Base.EnvDict mit "50" Einträgen:
  "SECURITYSESSIONID"            => "123"
  "USER"                         => "benutzername"
  "MallocNanoZone"               => "0"
  ⋮                              => ⋮

julia> ENV["JULIA_EDITOR"] = "vim"
"vim"

julia> ENV["JULIA_EDITOR"]
"vim"
```

Siehe auch: [`withenv`](@ref), [`addenv`](@ref).
