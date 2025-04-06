```
set_zero_subnormals(yes::Bool) -> Bool
```

Wenn `yes` `false` ist, folgen nachfolgende Gleitkommaoperationen den Regeln der IEEE-Arithmetik für subnormale Werte ("denormals"). Andernfalls ist es Gleitkommaoperationen erlaubt (aber nicht erforderlich), subnormale Eingaben oder Ausgaben in null zu konvertieren. Gibt `true` zurück, es sei denn, `yes==true`, aber die Hardware unterstützt das Nullsetzen von subnormalen Zahlen nicht.

`set_zero_subnormals(true)` kann einige Berechnungen auf bestimmter Hardware beschleunigen. Es kann jedoch Identitäten wie `(x-y==0) == (x==y)` brechen.

!!! warning
    Diese Funktion betrifft nur den aktuellen Thread.

