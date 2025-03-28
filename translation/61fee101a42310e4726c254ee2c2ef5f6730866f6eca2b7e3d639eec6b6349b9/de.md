```
swapfield!(value, name::Symbol, x, [order::Symbol])
swapfield!(value, i::Int, x, [order::Symbol])
```

Führen Sie die Operationen atomar aus, um gleichzeitig ein Feld zu erhalten und zu setzen:

```
y = getfield(value, name)
setfield!(value, name, x)
return y
```

!!! compat "Julia 1.7"
    Diese Funktion erfordert Julia 1.7 oder höher.

