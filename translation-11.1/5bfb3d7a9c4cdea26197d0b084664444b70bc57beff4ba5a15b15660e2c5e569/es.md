```
struct RequestError <: ErrorException
    url      :: String
    code     :: Int
    message  :: String
    response :: Response
end
```

`RequestError` es un tipo que captura las propiedades de una respuesta fallida a una solicitud como un objeto de excepción:

  * `url`: la URL original que se solicitó sin redirecciones
  * `code`: el código de error de libcurl; `0` si ocurrió un error solo de protocolo
  * `message`: el mensaje de error de libcurl que indica qué salió mal
  * `response`: objeto de respuesta que captura la información de respuesta disponible

El mismo tipo `RequestError` es lanzado por `download` si la solicitud fue exitosa pero hubo un error a nivel de protocolo indicado por un código de estado que no está en el rango de 2xx, en cuyo caso `code` será cero y el campo `message` será la cadena vacía. La API `request` solo lanza un `RequestError` si el código de error de libcurl es distinto de cero, en cuyo caso el objeto `response` incluido probablemente tendrá un `status` de cero y un mensaje vacío. Sin embargo, hay situaciones en las que se lanza un error a nivel de curl debido a un error de protocolo, en cuyo caso tanto el código como el mensaje interno y externo pueden ser de interés.
