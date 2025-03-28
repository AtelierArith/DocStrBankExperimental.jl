```
@deprecate old new [export_old=true]
```

Veraltet die Methode `old` und gibt den Ersatzaufruf `new` an, indem ein neuer Methode `old` mit der angegebenen Signatur im Prozess definiert wird.

Um zu verhindern, dass `old` exportiert wird, setzen Sie `export_old` auf `false`.

Siehe auch [`Base.depwarn()`](@ref).

!!! compat "Julia 1.5"
    Ab Julia 1.5 drucken Funktionen, die durch `@deprecate` definiert sind, keine Warnung aus, wenn `julia` ohne das gesetzte `--depwarn=yes`-Flag ausgeführt wird, da der Standardwert der `--depwarn`-Option `no` ist. Die Warnungen werden aus Tests ausgegeben, die von `Pkg.test()` ausgeführt werden.


# Beispiele

```jldoctest
julia> @deprecate old(x) new(x)
old (generische Funktion mit 1 Methode)

julia> @deprecate old(x) new(x) false
old (generische Funktion mit 1 Methode)
```

Aufrufe von `@deprecate` ohne explizite Typannotationen definieren veraltete Methoden, die eine beliebige Anzahl von Positions- und Schlüsselwortargumenten vom Typ `Any` akzeptieren.

!!! compat "Julia 1.9"
    Schlüsselwortargumente werden weitergeleitet, wenn es keine explizite Typannotation gibt, ab Julia 1.9. Für ältere Versionen können Sie Positions- und Schlüsselwortargumente manuell weiterleiten, indem Sie `@deprecate old(args...; kwargs...) new(args...; kwargs...)` verwenden.


Um die Veraltung auf eine bestimmte Signatur zu beschränken, annotieren Sie die Argumente von `old`. Zum Beispiel,

```jldoctest; filter = r"@ .*"a
julia> new(x::Int) = x;

julia> new(x::Float64) = 2x;

julia> @deprecate old(x::Int) new(x);

julia> methods(old)
# 1 Methode für die generische Funktion "old" aus Main:
 [1] old(x::Int64)
     @ deprecated.jl:94
```

wird eine Methode `old(x::Int)` definieren und veralten, die `new(x::Int)` spiegelt, aber die Methode `old(x::Float64)` weder definiert noch veraltet.
