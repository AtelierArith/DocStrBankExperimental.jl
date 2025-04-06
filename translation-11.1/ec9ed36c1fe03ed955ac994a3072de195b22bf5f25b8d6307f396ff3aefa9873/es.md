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

Realiza una solicitud a la URL dada, devolviendo un objeto `Response` que captura el estado, los encabezados y otra información sobre la respuesta. El cuerpo de la respuesta se escribe en `output` si se especifica y se descarta de lo contrario. Para solicitudes HTTP/S, si se proporciona un flujo `input`, se realiza una solicitud `PUT`; de lo contrario, si se proporciona un flujo `output`, se realiza una solicitud `GET`; si no se proporciona ninguno, se realiza una solicitud `HEAD`. Para otros protocolos, se utilizan métodos predeterminados apropiados según la combinación de entrada y salida solicitada. Las siguientes opciones difieren de la función `download`:

  * `input` permite proporcionar un cuerpo de solicitud; si se proporciona, se predetermina a la solicitud `PUT`
  * `progress` es una devolución de llamada que toma cuatro enteros para el progreso de carga y descarga
  * `throw` controla si se lanza o se devuelve un `RequestError` en caso de error de solicitud

Tenga en cuenta que, a diferencia de `download`, que lanza un error si la URL solicitada no se pudo descargar (indicado por un código de estado no 2xx), `request` devuelve un objeto `Response` sin importar cuál sea el código de estado de la respuesta. Si hay un error al obtener una respuesta, se lanza o se devuelve un `RequestError`.

Si se proporciona el argumento de palabra clave `interrupt`, debe ser un objeto `Base.Event`. Si se activa el evento mientras la solicitud está en progreso, la solicitud se cancelará y se lanzará un error. Esto se puede usar para interrumpir una solicitud de larga duración, por ejemplo, si el usuario desea cancelar una descarga.
