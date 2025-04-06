```
redisplay(x)
redisplay(d::AbstractDisplay, x)
redisplay(mime, x)
redisplay(d::AbstractDisplay, mime, x)
```

Standardmäßig rufen die `redisplay`-Funktionen einfach [`display`](@ref) auf. Einige Anzeige-Backends können jedoch `redisplay` überschreiben, um eine vorhandene Anzeige von `x` (falls vorhanden) zu ändern. Die Verwendung von `redisplay` ist auch ein Hinweis an das Backend, dass `x` möglicherweise mehrere Male neu angezeigt werden kann, und das Backend kann entscheiden, die Anzeige bis (zum Beispiel) zur nächsten interaktiven Eingabeaufforderung zu verschieben.
