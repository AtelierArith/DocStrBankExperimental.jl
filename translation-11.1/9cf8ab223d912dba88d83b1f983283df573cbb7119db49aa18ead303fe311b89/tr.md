```
@test_logs [log_patterns...] [keywords] ifade
```

`ifade` tarafından üretilen log kayıtlarının bir listesini `collect_test_logs` kullanarak toplayın, bunların `log_patterns` dizisine uyduğunu kontrol edin ve `ifade` değerini döndürün. `keywords` log kayıtlarının basit bir filtrelemesini sağlar: `min_level` anahtarı, test için toplanacak minimum log seviyesini kontrol eder, `match_mode` anahtarı eşleşmenin nasıl yapılacağını tanımlar (varsayılan `:all`, tüm logların ve desenlerin çiftler halinde eşleştiğini kontrol eder; `:any` kullanarak desenin dizide en az bir yerde eşleşip eşleşmediğini kontrol edebilirsiniz.)

En kullanışlı log deseni, `(level,message)` biçiminde basit bir demettir. Diğer log meta verilerini eşleştirmek için farklı sayıda demet elemanı kullanılabilir; bu, `handle_message` fonksiyonu aracılığıyla `AbstractLogger`'a geçirilen argümanlara karşılık gelir: `(level,message,module,group,id,file,line)`. Mevcut olan elemanlar, varsayılan olarak `==` kullanılarak log kaydı alanlarıyla çiftler halinde eşleştirilecektir; `Symbol`'lerin standart log seviyeleri için kullanılabileceği ve desendeki `Regex`'lerin string veya Symbol alanlarıyla `occursin` kullanarak eşleşeceği özel durumlar vardır.

# Örnekler

Bir uyarı kaydeden ve birkaç debug mesajı üreten bir fonksiyonu düşünün:

```
function foo(n)
    @info "Doing foo with n=$n"
    for i=1:n
        @debug "Iteration $i"
    end
    42
end
```

Info mesajını test edebiliriz:

```
@test_logs (:info,"Doing foo with n=2") foo(2)
```

Eğer debug mesajlarını da test etmek istiyorsak, bunların `min_level` anahtarı ile etkinleştirilmesi gerekir:

```
using Logging
@test_logs (:info,"Doing foo with n=2") (:debug,"Iteration 1") (:debug,"Iteration 2") min_level=Logging.Debug foo(2)
```

Belirli mesajların üretilip üretilmediğini test etmek istiyorsanız, `match_mode=:any` anahtarını ayarlayabilirsiniz:

```
using Logging
@test_logs (:info,) (:debug,"Iteration 42") min_level=Logging.Debug match_mode=:any foo(100)
```

Makro, döndürülen değeri de test etmek için `@test` ile zincirlenebilir:

```
@test (@test_logs (:info,"Doing foo with n=2") foo(2)) == 42
```

Uyarıların yokluğunu test etmek istiyorsanız, log desenlerini belirtmeyi atlayabilir ve `min_level`'i buna göre ayarlayabilirsiniz:

```
# logger seviyesi uyarı olduğunda ifadenin hiçbir mesaj kaydetmediğini test edin:
@test_logs min_level=Logging.Warn @info("Some information") # geçer
@test_logs min_level=Logging.Warn @warn("Some information") # başarısız
```

`@warn` tarafından üretilmeyen [`stderr`](@ref) içinde uyarıların (veya hata mesajlarının) yokluğunu test etmek istiyorsanız, [`@test_nowarn`](@ref) bakın. ```
