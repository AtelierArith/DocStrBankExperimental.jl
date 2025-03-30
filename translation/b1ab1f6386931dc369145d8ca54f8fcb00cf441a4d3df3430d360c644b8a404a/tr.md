```
try/catch
```

Bir `try`/`catch` ifadesi, [`throw`](@ref) tarafından fırlatılan hataları (istisnaları) yakalamaya olanak tanır, böylece program yürütmesi devam edebilir. Örneğin, aşağıdaki kod bir dosya yazmayı dener, ancak dosya yazılamıyorsa kullanıcıyı uyarır ve yürütmeyi sonlandırmak yerine devam eder:

```julia
try
    open("/danger", "w") do f
        println(f, "Hello")
    end
catch
    @warn "Dosya yazılamadı."
end
```

veya, dosya bir değişkene okunamadığında:

```julia
lines = try
    open("/danger", "r") do f
        readlines(f)
    end
catch
    @warn "Dosya bulunamadı."
end
```

`catch e` sözdizimi (burada `e` herhangi bir değişken) fırlatılan istisna nesnesini `catch` bloğu içindeki verilen değişkene atar.

`try`/`catch` yapısının gücü, derin bir şekilde iç içe geçmiş bir hesaplamayı hemen çağıran fonksiyonlar yığınında çok daha yüksek bir seviyeye geri sarabilme yeteneğindedir.
