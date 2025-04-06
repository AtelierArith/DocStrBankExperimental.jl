```
iterate(iter [, state]) -> Union{Nothing, Tuple{Any, Any}}
```

Bewege den Iterator vorwärts, um das nächste Element zu erhalten. Wenn keine Elemente mehr vorhanden sind, sollte `nothing` zurückgegeben werden. Andernfalls sollte ein 2-Tupel des nächsten Elements und des neuen Iterationsstatus zurückgegeben werden.
