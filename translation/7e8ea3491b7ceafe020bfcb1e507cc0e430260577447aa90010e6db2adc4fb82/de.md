```
quote
```

`quote` erstellt mehrere Ausdrucksobjekte in einem Block, ohne den expliziten [`Expr`](@ref) Konstruktor zu verwenden. Zum Beispiel:

```julia
ex = quote
    x = 1
    y = 2
    x + y
end
```

Im Gegensatz zu den anderen Methoden des Quotierens, `:( ... )`, führt diese Form `QuoteNode`-Elemente in den Ausdrucksbaum ein, die berücksichtigt werden müssen, wenn der Baum direkt manipuliert wird. Für andere Zwecke werden `:( ... )` und `quote .. end` Blöcke identisch behandelt.
