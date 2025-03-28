```
struct Response
    proto   :: String
    url     :: String
    status  :: Int
    message :: String
    headers :: Vector{Pair{String,String}}
end
```

`Response` ist ein Typ, der die Eigenschaften einer erfolgreichen Antwort auf eine Anfrage als Objekt erfasst. Es hat die folgenden Felder:

  * `proto`: das Protokoll, das verwendet wurde, um die Antwort zu erhalten
  * `url`: die URL, die letztendlich nach dem Folgen von Weiterleitungen angefordert wurde
  * `status`: der Statuscode der Antwort, der Erfolg, Misserfolg usw. anzeigt
  * `message`: eine textuelle Nachricht, die die Art der Antwort beschreibt
  * `headers`: alle Header, die mit der Antwort zurückgegeben wurden

Die Bedeutung und Verfügbarkeit einiger dieser Antworten hängt vom verwendeten Protokoll für die Anfrage ab. Für viele Protokolle, einschließlich HTTP/S und S/FTP, zeigt ein 2xx-Statuscode eine erfolgreiche Antwort an. Bei Antworten in Protokollen, die keine Header unterstützen, wird der Header-Vektor leer sein. HTTP/2 enthält keine Statusnachricht, nur einen Statuscode, sodass die Nachricht leer sein wird.
