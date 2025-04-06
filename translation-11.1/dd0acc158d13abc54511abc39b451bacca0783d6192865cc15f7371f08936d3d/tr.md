```
pmap(f, [::AbstractWorkerPool], c...; distributed=true, batch_size=1, on_error=nothing, retry_delays=[], retry_check=nothing) -> collection
```

Koleksiyonu `c`'yi, mevcut işçiler ve görevler kullanarak her bir elemana `f` uygulayarak dönüştürün.

Birden fazla koleksiyon argümanı için, `f`'yi eleman bazında uygulayın.

`f`'nin tüm işçi süreçlerine erişilebilir olması gerektiğini unutmayın; detaylar için [Kod Erişilebilirliği ve Paket Yükleme](@ref code-availability) bölümüne bakın.

Bir işçi havuzu belirtilmezse, tüm mevcut işçiler [`CachingPool`](@ref) aracılığıyla kullanılacaktır.

Varsayılan olarak, `pmap` hesaplamayı belirtilen tüm işçilere dağıtır. Sadece yerel süreci kullanmak ve görevler üzerinden dağıtmak için `distributed=false` belirtin. Bu, [`asyncmap`](@ref) kullanmakla eşdeğerdir. Örneğin, `pmap(f, c; distributed=false)` ifadesi `asyncmap(f,c; ntasks=()->nworkers())` ile eşdeğerdir.

`pmap`, `batch_size` argümanı aracılığıyla süreçler ve görevlerin bir karışımını da kullanabilir. 1'den büyük grup boyutları için, koleksiyon birden fazla grup halinde işlenir; her grup `batch_size` veya daha az uzunluktadır. Bir grup, serbest bir işçiye tek bir istek olarak gönderilir; burada yerel bir [`asyncmap`](@ref), gruptan elemanları birden fazla eşzamanlı görev kullanarak işler.

Herhangi bir hata, `pmap`'ın koleksiyonun geri kalanını işlemesini durdurur. Bu davranışı geçersiz kılmak için, tek bir argüman alan bir hata işleme fonksiyonu `on_error` argümanı aracılığıyla belirtilebilir; yani, istisna. Fonksiyon, hatayı yeniden fırlatarak işlemi durdurabilir veya devam etmek için, sonuçlarla birlikte çağırana döndürülen herhangi bir değeri döndürebilir.

Aşağıdaki iki örneği göz önünde bulundurun. İlk örnek, istisna nesnesini satır içi olarak döndürür, ikincisi ise herhangi bir istisna yerine 0 döndürür:

```julia-repl
julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=identity)
4-element Array{Any,1}:
 1
  ErrorException("foo")
 3
  ErrorException("foo")

julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=ex->0)
4-element Array{Int64,1}:
 1
 0
 3
 0
```

Hatalar, başarısız hesaplamaları yeniden deneyerek de işlenebilir. Anahtar kelime argümanları `retry_delays` ve `retry_check`, [`retry`](@ref) fonksiyonuna `delays` ve `check` anahtar kelime argümanları olarak geçirilir. Gruplama belirtilirse ve bir grup tamamen başarısız olursa, gruptaki tüm öğeler yeniden denenir.

`on_error` ve `retry_delays` belirtilirse, `on_error` kancası yeniden denemeden önce çağrılır. Eğer `on_error` bir istisna fırlatmazsa (veya yeniden fırlatmazsa), eleman yeniden denenmeyecektir.

Örnek: Hatalarda, bir eleman üzerinde `f`'yi maksimum 3 kez, yeniden denemeler arasında herhangi bir gecikme olmadan yeniden deneyin.

```julia
pmap(f, c; retry_delays = zeros(3))
```

Örnek: İstisna [`InexactError`](@ref) türünde değilse `f`'yi yeniden deneyin, 3 kez kadar artan gecikmelerle. Tüm `InexactError` oluşumları için bir `NaN` döndürün.

```julia
pmap(f, c; on_error = e->(isa(e, InexactError) ? NaN : rethrow()), retry_delays = ExponentialBackOff(n = 3))
```
