```
struct RequestError <: ErrorException
    url      :: String
    code     :: Int
    message  :: String
    response :: Response
end
```

`RequestError` ist ein Typ, der die Eigenschaften einer fehlgeschlagenen Antwort auf eine Anfrage als Ausnahmeobjekt erfasst:

  * `url`: die ursprüngliche URL, die angefordert wurde, ohne Weiterleitungen
  * `code`: der libcurl-Fehlercode; `0`, wenn ein nur protokollbezogener Fehler aufgetreten ist
  * `message`: die libcurl-Fehlermeldung, die angibt, was schiefgelaufen ist
  * `response`: Antwortobjekt, das die verfügbaren Antwortinformationen erfasst

Der gleiche `RequestError`-Typ wird von `download` ausgelöst, wenn die Anfrage erfolgreich war, aber ein protokollbezogener Fehler durch einen Statuscode angezeigt wurde, der nicht im 2xx-Bereich liegt, in diesem Fall wird `code` null sein und das Feld `message` wird der leere String sein. Die `request`-API wirft nur einen `RequestError`, wenn der libcurl-Fehler `code` ungleich null ist, in diesem Fall hat das enthaltene `response`-Objekt wahrscheinlich einen `status` von null und eine leere Nachricht. Es gibt jedoch Situationen, in denen ein curl-Fehler aufgrund eines Protokollfehlers ausgelöst wird, in diesem Fall können sowohl der innere als auch der äußere Code und die Nachricht von Interesse sein.
