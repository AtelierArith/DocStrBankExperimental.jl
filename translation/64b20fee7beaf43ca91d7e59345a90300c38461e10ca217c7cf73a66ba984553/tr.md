```
reject(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

Gelecek kimlik doğrulamalarında yeniden kullanılmak üzere `payload` kimlik bilgisi reddedilir. Sadece kimlik doğrulama başarısız olduğunda çağrılmalıdır.

`shred` anahtarı, yük kimlik bilgisi alanındaki hassas bilgilerin yok edilip edilmeyeceğini kontrol eder. Sadece test sırasında `false` olarak ayarlanmalıdır.
