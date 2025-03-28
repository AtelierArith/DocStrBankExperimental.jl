```
ReverseOrdering(fwd::Ordering=Forward)
```

Un envoltorio que invierte un orden.

Para un `Ordering` dado `o`, se cumple lo siguiente para todos `a`, `b`:

```
lt(ReverseOrdering(o), a, b) == lt(o, b, a)
```
