```
@. expr
```

Konvertiere jeden Funktionsaufruf oder Operator in `expr` in einen "Punktaufruf" (z. B. konvertiere `f(x)` in `f.(x)`) und konvertiere jede Zuweisung in `expr` in eine "Punktzuweisung" (z. B. konvertiere `+=` in `.+=`).

Wenn du *vermeiden* möchtest, Punkte für ausgewählte Funktionsaufrufe in `expr` hinzuzufügen, füge diese Funktionsaufrufe mit `$` ein. Zum Beispiel ist `@. sqrt(abs($sort(x)))` äquivalent zu `sqrt.(abs.(sort(x)))` (kein Punkt für `sort`).

(`@.` ist äquivalent zu einem Aufruf von `@__dot__`.)

# Beispiele

```jldoctest
julia> x = 1.0:3.0; y = similar(x);

julia> @. y = x + 3 * sin(x)
3-element Vector{Float64}:
 3.5244129544236893
 4.727892280477045
 3.4233600241796016
```
