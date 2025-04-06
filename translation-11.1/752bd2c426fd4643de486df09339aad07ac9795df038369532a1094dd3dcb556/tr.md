```
enumerate(iter)
```

Bir iterator, `(i, x)` çiftlerini döndürür; burada `i` 1'den başlayan bir sayıcıdır ve `x` verilen iterator'dan `i`'nci değerdir. Üzerinde döngü yaptığınız değerler `x`'in yanı sıra, şu ana kadar kaç kez döngü yapıldığını bilmeniz gerektiğinde kullanışlıdır.

Dikkat edin ki `i`, `iter` için geçerli bir indeks olmayabilir veya farklı bir öğeyi indeksleyebilir. Bu, `iter`'in indekslerinin 1'den başlamadığı durumlarda meydana gelebilir ve dizeler, sözlükler vb. için de olabilir. `i`'nin bir indeks olmasını istiyorsanız `pairs(IndexLinear(), iter)` yöntemine bakın.

# Örnekler

```jldoctest
julia> a = ["a", "b", "c"];

julia> for (index, value) in enumerate(a)
           println("$index $value")
       end
1 a
2 b
3 c

julia> str = "naïve";

julia> for (i, val) in enumerate(str)
           print("i = ", i, ", val = ", val, ", ")
           try @show(str[i]) catch e println(e) end
       end
i = 1, val = n, str[i] = 'n'
i = 2, val = a, str[i] = 'a'
i = 3, val = ï, str[i] = 'ï'
i = 4, val = v, StringIndexError("naïve", 4)
i = 5, val = e, str[i] = 'v'
```
