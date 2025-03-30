```
Printf.Format(format_str)
```

Değerleri biçimlendirmek için kullanılabilecek C printf uyumlu bir format nesnesi oluşturur.

Girdi `format_str`, geçerli herhangi bir format belirteci karakteri ve değiştirici içerebilir.

Bir `Format` nesnesi, biçimlendirilmiş bir dize üretmek için `Printf.format(f::Format, args...)` fonksiyonuna veya biçimlendirilmiş dizeyi doğrudan `io`'ya yazdırmak için `Printf.format(io::IO, f::Format, args...)` fonksiyonuna geçirilebilir.

Kolaylık olması açısından, bir `Printf.Format` nesnesi oluşturmak için `Printf.format"..."` dize makro biçimi makro genişletme zamanında kullanılabilir.

!!! compat "Julia 1.6"
    `Printf.Format` Julia 1.6 veya daha yenisini gerektirir.

