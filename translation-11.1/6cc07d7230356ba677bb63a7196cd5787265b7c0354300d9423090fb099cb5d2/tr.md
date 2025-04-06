```
unsafe_convert(T, x)
```

`x`'i `T` türünde bir C argümanına dönüştürün; burada giriş `x`, `cconvert(T, ...)`'in döndürdüğü değer olmalıdır.

[`convert`](@ref) bir Julia nesnesini `Ptr`'ye dönüştürmesi gerektiğinde, bu işlev o dönüşümü tanımlamak ve gerçekleştirmek için kullanılmalıdır.

Bu işlevin sonucunun kullanılacağı süre boyunca `x`'e bir Julia referansının var olduğundan emin olun. Bu nedenle, bu işlevin argümanı `x` asla bir ifade olmamalıdır, yalnızca bir değişken adı veya alan referansı olmalıdır. Örneğin, `x=a.b.c` kabul edilebilir, ancak `x=[a,b,c]` kabul edilemez.

Bu işlevdeki `unsafe` ön eki, bu işlevin `x` argümanının program için artık erişilebilir olmadığı bir durumda bu işlevin sonucunu kullanmanın tanımsız davranışa, program bozulmasına veya segfault'lara neden olabileceğini belirtir.

Ayrıca [`cconvert`](@ref) bakınız.
