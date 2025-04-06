```
set_num_threads(n::Integer)
set_num_threads(::Nothing)
```

BLAS kütüphanesinin kullanacağı iş parçacığı sayısını `n::Integer` olarak ayarlayın.

Ayrıca `nothing` kabul eder, bu durumda julia varsayılan iş parçacığı sayısını tahmin etmeye çalışır. `nothing` geçmek önerilmez ve esasen tarihsel nedenlerle mevcuttur.
