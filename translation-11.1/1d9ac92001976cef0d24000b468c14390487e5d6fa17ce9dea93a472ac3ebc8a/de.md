```
@atomic var
@atomic order ex
```

Markieren Sie `var` oder `ex` als atomar ausgeführt, wenn `ex` ein unterstützter Ausdruck ist. Wenn keine `order` angegeben ist, wird standardmäßig :sequentially_consistent verwendet.

```
@atomic a.b.x = new
@atomic a.b.x += addend
@atomic :release a.b.x = new
@atomic :acquire_release a.b.x += addend
```

Führen Sie die auf der rechten Seite ausgedrückte Speicheroperation atomar aus und geben Sie den neuen Wert zurück.

Mit `=` übersetzt sich diese Operation in einen `setproperty!(a.b, :x, new)` Aufruf. Mit jedem Operator übersetzt sich diese Operation ebenfalls in einen `modifyproperty!(a.b, :x, +, addend)[2]` Aufruf.

```
@atomic a.b.x max arg2
@atomic a.b.x + arg2
@atomic max(a.b.x, arg2)
@atomic :acquire_release max(a.b.x, arg2)
@atomic :acquire_release a.b.x + arg2
@atomic :acquire_release a.b.x max arg2
```

Führen Sie die auf der rechten Seite ausgedrückte binäre Operation atomar aus. Speichern Sie das Ergebnis im Feld des ersten Arguments und geben Sie die Werte `(old, new)` zurück.

Diese Operation übersetzt sich in einen `modifyproperty!(a.b, :x, func, arg2)` Aufruf.

Siehe [Per-field atomics](@ref man-atomics) Abschnitt im Handbuch für weitere Details.

# Beispiele

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomic a.x # Feld x von a abrufen, mit sequentieller Konsistenz
1

julia> @atomic :sequentially_consistent a.x = 2 # Feld x von a setzen, mit sequentieller Konsistenz
2

julia> @atomic a.x += 1 # Feld x von a inkrementieren, mit sequentieller Konsistenz
3

julia> @atomic a.x + 1 # Feld x von a inkrementieren, mit sequentieller Konsistenz
3 => 4

julia> @atomic a.x # Feld x von a abrufen, mit sequentieller Konsistenz
4

julia> @atomic max(a.x, 10) # Feld x von a auf den Maximalwert ändern, mit sequentieller Konsistenz
4 => 10

julia> @atomic a.x max 5 # erneut Feld x von a auf den Maximalwert ändern, mit sequentieller Konsistenz
10 => 10
```

!!! compat "Julia 1.7"
    Diese Funktionalität erfordert mindestens Julia 1.7.

