```
with(f::Function, obj)
```

Kaynak yönetimi yardımcı fonksiyonu. `f`'yi `obj`'ye uygular, `f` başarılı bir şekilde döndüğünde veya bir hata fırlattığında `obj` üzerinde `close` çağrısı yapmayı garanti eder. Tahsis edilen git kaynaklarının, artık ihtiyaç duyulmadığında en kısa sürede sonlandırılmasını sağlar.
