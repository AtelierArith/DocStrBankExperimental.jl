```
@nextract N esym isym
```

Genera `N` variables `esym_1`, `esym_2`, ..., `esym_N` para extraer valores de `isym`. `isym` puede ser un `Symbol` o una expresión de función anónima.

`@nextract 2 x y` generaría

```
x_1 = y[1]
x_2 = y[2]
```

mientras que `@nextract 3 x d->y[2d-1]` produce

```
x_1 = y[1]
x_2 = y[3]
x_3 = y[5]
```
