```
modifyfield!(value, name::Symbol, op, x, [order::Symbol]) -> Pair
modifyfield!(value, i::Int, op, x, [order::Symbol]) -> Pair
```

Führen Sie atomar die Operationen aus, um ein Feld zu lesen und zu setzen, nachdem die Funktion `op` angewendet wurde.

```
y = getfield(value, name)
z = op(y, x)
setfield!(value, name, z)
return y => z
```

Wenn von der Hardware unterstützt (zum Beispiel atomare Inkrementierung), kann dies auf die entsprechende Hardwareanweisung optimiert werden, andernfalls wird eine Schleife verwendet.

!!! compat "Julia 1.7"
    Diese Funktion erfordert Julia 1.7 oder höher.

