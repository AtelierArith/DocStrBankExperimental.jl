```
request(url;
    [ input = <none>, ]
    [ output = <none>, ]
    [ method = input ? "PUT" : output ? "GET" : "HEAD", ]
    [ headers = <none>, ]
    [ timeout = <none>, ]
    [ progress = <none>, ]
    [ verbose = false, ]
    [ debug = <none>, ]
    [ throw = true, ]
    [ downloader = <default>, ]
    [ interrupt = <none>, ]
) -> Union{Response, RequestError}

    url        :: AbstractString
    input      :: Union{AbstractString, AbstractCmd, IO}
    output     :: Union{AbstractString, AbstractCmd, IO}
    method     :: AbstractString
    headers    :: Union{AbstractVector, AbstractDict}
    timeout    :: Real
    progress   :: (dl_total, dl_now, ul_total, ul_now) --> Any
    verbose    :: Bool
    debug      :: (type, message) --> Any
    throw      :: Bool
    downloader :: Downloader
    interrupt  :: Base.Event
```

Machen Sie eine Anfrage an die angegebene URL und geben Sie ein `Response`-Objekt zurück, das den Status, die Header und andere Informationen zur Antwort erfasst. Der Körper der Antwort wird in `output` geschrieben, wenn angegeben, und andernfalls verworfen. Bei HTTP/S-Anfragen wird, wenn ein `input`-Stream angegeben ist, eine `PUT`-Anfrage gestellt; andernfalls, wenn ein `output`-Stream angegeben ist, wird eine `GET`-Anfrage gestellt; wenn weder angegeben ist, wird eine `HEAD`-Anfrage gestellt. Bei anderen Protokollen werden geeignete Standardmethoden basierend auf der angeforderten Kombination von Eingabe und Ausgabe verwendet. Die folgenden Optionen unterscheiden sich von der Funktion `download`:

  * `input` ermöglicht die Bereitstellung eines Anfragekörpers; wenn bereitgestellt, wird standardmäßig eine `PUT`-Anfrage gestellt
  * `progress` ist ein Callback, das vier Ganzzahlen für den Upload- und Download-Fortschritt entgegennimmt
  * `throw` steuert, ob bei einem Anforderungsfehler eine Ausnahme ausgelöst oder ein `RequestError` zurückgegeben wird

Beachten Sie, dass im Gegensatz zu `download`, das einen Fehler auslöst, wenn die angeforderte URL nicht heruntergeladen werden konnte (angezeigt durch einen Statuscode ungleich 2xx), `request` ein `Response`-Objekt zurückgibt, egal was der Statuscode der Antwort ist. Wenn es einen Fehler beim Erhalten einer Antwort gibt, wird ein `RequestError` ausgelöst oder zurückgegeben.

Wenn das Schlüsselwortargument `interrupt` bereitgestellt wird, muss es ein `Base.Event`-Objekt sein. Wenn das Ereignis ausgelöst wird, während die Anfrage in Bearbeitung ist, wird die Anfrage abgebrochen und ein Fehler wird ausgelöst. Dies kann verwendet werden, um eine lang laufende Anfrage zu unterbrechen, beispielsweise wenn der Benutzer einen Download abbrechen möchte.
