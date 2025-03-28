```
do
```

Erstellen Sie eine anonyme Funktion und übergeben Sie sie als erstes Argument an einen Funktionsaufruf. Zum Beispiel:

```julia
map(1:10) do x
    2x
end
```

ist äquivalent zu `map(x->2x, 1:10)`.

Verwenden Sie mehrere Argumente wie folgt:

```julia
map(1:10, 11:20) do x, y
    x + y
end
```
