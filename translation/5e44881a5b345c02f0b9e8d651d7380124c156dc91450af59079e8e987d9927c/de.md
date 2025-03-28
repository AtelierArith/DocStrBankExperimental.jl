```
isdispatchtuple(T)
```

Bestimmen Sie, ob der Typ `T` ein "Blatttyp"-Tupel ist, was bedeutet, dass er als Typsignatur in der Dispatch erscheinen könnte und keine Subtypen (oder Supertypen) hat, die in einem Aufruf erscheinen könnten. Wenn `T` kein Typ ist, geben Sie `false` zurück.
