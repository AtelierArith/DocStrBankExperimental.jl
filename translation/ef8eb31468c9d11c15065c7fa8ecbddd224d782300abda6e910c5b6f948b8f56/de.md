```
parse_pidfile(file::Union{IO, String}) => (pid, hostname, age)
```

Versuchen Sie, unser pidfile-Format zu parsen, wobei ein Element durch (0, "", 0.0) ersetzt wird, wenn ein Lesevorgang fehlschlägt.
