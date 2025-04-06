```
@test_throws exception expr
```

Testet, dass der Ausdruck `expr` `exception` auslöst. Die Ausnahme kann entweder einen Typ, einen String, einen regulären Ausdruck oder eine Liste von Strings, die in der angezeigten Fehlermeldung vorkommen, eine Übereinstimmungsfunktion oder einen Wert angeben (der auf Gleichheit durch den Vergleich von Feldern getestet wird). Beachten Sie, dass `@test_throws` keine abschließende Schlüsselwortform unterstützt.

!!! compat "Julia 1.8"
    Die Möglichkeit, etwas anderes als einen Typ oder einen Wert als `exception` anzugeben, erfordert Julia v1.8 oder höher.


# Beispiele

```jldoctest
julia> @test_throws BoundsError [1, 2, 3][4]
Test bestanden
      Ausgelöst: BoundsError

julia> @test_throws DimensionMismatch [1, 2, 3] + [1, 2]
Test bestanden
      Ausgelöst: DimensionMismatch

julia> @test_throws "Versuchen Sie sqrt(Complex" sqrt(-1)
Test bestanden
     Nachricht: "DomainError mit -1.0:\nsqrt wurde mit einem negativen reellen Argument aufgerufen, gibt jedoch nur ein komplexes Ergebnis zurück, wenn es mit einem komplexen Argument aufgerufen wird. Versuchen Sie sqrt(Complex(x))."
```

Im letzten Beispiel hätte anstelle der Übereinstimmung mit einem einzelnen String alternativ auch Folgendes verwendet werden können:

  * `["Versuchen", "Complex"]` (eine Liste von Strings)
  * `r"Versuchen sqrt\([Cc]omplex"` (ein regulärer Ausdruck)
  * `str -> occursin("complex", str)` (eine Übereinstimmungsfunktion)
