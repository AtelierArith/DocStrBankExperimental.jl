```
arg_isdir(f::Function, arg::AbstractString) -> f(arg)
```

Die Funktion `arg_isdir` nimmt `arg`, das der Pfad zu einem vorhandenen Verzeichnis sein muss (ansonsten wird ein Fehler ausgelöst), und übergibt diesen Pfad an `f`, wobei schließlich das Ergebnis von `f(arg)` zurückgegeben wird. Dies ist definitiv das am wenigsten nützliche Werkzeug, das von `ArgTools` angeboten wird, und existiert hauptsächlich aus Symmetrie mit `arg_mkdir` und um konsistente Fehlermeldungen zu geben.
