```
notify(condition, val=nothing; all=true, error=false)
```

Wecke Aufgaben, die auf eine Bedingung warten, und übergebe ihnen `val`. Wenn `all` `true` ist (der Standardwert), werden alle wartenden Aufgaben geweckt, andernfalls nur eine. Wenn `error` `true` ist, wird der übergebene Wert als Ausnahme in den geweckten Aufgaben ausgelöst.

Gib die Anzahl der geweckten Aufgaben zurück. Gib 0 zurück, wenn keine Aufgaben auf `condition` warten.
