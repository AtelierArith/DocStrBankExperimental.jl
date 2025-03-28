```
get(f::Union{Function, Type}, collection, key)
```

Gibt den Wert zurück, der für den angegebenen Schlüssel gespeichert ist, oder wenn keine Zuordnung für den Schlüssel vorhanden ist, gibt `f()` zurück. Verwenden Sie [`get!`](@ref), um auch den Standardwert im Wörterbuch zu speichern.

Dies ist dazu gedacht, mit der `do`-Block-Syntax aufgerufen zu werden

```julia
get(dict, key) do
    # Standardwert hier berechnet
    time()
end
```
