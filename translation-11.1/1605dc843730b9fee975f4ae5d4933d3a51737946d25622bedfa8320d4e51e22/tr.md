```
do
```

Anonim bir fonksiyon oluşturun ve bunu bir fonksiyon çağrısının ilk argümanı olarak geçirin. Örneğin:

```julia
map(1:10) do x
    2x
end
```

şu ile eşdeğerdir: `map(x->2x, 1:10)`.

Birden fazla argüman kullanın:

```julia
map(1:10, 11:20) do x, y
    x + y
end
```
