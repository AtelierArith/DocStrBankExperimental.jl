```
free(addr::Ptr)
```

C standart kütüphanesinden `free` çağrısı yapar. Bunu yalnızca [`malloc`](@ref) ile elde edilen bellek üzerinde kullanın, diğer C kütüphanelerinden alınan işaretçiler üzerinde değil. C kütüphanelerinden elde edilen [`Ptr`](@ref) nesneleri, sistemde birden fazla `libc` kütüphanesi varsa, doğrulama hatalarını önlemek için o kütüphanede tanımlanan serbest bırakma fonksiyonlarıyla serbest bırakılmalıdır.
