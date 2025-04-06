```
Timer(callback::Function, delay; interval = 0)
```

Bir zamanlayıcı oluşturun, bu zamanlayıcı `callback` fonksiyonunu her zamanlayıcı süresi dolduğunda çalıştırır.

Bekleyen görevler uyanır ve `callback` fonksiyonu, başlangıç gecikmesi olan `delay` saniyesinden sonra çağrılır ve ardından verilen `interval` saniyesi ile tekrarlanır. Eğer `interval` sıfıra eşitse, geri çağırma yalnızca bir kez çalıştırılır. `callback` fonksiyonu, yalnızca bir argüman ile, zamanlayıcı kendisi ile çağrılır. Bir zamanlayıcıyı durdurmak için `close` çağrısı yapılır. Zamanlayıcı zaten süresi dolmuşsa, `callback` bir son kez çalıştırılabilir.

# Örnekler

Burada ilk sayı iki saniyelik bir gecikmeden sonra yazdırılır, ardından takip eden sayılar hızlı bir şekilde yazdırılır.

```julia-repl
julia> begin
           i = 0
           cb(timer) = (global i += 1; println(i))
           t = Timer(cb, 2, interval=0.2)
           wait(t)
           sleep(0.5)
           close(t)
       end
1
2
3
```
