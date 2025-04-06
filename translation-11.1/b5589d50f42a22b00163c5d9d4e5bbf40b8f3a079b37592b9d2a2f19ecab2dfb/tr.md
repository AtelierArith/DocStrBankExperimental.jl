```
dlsym(handle, sym; throw_error::Bool = true)
```

Paylaşılan bir kütüphane tutamacından bir sembol arayın, başarılı olursa çağrılabilir işlev işaretçisi döndürün.

Sembol bulunamazsa, bu yöntem bir hata fırlatır, `throw_error` anahtar kelime argümanı `false` olarak ayarlanmadığı sürece; bu durumda bu yöntem `nothing` döndürür.
