```
StridedArray{T, N}
```

Sabit kodlanmış [`Union`](@ref) ortak dizi türlerinin bir birleşimidir ve [strided array interface](@ref man-interface-strided-arrays) ile uyumludur, `T` türünde elemanlar ve `N` boyutları vardır.

Eğer `A` bir `StridedArray` ise, o zaman elemanları bellekte kaydırmalarla depolanır; bu kaydırmalar boyutlar arasında değişebilir ancak bir boyut içinde sabittir. Örneğin, `A` boyut 1'de 2 kaydırmaya ve boyut 2'de 3 kaydırmaya sahip olabilir. `A`'yı boyut `d` boyunca artırmak, bellekte [`stride(A, d)`] slotları kadar atlamaya neden olur. Strided diziler özellikle önemlidir ve kullanışlıdır çünkü bazen doğrudan BLAS gibi yabancı dil kütüphanelerine işaretçi olarak geçirilebilirler.
