```
<=(x)
```

`x` ile argümanını [`<=`](@ref) kullanarak karşılaştıran bir fonksiyon oluşturun, yani `y -> y <= x` ile eşdeğer bir fonksiyon. Döndürülen fonksiyon `Base.Fix2{typeof(<=)}` türündedir ve özel yöntemleri uygulamak için kullanılabilir.

!!! compat "Julia 1.2"
    Bu işlevsellik en az Julia 1.2 gerektirir.

