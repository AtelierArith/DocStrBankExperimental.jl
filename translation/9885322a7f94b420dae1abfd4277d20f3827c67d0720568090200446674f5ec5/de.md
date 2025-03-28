```
unlock(lock)
```

Gibt das Eigentum des `lock` frei.

Wenn dies ein rekursiver Lock ist, der zuvor erworben wurde, wird ein interner Zähler verringert und sofort zurückgegeben.
