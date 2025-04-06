```
function
```

Fonksiyonlar `function` anahtar kelimesi ile tanımlanır:

```julia
function add(a, b)
    return a + b
end
```

Ya da kısa form notasyonu:

```julia
add(a, b) = a + b
```

[`return`](@ref) anahtar kelimesinin kullanımı diğer dillerdeki ile tam olarak aynıdır, ancak genellikle isteğe bağlıdır. Açık bir `return` ifadesi olmayan bir fonksiyon, fonksiyon gövdesindeki son ifadeyi döndürecektir.
