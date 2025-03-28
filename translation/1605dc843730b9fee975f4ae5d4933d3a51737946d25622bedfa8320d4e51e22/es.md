```
do
```

Crea una función anónima y pásala como el primer argumento a una llamada de función. Por ejemplo:

```julia
map(1:10) do x
    2x
end
```

es equivalente a `map(x->2x, 1:10)`.

Usa múltiples argumentos de la siguiente manera:

```julia
map(1:10, 11:20) do x, y
    x + y
end
```
