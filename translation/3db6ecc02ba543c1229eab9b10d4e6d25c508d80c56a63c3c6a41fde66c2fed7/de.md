```
DateTime(f::Function, y[, m, d, h, mi, s]; step=Day(1), limit=10000) -> DateTime
```

Erstellen Sie ein `DateTime` über die Adjuster-API. Der Ausgangspunkt wird aus den bereitgestellten `y, m, d...`-Argumenten konstruiert und wird angepasst, bis `f::Function` `true` zurückgibt. Die Schrittgröße bei der Anpassung kann manuell über das Schlüsselwort `step` bereitgestellt werden. `limit` gibt eine Grenze für die maximale Anzahl von Iterationen an, die die Anpassungs-API verfolgen wird, bevor ein Fehler ausgelöst wird (im Falle, dass `f::Function` niemals erfüllt wird).

# Beispiele

```jldoctest
julia> DateTime(dt -> second(dt) == 40, 2010, 10, 20, 10; step = Second(1))
2010-10-20T10:00:40

julia> DateTime(dt -> hour(dt) == 20, 2010, 10, 20, 10; step = Hour(1), limit = 5)
ERROR: ArgumentError: Anpassungsgrenze erreicht: 5 Iterationen
Stacktrace:
[...]
```
