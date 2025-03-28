```
struct Response
    proto   :: String
    url     :: String
    status  :: Int
    message :: String
    headers :: Vector{Pair{String,String}}
end
```

`Response` es un tipo que captura las propiedades de una respuesta exitosa a una solicitud como un objeto. Tiene los siguientes campos:

  * `proto`: el protocolo que se utilizó para obtener la respuesta
  * `url`: la URL que se solicitó finalmente después de seguir las redirecciones
  * `status`: el código de estado de la respuesta, que indica éxito, fallo, etc.
  * `message`: un mensaje textual que describe la naturaleza de la respuesta
  * `headers`: cualquier encabezado que se devolvió con la respuesta

El significado y la disponibilidad de algunas de estas respuestas dependen del protocolo utilizado para la solicitud. Para muchos protocolos, incluidos HTTP/S y S/FTP, un código de estado 2xx indica una respuesta exitosa. Para respuestas en protocolos que no admiten encabezados, el vector de encabezados estará vacío. HTTP/2 no incluye un mensaje de estado, solo un código de estado, por lo que el mensaje estará vacío.
