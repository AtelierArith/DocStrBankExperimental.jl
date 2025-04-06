```
@ccall library.function_name(argvalue1::argtype1, ...)::returntype
@ccall function_name(argvalue1::argtype1, ...)::returntype
@ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

C tarafından dışa aktarılan bir paylaşımlı kütüphanede, `library.function_name` ile belirtilen bir fonksiyonu çağırın; burada `library` bir dize sabiti veya literaldir. Kütüphane atlanabilir; bu durumda `function_name` mevcut süreçte çözülür. Alternatif olarak, `@ccall`, `dlsym` tarafından döndürülen bir fonksiyon işaretçisi `$function_pointer` çağırmak için de kullanılabilir.

Her `argvalue`, `@ccall` için otomatik olarak `unsafe_convert(argtype, cconvert(argtype, argvalue))` çağrıları eklenerek karşılık gelen `argtype`'e dönüştürülür. (Daha fazla ayrıntı için [`unsafe_convert`](@ref Base.unsafe_convert) ve [`cconvert`](@ref Base.cconvert) belgelerine de bakın.) Çoğu durumda, bu basitçe `convert(argtype, argvalue)` çağrısına yol açar.

# Örnekler

```
@ccall strlen(s::Cstring)::Csize_t
```

Bu, C standart kütüphane fonksiyonunu çağırır:

```
size_t strlen(char *)
```

`S` adında bir Julia değişkeni ile. Ayrıca `ccall`'a da bakın.

Varargs, aşağıdaki kural ile desteklenir:

```
@ccall printf("%s = %d"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
```

Noktalı virgül, en az bir tane olması gereken zorunlu argümanları değişken argümanlardan ayırmak için kullanılır.

Bir dış kütüphane kullanarak örnek:

```
# g_uri_escape_string'in C imzası:
# char *g_uri_escape_string(const char *unescaped, const char *reserved_chars_allowed, gboolean allow_utf8);

const glib = "libglib-2.0"
@ccall glib.g_uri_escape_string(my_uri::Cstring, ":/"::Cstring, true::Cint)::Cstring
```

Dize literali, istenirse fonksiyon adından önce doğrudan da kullanılabilir `"libglib-2.0".g_uri_escape_string(...`
