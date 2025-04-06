```
dlclose(::Nothing)
```

Çok yaygın bir kullanım deseni için

```
try
    hdl = dlopen(library_name)
    ... bir şey yap
finally
    dlclose(hdl)
end
```

Kullanıcı kodunun `library_name` bulunamadığında davranışını değiştirmesi gerekmemesi için, `Nothing` türünde bir parametre kabul eden bir `dlclose()` yöntemi tanımlıyoruz.
