```
@nall N expr
```

Anonim fonksiyon ifadesi `expr` tarafından üretilen tüm ifadelerin `true` değerine sahip olup olmadığını kontrol edin.

`@nall 3 d->(i_d > 1)` ifadesi `(i_1 > 1 && i_2 > 1 && i_3 > 1)` ifadesini üretecektir. Bu, sınır kontrolü için kullanışlı olabilir.
