```
ilkel tür
```

`ilkel tür` yalnızca bir dizi bitten oluşan veriye sahip somut bir türü tanımlar. İlkel türlerin klasik örnekleri tam sayılar ve kayan nokta değerleridir. İşte bazı örnek yerleşik ilkel tür tanımları:

```julia
ilkel tür Char 32 son
ilkel tür Bool <: TamSayı 8 son
```

İsmin ardından gelen sayı, türün ne kadar depolama alanı gerektirdiğini gösterir. Şu anda yalnızca 8 bitin katları olan boyutlar desteklenmektedir. [`Bool`](@ref) tanımı, bir ilkel türün isteğe bağlı olarak bazı bir süper türün alt türü olarak nasıl tanımlanabileceğini gösterir.
