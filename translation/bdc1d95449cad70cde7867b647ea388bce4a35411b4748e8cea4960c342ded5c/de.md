```
open(command, mode::AbstractString, stdio=devnull)
```

Führen Sie `command` asynchron aus. Ähnlich wie `open(command, stdio; read, write)`, jedoch werden die Lese- und Schreibflags über eine Moduszeichenfolge anstelle von Schlüsselwortargumenten angegeben. Mögliche Moduszeichenfolgen sind:

| Modus | Beschreibung     | Schlüsselwörter             |
|:----- |:---------------- |:--------------------------- |
| `r`   | lesen            | keine                       |
| `w`   | schreiben        | `write = true`              |
| `r+`  | lesen, schreiben | `read = true, write = true` |
| `w+`  | lesen, schreiben | `read = true, write = true` |
