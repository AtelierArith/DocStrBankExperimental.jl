```
@nextract N esym isym
```

`isym`'den değerleri çıkarmak için `esym_1`, `esym_2`, ..., `esym_N` değişkenlerini oluşturur. `isym` ya bir `Symbol` ya da anonim fonksiyon ifadesi olabilir.

`@nextract 2 x y` şu sonucu üretir:

```
x_1 = y[1]
x_2 = y[2]
```

`@nextract 3 x d->y[2d-1]` ise şu sonucu verir:

```
x_1 = y[1]
x_2 = y[3]
x_3 = y[5]
```
