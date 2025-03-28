```
ReverseOrdering(fwd::Ordering=Forward)
```

Un wrapper qui inverse un ordre.

Pour un `Ordering` donné `o`, ce qui suit est vrai pour tous les `a`, `b` :

```
lt(ReverseOrdering(o), a, b) == lt(o, b, a)
```
