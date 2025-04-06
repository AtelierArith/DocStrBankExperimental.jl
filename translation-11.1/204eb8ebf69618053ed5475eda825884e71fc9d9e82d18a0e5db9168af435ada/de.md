```
return
```

`return x` bewirkt, dass die umschließende Funktion vorzeitig beendet wird und den angegebenen Wert `x` an den Aufrufer zurückgibt. `return` allein ohne Wert ist äquivalent zu `return nothing` (siehe [`nothing`](@ref)).

```julia
function compare(a, b)
    a == b && return "equal to"
    a < b ? "less than" : "greater than"
end
```

Im Allgemeinen können Sie eine `return`-Anweisung überall innerhalb eines Funktionskörpers platzieren, auch innerhalb von tief verschachtelten Schleifen oder Bedingungen, aber seien Sie vorsichtig mit `do`-Blöcken. Zum Beispiel:

```julia
function test1(xs)
    for x in xs
        iseven(x) && return 2x
    end
end

function test2(xs)
    map(xs) do x
        iseven(x) && return 2x
        x
    end
end
```

Im ersten Beispiel bricht die Rückgabe `test1` sofort ab, sobald sie eine gerade Zahl erreicht, sodass `test1([5,6,7])` `12` zurückgibt.

Sie könnten erwarten, dass das zweite Beispiel sich gleich verhält, aber in der Tat bricht das `return` dort nur aus der *inneren* Funktion (innerhalb des `do`-Blocks) aus und gibt einen Wert an `map` zurück. `test2([5,6,7])` gibt dann `[5,12,7]` zurück.

Wenn `return` in einem Ausdruck auf oberster Ebene verwendet wird (d.h. außerhalb einer Funktion), bewirkt es, dass der gesamte aktuelle Ausdruck auf oberster Ebene vorzeitig beendet wird.
