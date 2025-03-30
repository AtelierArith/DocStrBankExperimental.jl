```
find_library(names [, locations])
```

`names` listesindeki ilk kütüphaneyi, `locations` listesindeki yolları, `DL_LOAD_PATH` veya sistem kütüphane yollarını (bu sırayla) kullanarak arar ve başarılı bir şekilde dlopen'lanabilir. Başarılı olursa, dönen değer, isimlerden biri (potansiyel olarak locations'daki yolların biriyle ön eklenmiş) olacaktır. Bu dize, gelecekteki `ccall`'lerde kütüphane adı olarak kullanılmak üzere bir `global const`'a atanabilir. Başarısız olursa, boş dize döner.
