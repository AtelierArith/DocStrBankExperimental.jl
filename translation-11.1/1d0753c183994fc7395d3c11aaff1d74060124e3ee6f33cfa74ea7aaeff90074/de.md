```
Date(f::Function, y[, m, d]; step=Day(1), limit=10000) -> Date
```

Erstellen Sie ein `Date` über die Adjuster-API. Der Ausgangspunkt wird aus den bereitgestellten `y, m, d`-Argumenten konstruiert und wird angepasst, bis `f::Function` `true` zurückgibt. Die Schrittgröße bei der Anpassung kann manuell über das Schlüsselwort `step` bereitgestellt werden. `limit` gibt eine Grenze für die maximale Anzahl von Iterationen an, die die Anpassungs-API verfolgen wird, bevor ein Fehler ausgelöst wird (vorausgesetzt, dass `f::Function` niemals erfüllt wird).

# Beispiele

```jldoctest
julia> Date(date -> week(date) == 20, 2010, 01, 01)
2010-05-17

julia> Date(date -> year(date) == 2010, 2000, 01, 01)
2010-01-01

julia> Date(date -> month(date) == 10, 2000, 01, 01; limit = 5)
ERROR: ArgumentError: Anpassungsgrenze erreicht: 5 Iterationen
Stacktrace:
[...]
```
