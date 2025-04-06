```
gees!(jobvs, A) -> (A, vs, w)
```

Berechnet die Eigenwerte (`jobvs = N`) oder die Eigenwerte und Schur-Vektoren (`jobvs = V`) der Matrix `A`. `A` wird durch ihre Schur-Form überschrieben.

Gibt `A`, `vs`, das die Schur-Vektoren enthält, und `w`, das die Eigenwerte enthält, zurück.
