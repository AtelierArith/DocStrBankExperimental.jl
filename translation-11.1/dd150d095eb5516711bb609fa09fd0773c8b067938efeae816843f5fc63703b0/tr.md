```
Threads.@spawn [:default|:interactive] expr
```

Bir [`Task`](@ref) oluşturur ve belirtilen thread havuzunda (`belirtilmezse :default`) çalışması için [`schedule`](@ref) eder. Görev, bir thread mevcut olduğunda ona tahsis edilir. Görevin bitmesini beklemek için, bu makronun sonucunda [`wait`](@ref) çağrısı yapabilir veya [`fetch`](@ref) çağrısı yaparak bekleyip dönen değerini alabilirsiniz.

Değerler, `$` aracılığıyla `@spawn` içine interpolasyon yapılabilir; bu, değeri doğrudan oluşturulan alt kapanıma kopyalar. Bu, bir değişkenin *değerini* eklemenizi sağlar ve asenkron kodu mevcut görevdeki değişkenin değerindeki değişikliklerden izole eder.

!!! not
    Görevin çalıştığı thread, görev yield ettiğinde değişebilir; bu nedenle `threadid()` bir görev için sabit olarak değerlendirilmemelidir. Daha fazla önemli uyarılar için [`Task Migration`](@ref man-task-migration) ve daha geniş [çoklu iş parçacığı](@ref man-multithreading) kılavuzuna bakın. Ayrıca [thread havuzları](@ref man-threadpools) bölümüne de bakın.


!!! uyumluluk "Julia 1.3"
    Bu makro, Julia 1.3 itibarıyla mevcuttur.


!!! uyumluluk "Julia 1.4"
    `$` aracılığıyla değerlerin interpolasyonu, Julia 1.4 itibarıyla mevcuttur.


!!! uyumluluk "Julia 1.9"
    Bir thread havuzu, Julia 1.9 itibarıyla belirtilebilir.


# Örnekler

```julia-repl
julia> t() = println("Hello from ", Threads.threadid());

julia> tasks = fetch.([Threads.@spawn t() for i in 1:4]);
Hello from 1
Hello from 1
Hello from 3
Hello from 4
```
