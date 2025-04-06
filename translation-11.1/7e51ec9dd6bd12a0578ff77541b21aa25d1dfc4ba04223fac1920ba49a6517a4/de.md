```
@arg_test arg1 arg2 ... body
```

Das `@arg_test` Makro wird verwendet, um `arg` Funktionen, die von `arg_readers` und `arg_writers` bereitgestellt werden, in tatsächliche Argumentwerte umzuwandeln. Wenn Sie `@arg_test arg body` schreiben, ist es äquivalent zu `arg(arg -> body)`.
