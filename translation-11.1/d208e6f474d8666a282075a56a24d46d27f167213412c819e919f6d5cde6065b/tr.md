```
trsyl!(transa, transb, A, B, C, isgn=1) -> (C, scale)
```

Sylvester matris denklemini `A * X +/- X * B = scale*C` çözer; burada `A` ve `B` her ikisi de neredeyse üst üçgenlidir. Eğer `transa = N` ise, `A` değiştirilmez. Eğer `transa = T` ise, `A` transpoze edilir. Eğer `transa = C` ise, `A` konjugat transpoze edilir. Benzer şekilde `transb` ve `B` için de geçerlidir. Eğer `isgn = 1` ise, denklem `A * X + X * B = scale * C` çözülür. Eğer `isgn = -1` ise, denklem `A * X - X * B = scale * C` çözülür.

`X` (C'yi üzerine yazarak) ve `scale` döner.
