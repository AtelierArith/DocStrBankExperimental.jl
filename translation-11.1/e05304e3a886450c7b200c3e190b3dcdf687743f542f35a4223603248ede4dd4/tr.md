```
with_warn(f::Function, ::Type{T}, args...)
```

Kaynak yönetimi yardımcı işlevi. `args`'dan `T` türünde bir örnek oluşturarak `f`'yi `args`'ya uygular. `f` başarılı bir şekilde döndüğünde veya bir hata fırlattığında, elde edilen nesne üzerinde `close` çağrısı yapıldığından emin olur. Tahsis edilen git kaynaklarının, artık ihtiyaç duyulmadıklarında mümkün olan en kısa sürede sonlandırılmasını sağlar. `f` tarafından bir hata fırlatıldığında, hatayı içeren bir uyarı gösterilir.
