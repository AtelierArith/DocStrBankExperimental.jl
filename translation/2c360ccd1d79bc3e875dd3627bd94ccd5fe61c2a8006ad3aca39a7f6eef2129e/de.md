```
gges!(jobvsl, jobvsr, A, B) -> (A, B, alpha, beta, vsl, vsr)
```

Berechnet die verallgemeinerten Eigenwerte, die verallgemeinerte Schur-Form, linke Schur-Vektoren (`jobsvl = V`) oder rechte Schur-Vektoren (`jobvsr = V`) von `A` und `B`.

Die verallgemeinerten Eigenwerte werden in `alpha` und `beta` zurückgegeben. Die linken Schur-Vektoren werden in `vsl` und die rechten Schur-Vektoren werden in `vsr` zurückgegeben.
