```
asyncmap!(f, results, c...; ntasks=0, batch_size=nothing)
```

Wie [`asyncmap`](@ref), aber speichert die Ausgabe in `results`, anstatt eine Sammlung zurückzugeben.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein verändertes Argument Speicher mit einem anderen Argument teilt.

