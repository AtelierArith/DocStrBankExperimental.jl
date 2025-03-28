```
ReverseOrdering(fwd::Ordering=Forward)
```

Ein Wrapper, der eine Reihenfolge umkehrt.

Für eine gegebene `Ordering` `o` gilt Folgendes für alle `a`, `b`:

```
lt(ReverseOrdering(o), a, b) == lt(o, b, a)
```
