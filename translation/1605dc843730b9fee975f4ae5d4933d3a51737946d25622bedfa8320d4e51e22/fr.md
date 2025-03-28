```
do
```

Créez une fonction anonyme et passez-la comme premier argument à un appel de fonction. Par exemple :

```julia
map(1:10) do x
    2x
end
```

est équivalent à `map(x->2x, 1:10)`.

Utilisez plusieurs arguments comme ceci :

```julia
map(1:10, 11:20) do x, y
    x + y
end
```
