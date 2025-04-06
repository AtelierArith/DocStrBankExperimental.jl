```
gels!(trans, A, B) -> (F, B, ssr)
```

Löst die lineare Gleichung `A * X = B`, `transpose(A) * X = B` oder `adjoint(A) * X = B` unter Verwendung einer QR- oder LQ-Faktorisierung. Modifiziert die Matrix/Vektor `B` vor Ort mit der Lösung. `A` wird mit seiner `QR`- oder `LQ`-Faktorisierung überschrieben. `trans` kann eines von `N` (keine Modifikation), `T` (Transponierte) oder `C` (konjugierte Transponierte) sein. `gels!` sucht nach der Lösung mit minimaler Norm/kleinsten Quadraten. `A` kann unter- oder überbestimmt sein. Die Lösung wird in `B` zurückgegeben.
