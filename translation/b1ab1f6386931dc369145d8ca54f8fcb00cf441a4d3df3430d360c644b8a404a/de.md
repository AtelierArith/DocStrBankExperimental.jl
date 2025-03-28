```
try/catch
```

Eine `try`/`catch`-Anweisung ermöglicht das Abfangen von Fehlern (Ausnahmen), die von [`throw`](@ref) ausgelöst werden, sodass die Programmausführung fortgesetzt werden kann. Zum Beispiel versucht der folgende Code, eine Datei zu schreiben, warnt jedoch den Benutzer und fährt fort, anstatt die Ausführung zu beenden, wenn die Datei nicht geschrieben werden kann:

```julia
try
    open("/danger", "w") do f
        println(f, "Hello")
    end
catch
    @warn "Konnte die Datei nicht schreiben."
end
```

oder, wenn die Datei nicht in eine Variable gelesen werden kann:

```julia
lines = try
    open("/danger", "r") do f
        readlines(f)
    end
catch
    @warn "Datei nicht gefunden."
end
```

Die Syntax `catch e` (wobei `e` eine beliebige Variable ist) weist das ausgelöste Ausnahmeobjekt der angegebenen Variablen innerhalb des `catch`-Blocks zu.

Die Stärke des `try`/`catch`-Konstrukts liegt in der Fähigkeit, eine tief verschachtelte Berechnung sofort auf ein viel höheres Niveau im Stapel der aufrufenden Funktionen zurückzuführen.
