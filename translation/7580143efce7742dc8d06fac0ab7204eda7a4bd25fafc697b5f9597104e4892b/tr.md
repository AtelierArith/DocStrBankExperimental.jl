```
const
```

`const`, değiştirilemeyecek değerleri olan global değişkenleri tanımlamak için kullanılır. Neredeyse tüm kodlarda (özellikle performansa duyarlı kodlarda) global değişkenler bu şekilde sabit olarak tanımlanmalıdır.

```julia
const x = 5
```

Birden fazla değişken tek bir `const` içinde tanımlanabilir:

```julia
const y, z = 7, 11
```

`const` yalnızca bir `=` işlemi için geçerlidir; bu nedenle `const x = y = 1` ifadesi `x`'i sabit olarak tanımlar ama `y`'yi tanımlamaz. Öte yandan, `const x = const y = 1` ifadesi hem `x` hem de `y`'yi sabit olarak tanımlar.

"Sabirlik" durumu, değiştirilebilir konteynerlere uzanmaz; yalnızca bir değişken ile değeri arasındaki ilişki sabittir. Eğer `x` bir dizi veya sözlükse (örneğin) elemanları hala değiştirebilir, ekleyebilir veya kaldırabilirsiniz.

Bazı durumlarda bir `const` değişkeninin değerini değiştirmek bir hata yerine uyarı verir. Ancak bu, öngörülemeyen davranışlara veya programınızın durumunu bozmasına neden olabilir ve bu nedenle kaçınılmalıdır. Bu özellik yalnızca etkileşimli kullanım sırasında kolaylık sağlamak amacıyla tasarlanmıştır.
