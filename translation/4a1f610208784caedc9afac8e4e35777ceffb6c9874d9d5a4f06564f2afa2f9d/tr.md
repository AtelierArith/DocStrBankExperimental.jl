```
current_exceptions(task::Task=current_task(); [backtrace::Bool=true])
```

Şu anda işlenen istisnaların yığınını alın. İç içe yakalama blokları için yığında birden fazla mevcut istisna olabilir; bu durumda en son fırlatılan istisna yığının en sonunda yer alır. Yığın, `(exception,backtrace)` adlı demetlerin AbstractVector'ı olan bir `ExceptionStack` olarak döndürülür. Eğer `backtrace` false ise, her çiftteki geri izleme `nothing` olarak ayarlanacaktır.

Açıkça `task` geçmek, rastgele bir görevdeki mevcut istisna yığınını döndürecektir. Bu, yakalanmamış istisnalar nedeniyle başarısız olan görevleri incelemek için yararlıdır.

!!! compat "Julia 1.7"
    Bu işlev, Julia 1.1–1.6'da deneysel adı `catch_stack()` olarak biliniyordu ve bir döndürme türü olarak düz bir Tuple'lar Vektörü vardı.

