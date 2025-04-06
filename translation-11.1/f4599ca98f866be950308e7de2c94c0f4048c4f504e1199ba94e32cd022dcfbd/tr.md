```
asyncmap(f, c...; ntasks=0, batch_size=nothing)
```

Bir koleksiyon (veya birden fazla eşit uzunlukta koleksiyon) üzerinde `f`'yi eşzamanlı görevler kullanarak haritalar. Birden fazla koleksiyon argümanı için, `f` eleman bazında uygulanır.

`ntasks`, eşzamanlı olarak çalıştırılacak görev sayısını belirtir. Koleksiyonların uzunluğuna bağlı olarak, `ntasks` belirtilmemişse, eşzamanlı haritalama için en fazla 100 görev kullanılacaktır.

`ntasks`, ayrıca sıfır argümanlı bir fonksiyon olarak da belirtilebilir. Bu durumda, her bir elemanı işlemden önce paralel olarak çalıştırılacak görev sayısı kontrol edilir ve `ntasks_func` değeri mevcut görev sayısından büyükse yeni bir görev başlatılır.

`batch_size` belirtilirse, koleksiyon toplu modda işlenir. Bu durumda, `f`, bir `Vector` argüman demetleri kabul eden ve bir sonuç vektörü döndüren bir fonksiyon olmalıdır. Girdi vektörünün uzunluğu `batch_size` veya daha az olacaktır.

Aşağıdaki örnekler, haritalama fonksiyonunun çalıştırıldığı görevlerin `objectid`'sini döndürerek farklı görevlerdeki yürütmeyi vurgular.

Öncelikle, `ntasks` tanımlanmamışken, her bir eleman farklı bir görevde işlenir.

```
julia> tskoid() = objectid(current_task());

julia> asyncmap(x->tskoid(), 1:5)
5-element Array{UInt64,1}:
 0x6e15e66c75c75853
 0x440f8819a1baa682
 0x9fb3eeadd0c83985
 0xebd3e35fe90d4050
 0x29efc93edce2b961

julia> length(unique(asyncmap(x->tskoid(), 1:5)))
5
```

`ntasks=2` ile tüm elemanlar 2 görevde işlenir.

```
julia> asyncmap(x->tskoid(), 1:5; ntasks=2)
5-element Array{UInt64,1}:
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94

julia> length(unique(asyncmap(x->tskoid(), 1:5; ntasks=2)))
2
```

`batch_size` tanımlandığında, haritalama fonksiyonu bir argüman demetleri dizisini kabul edecek ve bir sonuç dizisi döndürecek şekilde değiştirilmelidir. Bunu başarmak için değiştirilmiş haritalama fonksiyonunda `map` kullanılır.

```
julia> batch_func(input) = map(x->string("args_tuple: ", x, ", element_val: ", x[1], ", task: ", tskoid()), input)
batch_func (generic function with 1 method)

julia> asyncmap(batch_func, 1:5; ntasks=2, batch_size=2)
5-element Array{String,1}:
 "args_tuple: (1,), element_val: 1, task: 9118321258196414413"
 "args_tuple: (2,), element_val: 2, task: 4904288162898683522"
 "args_tuple: (3,), element_val: 3, task: 9118321258196414413"
 "args_tuple: (4,), element_val: 4, task: 4904288162898683522"
 "args_tuple: (5,), element_val: 5, task: 9118321258196414413"
```
