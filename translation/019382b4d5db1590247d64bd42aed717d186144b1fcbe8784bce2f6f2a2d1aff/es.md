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

Descarga un archivo desde la URL dada, guardándolo en `output` o, si no se especifica, en una ruta temporal. El `output` también puede ser un manejador `IO`, en cuyo caso el cuerpo de la respuesta se transmite a ese manejador y se devuelve el manejador. Si `output` es un comando, el comando se ejecuta y la salida se envía a él a través de stdin.

Si se proporciona el argumento de palabra clave `downloader`, debe ser un objeto `Downloader`. Los recursos y conexiones se compartirán entre las descargas realizadas por el mismo `Downloader` y se limpiarán automáticamente cuando el objeto sea recolectado por el garbage collector o no se hayan realizado descargas con él durante un período de gracia. Consulta `Downloader` para obtener más información sobre la configuración y el uso.

Si se proporciona el argumento de palabra clave `headers`, debe ser un vector o diccionario cuyos elementos son todos pares de cadenas. Estos pares se pasan como encabezados al descargar URLs con protocolos que los admiten, como HTTP/S.

El argumento de palabra clave `timeout` especifica un tiempo de espera para que la descarga se complete en segundos, con una resolución de milisegundos. Por defecto, no se establece ningún tiempo de espera, pero esto también se puede solicitar explícitamente pasando un valor de tiempo de espera de `Inf`. Por separado, si transcurren 20 segundos sin recibir ningún dato, la descarga se agotará. Consulta la ayuda extendida para saber cómo desactivar este tiempo de espera.

Si se proporciona el argumento de palabra clave `progress`, debe ser una función de callback que se llamará cada vez que haya actualizaciones sobre el tamaño y el estado de la descarga en curso. El callback debe tomar dos argumentos enteros: `total` y `now`, que son el tamaño total de la descarga en bytes y el número de bytes que se han descargado hasta ahora. Ten en cuenta que `total` comienza en cero y permanece en cero hasta que el servidor da una indicación del tamaño total de la descarga (por ejemplo, con un encabezado `Content-Length`), lo que puede que nunca suceda. Por lo tanto, un callback de progreso bien comportado debería manejar un tamaño total de cero de manera adecuada.

Si la opción `verbose` se establece en verdadero, `libcurl`, que se utiliza para implementar la funcionalidad de descarga, imprimirá información de depuración en `stderr`. Si la opción `debug` se establece en una función que acepta dos argumentos `String`, entonces se ignora la opción verbose y, en su lugar, los datos que se habrían impreso en `stderr` se pasan al callback `debug` con los argumentos `type` y `message`. El argumento `type` indica qué tipo de evento ha ocurrido y es uno de: `TEXT`, `HEADER IN`, `HEADER OUT`, `DATA IN`, `DATA OUT`, `SSL DATA IN` o `SSL DATA OUT`. El argumento `message` es la descripción del evento de depuración.

## Ayuda Extendida

Para una mayor personalización, utiliza un [`Downloader`](@ref) y [`easy_hook`s](https://github.com/JuliaLang/Downloads.jl#mutual-tls-using-downloads). Por ejemplo, para desactivar el tiempo de espera de 20 segundos cuando no se recibe ningún dato, puedes usar lo siguiente:

```jl
downloader = Downloads.Downloader()
downloader.easy_hook = (easy, info) -> Downloads.Curl.setopt(easy, Downloads.Curl.CURLOPT_LOW_SPEED_TIME, 0)

Downloads.download("https://httpbingo.julialang.org/delay/30"; downloader)
```
