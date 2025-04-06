```
reduce(op, itr; [init])
```

Verilen koleksiyonu `itr` verilen ikili operatör `op` ile azaltın. Eğer sağlanmışsa, başlangıç değeri `init` `op` için nötr bir eleman olmalı ve boş koleksiyonlar için döndürülmelidir. `init`'in boş olmayan koleksiyonlar için kullanılıp kullanılmayacağı belirsizdir.

Boş koleksiyonlar için, `init` sağlamak gerekli olacaktır, bazı özel durumlar dışında (örneğin, `op` `+`, `*`, `max`, `min`, `&`, `|`'den biri olduğunda) Julia `op`'nin nötr elemanını belirleyebilir.

Belirli yaygın kullanılan operatörler için azaltmaların özel uygulamaları olabilir ve bunun yerine kullanılmalıdır: [`maximum`](@ref)`(itr)`, [`minimum`](@ref)`(itr)`, [`sum`](@ref)`(itr)`, [`prod`](@ref)`(itr)`, [`any`](@ref)`(itr)`, [`all`](@ref)`(itr)`. Belirli dizi dizilerini birleştirmek için `reduce(`[`vcat`](@ref)`, arr)` veya `reduce(`[`hcat`](@ref)`, arr)` çağrısını yaparak verimli yöntemler vardır.

Azaltmanın birleşim özelliği uygulamaya bağlıdır. Bu, `-` gibi birleşim özelliği taşımayan işlemleri kullanamayacağınız anlamına gelir çünkü `reduce(-,[1,2,3])`'ün `(1-2)-3` veya `1-(2-3)` olarak değerlendirilip değerlendirilmeyeceği belirsizdir. Garantili soldan veya sağdan birleşim özelliği için [`foldl`](@ref) veya [`foldr`](@ref) kullanın.

Bazı işlemler hata biriktirir. Paralellik, azaltmanın gruplar halinde yürütülmesi daha kolay olursa daha kolay olacaktır. Julia'nın gelecekteki sürümleri algoritmayı değiştirebilir. Sıralı bir koleksiyon kullanıyorsanız, elemanlar yeniden sıralanmaz.

# Örnekler

```jldoctest
julia> reduce(*, [2; 3; 4])
24

julia> reduce(*, [2; 3; 4]; init=-1)
-24
```
