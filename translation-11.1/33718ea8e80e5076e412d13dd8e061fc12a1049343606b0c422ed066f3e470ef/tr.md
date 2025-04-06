```
Unsigned <: Integer
```

Tüm işaretsiz tam sayılar için soyut üst tür.

Yerleşik işaretsiz tam sayılar onaltılık olarak, `0x` öneki ile yazdırılır ve aynı şekilde girilebilir.

# Örnekler

```
julia> typemax(UInt8)
0xff

julia> Int(0x00d)
13

julia> unsigned(true)
0x0000000000000001
```
