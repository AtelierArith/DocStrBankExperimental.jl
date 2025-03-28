```
Printf.Format(format_str)
```

Erstellen Sie ein C printf-kompatibles Formatobjekt, das zur Formatierung von Werten verwendet werden kann.

Der Eingabewert `format_str` kann beliebige gültige Formatbezeichnerzeichen und Modifikatoren enthalten.

Ein `Format`-Objekt kann an `Printf.format(f::Format, args...)` übergeben werden, um einen formatierten String zu erzeugen, oder an `Printf.format(io::IO, f::Format, args...)`, um den formatierten String direkt an `io` auszugeben.

Zur Vereinfachung kann die `Printf.format"..."`-String-Makroform verwendet werden, um ein `Printf.Format`-Objekt zur Makro-Expansionszeit zu erstellen.

!!! compat "Julia 1.6"
    `Printf.Format` erfordert Julia 1.6 oder höher.

