```
LAPACKException
```

Genel LAPACK istisnası, ya doğrudan [LAPACK fonksiyonları](@ref man-linalg-lapack-functions) çağrılırken ya da LAPACK fonksiyonlarını dahili olarak kullanan ancak özel hata işleme eksik olan diğer fonksiyonlara yapılan çağrılarda fırlatılır. `info` alanı, çağrılan LAPACK fonksiyonuna bağlı olarak temel hata hakkında ek bilgi içerir.
