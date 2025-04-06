```
isequal(x)
```

Bir argümanı `x` ile [`isequal`](@ref) kullanarak karşılaştıran bir fonksiyon oluşturun, yani `y -> isequal(y, x)` ile eşdeğer bir fonksiyon.

Dönen fonksiyon `Base.Fix2{typeof(isequal)}` türündedir ve özel yöntemler uygulamak için kullanılabilir.
