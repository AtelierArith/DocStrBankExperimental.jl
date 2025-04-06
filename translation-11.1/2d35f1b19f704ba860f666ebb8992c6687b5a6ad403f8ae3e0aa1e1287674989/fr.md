```
@nextract N esym isym
```

Générer `N` variables `esym_1`, `esym_2`, ..., `esym_N` pour extraire des valeurs de `isym`. `isym` peut être soit un `Symbol`, soit une expression de fonction anonyme.

`@nextract 2 x y` générerait

```
x_1 = y[1]
x_2 = y[2]
```

tandis que `@nextract 3 x d->y[2d-1]` donnerait

```
x_1 = y[1]
x_2 = y[3]
x_3 = y[5]
```
