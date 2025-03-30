```
UInt
```

Sys.WORD_SIZE bit işaretsiz tam sayı türü, `UInt <: Unsigned <: Integer`.

[`Int`](@ref Int) gibi, `UInt` takma adı, belirli bir bilgisayardaki `Sys.WORD_SIZE` değerine göre ya `UInt32` ya da `UInt64`'e işaret edebilir.

Onaltılık olarak yazdırılır ve ayrıştırılır: `UInt(15) === 0x000000000000000f`.
