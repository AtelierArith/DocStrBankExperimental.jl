```
kill(p::Process, signum=Base.SIGTERM)
```

Bir işleme sinyal gönderir. Varsayılan olarak işlemi sonlandırır. İşlem zaten çıkmışsa başarılı bir şekilde döner, ancak işlemi öldürme başarısız olursa (örneğin, yetersiz izinler gibi) bir hata fırlatır.
