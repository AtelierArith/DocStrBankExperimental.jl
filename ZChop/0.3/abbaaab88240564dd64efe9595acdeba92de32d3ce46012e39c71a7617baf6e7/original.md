```
zchop(x, eps::Real = ZEPS)
```

Replace `x` by zero if `abs(x) < eps`.

`zchop` acts recursively on mappable objects. `zchop` acts independently on each part of a complex number. Objects whose components cannot be sensibly compared to a real number are passed unaltered.

See also `zchop!`, `nchop`, and `nchop!`.
