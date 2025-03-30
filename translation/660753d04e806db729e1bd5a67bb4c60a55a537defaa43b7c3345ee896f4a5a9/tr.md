```
issetequal(x)
```

`x` argümanını [`issetequal`](@ref) kullanarak karşılaştıran bir fonksiyon oluşturun, yani `y -> issetequal(y, x)` fonksiyonuna eşdeğer bir fonksiyon. Döndürülen fonksiyon `Base.Fix2{typeof(issetequal)}` türündedir ve özel yöntemleri uygulamak için kullanılabilir.

!!! compat "Julia 1.11"
    Bu işlevsellik en az Julia 1.11 gerektirir.

