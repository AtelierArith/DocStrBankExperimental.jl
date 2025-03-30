```
@ncall N f sym...
```

Fonksiyon çağrısı ifadesi oluşturun. `sym`, herhangi bir sayıda fonksiyon argümanını temsil eder; bunların sonuncusu bir anonim fonksiyon ifadesi olabilir ve `N` argümanına genişletilir.

Örneğin, `@ncall 3 func a` şu sonucu üretir:

```
func(a_1, a_2, a_3)
```

`@ncall 2 func a b i->c[i]` ise şu sonucu verir:

```
func(a, b, c[1], c[2])
```
