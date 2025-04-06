```
apropos([io::IO=stdout], pattern::Union{AbstractString,Regex})
```

Durchsuchen Sie die verfügbaren Dokumentationszeichenfolgen nach Einträgen, die `pattern` enthalten.

Wenn `pattern` eine Zeichenfolge ist, wird die Groß- und Kleinschreibung ignoriert. Die Ergebnisse werden an `io` ausgegeben.

`apropos` kann im Hilfemodus im REPL aufgerufen werden, indem die Abfrage in doppelte Anführungszeichen gesetzt wird:

```
help?> "pattern"
```
