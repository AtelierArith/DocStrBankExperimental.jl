```
Sembol
```

Parselanmış julia kodundaki (AST'ler) tanımlayıcıları temsil etmek için kullanılan nesne türü. Ayrıca genellikle bir varlığı tanımlamak için bir ad veya etiket olarak kullanılır (örneğin, bir sözlük anahtarı olarak). `Symbol`lar `:` alıntı operatörü kullanılarak girilebilir:

```jldoctest
julia> :name
:name

julia> typeof(:name)
Symbol

julia> x = 42
42

julia> eval(:x)
42
```

`Symbol`lar ayrıca `Symbol(x...)` yapıcıyı çağırarak dizelerden veya diğer değerlerden oluşturulabilir.

`Symbol`lar değişmezdir ve uygulamaları, aynı ada sahip tüm `Symbol`lar için aynı nesneyi yeniden kullanır.

Dizelerin aksine, `Symbol`lar "atomik" veya "skalar" varlıklar olup karakterler üzerinde yineleme desteklemez.
