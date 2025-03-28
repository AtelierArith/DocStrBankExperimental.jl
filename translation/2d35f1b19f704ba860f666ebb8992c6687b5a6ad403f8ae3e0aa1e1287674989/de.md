```
@nextract N esym isym
```

Generiere `N` Variablen `esym_1`, `esym_2`, ..., `esym_N`, um Werte aus `isym` zu extrahieren. `isym` kann entweder ein `Symbol` oder ein anonyme Funktionsausdruck sein.

`@nextract 2 x y` würde generieren

```
x_1 = y[1]
x_2 = y[2]
```

während `@nextract 3 x d->y[2d-1]` ergibt

```
x_1 = y[1]
x_2 = y[3]
x_3 = y[5]
```
