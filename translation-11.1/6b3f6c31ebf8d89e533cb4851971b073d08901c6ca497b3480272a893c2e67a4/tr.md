```
mapreduce(f, op, itrs...; [init])
```

Fonksiyonu `f`'yi `itrs` içindeki her bir eleman(lar)a uygular ve ardından sonucu ikili fonksiyon `op` ile azaltır. Eğer sağlanmışsa, `init` `op` için nötr bir eleman olmalı ve boş koleksiyonlar için döndürülmelidir. `init`'in boş olmayan koleksiyonlar için kullanılıp kullanılmadığı belirsizdir. Genel olarak, boş koleksiyonlarla çalışmak için `init` sağlamak gerekecektir.

[`mapreduce`](@ref) fonksiyonel olarak `reduce(op, map(f, itr); init=init)` çağrısına eşdeğerdir, ancak genellikle daha hızlı çalışır çünkü ara bir koleksiyon oluşturulmasına gerek yoktur. [`reduce`](@ref) ve [`map`](@ref) için belgeleri inceleyin.

!!! compat "Julia 1.2"
    Birden fazla iteratör ile `mapreduce` Julia 1.2 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> mapreduce(x->x^2, +, [1:3;]) # == 1 + 4 + 9
14
```

Azaltmanın birleşim özelliği uygulamaya bağlıdır. Ayrıca, bazı uygulamalar `itr` içinde birden fazla kez görünen elemanlar için `f`'nin döndürdüğü değeri yeniden kullanabilir. Her değer için `f`'nin çağrılmasını garanti etmek ve soldan veya sağdan birleşim özelliği için [`mapfoldl`](@ref) veya [`mapfoldr`](@ref) kullanın.
