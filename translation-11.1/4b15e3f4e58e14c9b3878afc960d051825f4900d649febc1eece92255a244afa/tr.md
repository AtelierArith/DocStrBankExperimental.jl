```
@nany N expr
```

Anonim fonksiyon ifadesi `expr` tarafından üretilen ifadelerden herhangi birinin `true` değerine eşit olup olmadığını kontrol eder.

`@nany 3 d->(i_d > 1)` ifadesi `(i_1 > 1 || i_2 > 1 || i_3 > 1)` ifadesini üretecektir.
