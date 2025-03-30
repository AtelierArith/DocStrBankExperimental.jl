```
approve(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

Gelecek bir kimlik doğrulama işleminde yeniden kullanılmak üzere `payload` kimlik bilgilerini saklayın. Sadece kimlik doğrulama başarılı olduğunda çağrılmalıdır.

`shred` anahtarı, yük kimlik bilgisi alanındaki hassas bilgilerin yok edilip edilmeyeceğini kontrol eder. Sadece test sırasında `false` olarak ayarlanmalıdır.
