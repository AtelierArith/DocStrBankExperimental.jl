```
invokelatest(f, args...; kwargs...)
```

`f(args...; kwargs...)` çağrısını yapar, ancak `f`'nin en son yönteminin çalıştırılmasını garanti eder. Bu, uzun süreli olay döngüleri veya eski sürümlerini çağırabilecek geri çağırma işlevleri gibi özel durumlarda yararlıdır. (Dezavantajı, `invokelatest`'in `f`'yi doğrudan çağırmaktan biraz daha yavaş olması ve sonucun türünün derleyici tarafından çıkarılamamasıdır.)

!!! compat "Julia 1.9"
    Julia 1.9'dan önce, bu işlev dışa aktarılmamıştı ve `Base.invokelatest` olarak adlandırılıyordu.

