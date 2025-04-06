```
Time(f::Function, h, mi=0; step::Period=Second(1), limit::Int=10000)
Time(f::Function, h, mi, s; step::Period=Millisecond(1), limit::Int=10000)
Time(f::Function, h, mi, s, ms; step::Period=Microsecond(1), limit::Int=10000)
Time(f::Function, h, mi, s, ms, us; step::Period=Nanosecond(1), limit::Int=10000)
```

Erstellen Sie eine `Time` über die Adjuster-API. Der Ausgangspunkt wird aus den bereitgestellten `h, mi, s, ms, us`-Argumenten konstruiert und wird angepasst, bis `f::Function` `true` zurückgibt. Die Schrittgröße bei der Anpassung kann manuell über das Schlüsselwort `step` bereitgestellt werden. `limit` gibt eine Grenze für die maximale Anzahl von Iterationen an, die die Anpassungs-API verfolgen wird, bevor ein Fehler ausgelöst wird (im Falle, dass `f::Function` niemals erfüllt wird). Beachten Sie, dass der Standard-Schritt so angepasst wird, dass eine höhere Präzision für die gegebenen Argumente ermöglicht wird; d.h. wenn Stunden-, Minuten- und Sekundenargumente bereitgestellt werden, wird der Standard-Schritt `Millisecond(1)` anstelle von `Second(1)` sein.

# Beispiele

```jldoctest
julia> Time(t -> minute(t) == 30, 20)
20:30:00

julia> Time(t -> minute(t) == 0, 20)
20:00:00

julia> Time(t -> hour(t) == 10, 3; limit = 5)
ERROR: ArgumentError: Anpassungsgrenze erreicht: 5 Iterationen
Stacktrace:
[...]
```
