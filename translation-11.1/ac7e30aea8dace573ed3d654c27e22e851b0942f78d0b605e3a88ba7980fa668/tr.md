```
llvmcall(fun_ir::String, returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_ir::String, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
llvmcall((mod_bc::Vector{UInt8}, entry_fn::String), returntype, Tuple{argtype1, ...}, argvalue1, ...)
```

İlk argümanda sağlanan LLVM kodunu çağırın. Bu ilk argümanı belirtmenin birkaç yolu vardır:

  * argümanların ardışık isimsiz SSA değişkenleri (%0, %1, vb.) olarak mevcut olduğu, fonksiyon seviyesinde IR'yi temsil eden bir literal dize olarak;
  * çağrılacak giriş noktası fonksiyonunun adını temsil eden bir dize ve bir modül IR'si içeren 2 elemanlı bir demet olarak;
  * ancak modül, bit kodu ile `Vector{UInt8}` olarak sağlandığında 2 elemanlı bir demet olarak.

`ccall`'ın aksine, argüman türlerinin bir demet türü olarak belirtilmesi gerektiğini ve türlerin bir demetinin değil. Tüm türler ve LLVM kodu, değişkenler veya ifadeler olarak değil, literal olarak belirtilmelidir (bu literal'leri oluşturmak için `@eval` kullanmak gerekebilir).

[Opak işaretçiler](https://llvm.org/docs/OpaquePointers.html) (yazıldığı gibi `ptr`) LLVM kodunda izin verilmez.

Kullanım örnekleri için [`test/llvmcall.jl`](https://github.com/JuliaLang/julia/blob/v1.11.4/test/llvmcall.jl) dosyasına bakın.
