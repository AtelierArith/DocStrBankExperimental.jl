```
process_messages(r_stream::IO, w_stream::IO, incoming::Bool=true)
```

Özel taşıma yöntemleri kullanan küme yöneticileri tarafından çağrılır. Uzak bir işçiden ilk mesaj alındığında çağrılmalıdır. Özel taşıma yöntemi, uzak işçiye mantıksal bir bağlantıyı yönetmeli ve biri gelen mesajlar için diğeri uzak işçiye adreslenmiş mesajlar için olmak üzere iki `IO` nesnesi sağlamalıdır. Eğer `incoming` `true` ise, uzak eş bağlantıyı başlatmıştır. Bağlantıyı başlatan çiftin hangisi olursa olsun, küme çerezini ve Julia sürüm numarasını kimlik doğrulama el sıkışması gerçekleştirmek için gönderir.

Ayrıca bkz. [`cluster_cookie`](@ref).
