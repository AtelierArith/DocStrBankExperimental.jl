```
range(start, stop, length)
range(start, stop; length, step)
range(start; length, stop, step)
range(;start, length, stop, step)
```

Konstruiere ein spezialisiertes Array mit gleichmäßig verteilten Elementen und optimierter Speicherung (ein [`AbstractRange`](@ref)) aus den Argumenten. Mathematisch wird ein Bereich eindeutig durch drei der Werte `start`, `step`, `stop` und `length` bestimmt. Gültige Aufrufe von range sind:

  * Rufe `range` mit drei der Werte `start`, `step`, `stop`, `length` auf.
  * Rufe `range` mit zwei der Werte `start`, `stop`, `length` auf. In diesem Fall wird `step` als eins angenommen. Wenn beide Argumente Ganzzahlen sind, wird ein [`UnitRange`](@ref) zurückgegeben.
  * Rufe `range` mit einem der Werte `stop` oder `length` auf. `start` und `step` werden als eins angenommen.

Siehe Erweiterte Hilfe für zusätzliche Details zum zurückgegebenen Typ. Siehe auch [`logrange`](@ref) für logarithmisch verteilte Punkte.

# Beispiele

```jldoctest
julia> range(1, length=100)
1:100

julia> range(1, stop=100)
1:100

julia> range(1, step=5, length=100)
1:5:496

julia> range(1, step=5, stop=100)
1:5:96

julia> range(1, 10, length=101)
1.0:0.09:10.0

julia> range(1, 100, step=5)
1:5:96

julia> range(stop=10, length=5)
6:10

julia> range(stop=10, step=1, length=5)
6:1:10

julia> range(start=1, step=1, stop=10)
1:1:10

julia> range(; length = 10)
Base.OneTo(10)

julia> range(; stop = 6)
Base.OneTo(6)

julia> range(; stop = 6.5)
1.0:1.0:6.0
```

Wenn `length` nicht angegeben ist und `stop - start` kein ganzzahliges Vielfaches von `step` ist, wird ein Bereich erzeugt, der vor `stop` endet.

```jldoctest
julia> range(1, 3.5, step=2)
1.0:2.0:3.0
```

Besondere Sorgfalt wird darauf verwendet, sicherzustellen, dass Zwischenwerte rational berechnet werden. Um diesen induzierten Overhead zu vermeiden, siehe den [`LinRange`](@ref) Konstruktor.

!!! compat "Julia 1.1"
    `stop` als positionsgebundenes Argument erfordert mindestens Julia 1.1.


!!! compat "Julia 1.7"
    Die Versionen ohne Schlüsselwortargumente und `start` als Schlüsselwortargument erfordern mindestens Julia 1.7.


!!! compat "Julia 1.8"
    Die Versionen mit `stop` als einzigem Schlüsselwortargument oder `length` als einzigem Schlüsselwortargument erfordern mindestens Julia 1.8.


# Erweiterte Hilfe

`range` erzeugt ein `Base.OneTo`, wenn die Argumente Ganzzahlen sind und

  * Nur `length` angegeben ist
  * Nur `stop` angegeben ist

`range` erzeugt einen `UnitRange`, wenn die Argumente Ganzzahlen sind und

  * Nur `start` und `stop` angegeben sind
  * Nur `length` und `stop` angegeben sind

Ein `UnitRange` wird nicht erzeugt, wenn `step` angegeben ist, selbst wenn es als eins angegeben ist.
