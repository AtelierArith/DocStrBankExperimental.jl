```
isdisjoint(x)
```

`x` ile [`isdisjoint`](@ref) kullanarak argümanını karşılaştıran bir fonksiyon oluşturun, yani `y -> isdisjoint(y, x)` ile eşdeğer bir fonksiyon. Döndürülen fonksiyon `Base.Fix2{typeof(isdisjoint)}` türündedir ve özel yöntemleri uygulamak için kullanılabilir.

!!! compat "Julia 1.11"
    Bu işlevsellik en az Julia 1.11 gerektirir.

