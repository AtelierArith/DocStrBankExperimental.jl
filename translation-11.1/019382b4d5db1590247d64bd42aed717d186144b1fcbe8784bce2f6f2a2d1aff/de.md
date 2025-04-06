```
download(url, [ output = tempname() ];
    [ method = "GET", ]
    [ headers = <none>, ]
    [ timeout = <none>, ]
    [ progress = <none>, ]
    [ verbose = false, ]
    [ debug = <none>, ]
    [ downloader = <default>, ]
) -> output

    url        :: AbstractString
    output     :: Union{AbstractString, AbstractCmd, IO}
    method     :: AbstractString
    headers    :: Union{AbstractVector, AbstractDict}
    timeout    :: Real
    progress   :: (total::Integer, now::Integer) --> Any
    verbose    :: Bool
    debug      :: (type, message) --> Any
    downloader :: Downloader
```

Laden Sie eine Datei von der angegebenen URL herunter und speichern Sie sie in `output` oder, falls nicht angegeben, an einem temporären Speicherort. Das `output` kann auch ein `IO`-Handle sein, in diesem Fall wird der Inhalt der Antwort an dieses Handle gestreamt und das Handle wird zurückgegeben. Wenn `output` ein Befehl ist, wird der Befehl ausgeführt und die Ausgabe wird über stdin an ihn gesendet.

Wenn das Schlüsselwortargument `downloader` bereitgestellt wird, muss es sich um ein `Downloader`-Objekt handeln. Ressourcen und Verbindungen werden zwischen Downloads, die vom selben `Downloader` durchgeführt werden, geteilt und automatisch bereinigt, wenn das Objekt garbage collected wird oder wenn in einem bestimmten Zeitraum keine Downloads mit ihm durchgeführt wurden. Weitere Informationen zur Konfiguration und Verwendung finden Sie in `Downloader`.

Wenn das Schlüsselwortargument `headers` bereitgestellt wird, muss es sich um einen Vektor oder ein Wörterbuch handeln, dessen Elemente alle Paare von Zeichenfolgen sind. Diese Paare werden als Header übergeben, wenn URLs mit Protokollen heruntergeladen werden, die sie unterstützen, wie z.B. HTTP/S.

Das Schlüsselwortargument `timeout` gibt einen Timeout für den Download in Sekunden an, mit einer Auflösung von Millisekunden. Standardmäßig ist kein Timeout festgelegt, dies kann jedoch auch ausdrücklich angefordert werden, indem ein Timeout-Wert von `Inf` übergeben wird. Separat, wenn 20 Sekunden vergehen, ohne dass Daten empfangen werden, wird der Download zeitlich begrenzt. Siehe erweiterte Hilfe, um zu erfahren, wie Sie diesen Timeout deaktivieren können.

Wenn das Schlüsselwortargument `progress` bereitgestellt wird, muss es sich um eine Callback-Funktion handeln, die aufgerufen wird, wann immer es Updates zur Größe und zum Status des laufenden Downloads gibt. Der Callback muss zwei ganzzahlige Argumente annehmen: `total` und `now`, die die Gesamtgröße des Downloads in Bytes und die Anzahl der bisher heruntergeladenen Bytes darstellen. Beachten Sie, dass `total` zu Beginn null ist und null bleibt, bis der Server einen Hinweis auf die Gesamtgröße des Downloads gibt (z.B. mit einem `Content-Length`-Header), was möglicherweise nie geschieht. Ein gut funktionierender Fortschritts-Callback sollte eine Gesamtgröße von null elegant behandeln.

Wenn die Option `verbose` auf true gesetzt ist, wird `libcurl`, das zur Implementierung der Download-Funktionalität verwendet wird, Debugging-Informationen an `stderr` ausgeben. Wenn die Option `debug` auf eine Funktion gesetzt ist, die zwei `String`-Argumente akzeptiert, wird die verbose-Option ignoriert und stattdessen werden die Daten, die an `stderr` ausgegeben worden wären, an den `debug`-Callback mit den Argumenten `type` und `message` übergeben. Das Argument `type` gibt an, welche Art von Ereignis aufgetreten ist, und ist eines von: `TEXT`, `HEADER IN`, `HEADER OUT`, `DATA IN`, `DATA OUT`, `SSL DATA IN` oder `SSL DATA OUT`. Das Argument `message` ist die Beschreibung des Debug-Ereignisses.

## Erweiterte Hilfe

Für weitere Anpassungen verwenden Sie einen [`Downloader`](@ref) und [`easy_hook`s](https://github.com/JuliaLang/Downloads.jl#mutual-tls-using-downloads). Um beispielsweise den 20-Sekunden-Timeout zu deaktivieren, wenn keine Daten empfangen werden, können Sie Folgendes verwenden:

```jl
downloader = Downloads.Downloader()
downloader.easy_hook = (easy, info) -> Downloads.Curl.setopt(easy, Downloads.Curl.CURLOPT_LOW_SPEED_TIME, 0)

Downloads.download("https://httpbingo.julialang.org/delay/30"; downloader)
```
