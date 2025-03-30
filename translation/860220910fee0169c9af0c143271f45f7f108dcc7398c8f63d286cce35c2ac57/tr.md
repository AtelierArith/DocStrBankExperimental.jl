```
expm1(x)
```

Doğru bir şekilde $e^x-1$ hesaplar. Küçük x değerleri için exp(x)-1'in doğrudan değerlendirilmesinde meydana gelen hassasiyet kaybını önler.

# Örnekler

```jldoctest
julia> expm1(1e-16)
1.0e-16

julia> exp(1e-16) - 1
0.0
```
