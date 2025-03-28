# Networking and Streams

Julia proporciona una rica interfaz para tratar con objetos de E/S en streaming, como terminales, tuberías y sockets TCP. Estos objetos permiten que los datos se envíen y reciban de manera similar a un flujo, lo que significa que los datos se procesan secuencialmente a medida que están disponibles. Esta interfaz, aunque es asíncrona a nivel del sistema, se presenta de manera sincrónica al programador. Esto se logra haciendo un uso intensivo de la funcionalidad de subprocesos cooperativos de Julia ([coroutine](@ref man-tasks)).

## Basic Stream I/O

Todos los flujos de Julia exponen al menos un método [`read`](@ref) y un método [`write`](@ref), tomando el flujo como su primer argumento, por ejemplo:

```julia-repl
julia> write(stdout, "Hello World");  # suppress return value 11 with ;
Hello World
julia> read(stdin, Char)

'\n': ASCII/Unicode U+000a (category Cc: Other, control)
```

Tenga en cuenta que [`write`](@ref) devuelve 11, el número de bytes (en `"Hello World"`) escritos en [`stdout`](@ref), pero este valor de retorno se suprime con el `;`.

Aquí se presionó Enter nuevamente para que Julia leyera la nueva línea. Ahora, como puedes ver en este ejemplo, [`write`](@ref) toma los datos a escribir como su segundo argumento, mientras que [`read`](@ref) toma el tipo de los datos a ser leídos como el segundo argumento.

Por ejemplo, para leer un simple arreglo de bytes, podríamos hacer:

```julia-repl
julia> x = zeros(UInt8, 4)
4-element Array{UInt8,1}:
 0x00
 0x00
 0x00
 0x00

julia> read!(stdin, x)
abcd
4-element Array{UInt8,1}:
 0x61
 0x62
 0x63
 0x64
```

Sin embargo, dado que esto es un poco engorroso, se proporcionan varios métodos de conveniencia. Por ejemplo, podríamos haber escrito lo anterior como:

```julia-repl
julia> read(stdin, 4)
abcd
4-element Array{UInt8,1}:
 0x61
 0x62
 0x63
 0x64
```

o si hubiéramos querido leer toda la línea en su lugar:

```julia-repl
julia> readline(stdin)
abcd
"abcd"
```

Tenga en cuenta que, dependiendo de la configuración de su terminal, su TTY ("terminal de teletipo") puede estar en modo de búfer de línea y, por lo tanto, puede requerir un enter adicional antes de que los datos de `stdin` se envíen a Julia. Al ejecutar Julia desde la línea de comandos en un TTY, la salida se envía a la consola por defecto y la entrada estándar se lee del teclado.

Para leer cada línea de [`stdin`](@ref) puedes usar [`eachline`](@ref):

```julia
for line in eachline(stdin)
    print("Found $line")
end
```

o [`read`](@ref) si quisieras leer por carácter en su lugar:

```julia
while !eof(stdin)
    x = read(stdin, Char)
    println("Found: $x")
end
```

## Text I/O

Tenga en cuenta que el método [`write`](@ref) mencionado anteriormente opera en flujos binarios. En particular, los valores no se convierten a ninguna representación de texto canónica, sino que se escriben tal como están:

```jldoctest
julia> write(stdout, 0x61);  # suppress return value 1 with ;
a
```

Tenga en cuenta que `a` se escribe en [`stdout`](@ref) por la función [`write`](@ref) y que el valor devuelto es `1` (ya que `0x61` es un byte).

Para la entrada/salida de texto, utiliza los métodos [`print`](@ref) o [`show`](@ref), dependiendo de tus necesidades (consulta la documentación de estos dos métodos para una discusión detallada sobre la diferencia entre ellos):

```jldoctest
julia> print(stdout, 0x61)
97
```

Consulta [Custom pretty-printing](@ref man-custom-pretty-printing) para obtener más información sobre cómo implementar métodos de visualización para tipos personalizados.

## IO Output Contextual Properties

A veces, la salida de IO puede beneficiarse de la capacidad de pasar información contextual a los métodos de mostrar. El objeto [`IOContext`](@ref) proporciona este marco para asociar metadatos arbitrarios con un objeto IO. Por ejemplo, `:compact => true` agrega un parámetro de sugerencia al objeto IO que indica que el método de mostrar invocado debería imprimir una salida más corta (si es aplicable). Consulte la documentación de `4d61726b646f776e2e436f64652822222c2022494f436f6e746578742229_40726566` para obtener una lista de propiedades comunes.

## Working with Files

Puedes escribir contenido en un archivo con el método `write(filename::String, content)`:

```julia-repl
julia> write("hello.txt", "Hello, World!")
13
```

*(`13` es el número de bytes escritos.)*

Puedes leer el contenido de un archivo con el método `read(filename::String)`, o `read(filename::String, String)` para obtener el contenido como una cadena:

```julia-repl
julia> read("hello.txt", String)
"Hello, World!"
```

### Advanced: streaming files

Los métodos `read` y `write` anteriores te permiten leer y escribir el contenido de archivos. Al igual que muchos otros entornos, Julia también tiene una función [`open`](@ref), que toma un nombre de archivo y devuelve un objeto [`IOStream`](@ref) que puedes usar para leer y escribir cosas desde el archivo. Por ejemplo, si tenemos un archivo, `hello.txt`, cuyo contenido es `¡Hola, Mundo!`:

```julia-repl
julia> f = open("hello.txt")
IOStream(<file hello.txt>)

julia> readlines(f)
1-element Array{String,1}:
 "Hello, World!"
```

Si deseas escribir en un archivo, puedes abrirlo con la bandera de escritura (`"w"`):

```julia-repl
julia> f = open("hello.txt","w")
IOStream(<file hello.txt>)

julia> write(f,"Hello again.")
12
```

Si examinas el contenido de `hello.txt` en este momento, notarás que está vacío; en realidad, no se ha escrito nada en el disco aún. Esto se debe a que el `IOStream` debe cerrarse antes de que la escritura se envíe realmente al disco:

```julia-repl
julia> close(f)
```

Examinar `hello.txt` nuevamente mostrará que su contenido ha cambiado.

Abrir un archivo, hacer algo con su contenido y cerrarlo nuevamente es un patrón muy común. Para facilitar esto, existe otra invocación de [`open`](@ref) que toma una función como su primer argumento y el nombre del archivo como su segundo, abre el archivo, llama a la función con el archivo como argumento y luego lo cierra nuevamente. Por ejemplo, dada una función:

```julia
function read_and_capitalize(f::IOStream)
    return uppercase(read(f, String))
end
```

Puedes llamar:

```julia-repl
julia> open(read_and_capitalize, "hello.txt")
"HELLO AGAIN."
```

para abrir `hello.txt`, llama a `read_and_capitalize` en él, cierra `hello.txt` y devuelve el contenido en mayúsculas.

Para evitar incluso tener que definir una función con nombre, puedes usar la sintaxis `do`, que crea una función anónima sobre la marcha:

```julia-repl
julia> open("hello.txt") do f
           uppercase(read(f, String))
       end
"HELLO AGAIN."
```

Si deseas redirigir stdout a un archivo

```# Open file for writing
out_file = open("output.txt", "w")

# Redirect stdout to file
redirect_stdout(out_file) do
    # Your code here
    println("This output goes to `out_file` via the `stdout` variable.")
end

# Close file
close(out_file)

```

Redirigir stdout a un archivo puede ayudarte a guardar y analizar la salida del programa, automatizar procesos y cumplir con los requisitos de cumplimiento.

## A simple TCP example

Vamos a entrar de lleno con un ejemplo simple que involucra sockets TCP. Esta funcionalidad está en un paquete de biblioteca estándar llamado `Sockets`. Primero, creemos un servidor simple:

```julia-repl
julia> using Sockets

julia> errormonitor(@async begin
           server = listen(2000)
           while true
               sock = accept(server)
               println("Hello World\n")
           end
       end)
Task (runnable) @0x00007fd31dc11ae0
```

Para aquellos familiarizados con la API de sockets de Unix, los nombres de los métodos se sentirán familiares, aunque su uso es algo más simple que la API de sockets de Unix en bruto. La primera llamada a [`listen`](@ref) creará un servidor esperando conexiones entrantes en el puerto especificado (2000) en este caso. La misma función también se puede utilizar para crear varios otros tipos de servidores:

```julia-repl
julia> listen(2000) # Listens on localhost:2000 (IPv4)
Sockets.TCPServer(active)

julia> listen(ip"127.0.0.1",2000) # Equivalent to the first
Sockets.TCPServer(active)

julia> listen(ip"::1",2000) # Listens on localhost:2000 (IPv6)
Sockets.TCPServer(active)

julia> listen(IPv4(0),2001) # Listens on port 2001 on all IPv4 interfaces
Sockets.TCPServer(active)

julia> listen(IPv6(0),2001) # Listens on port 2001 on all IPv6 interfaces
Sockets.TCPServer(active)

julia> listen("testsocket") # Listens on a UNIX domain socket
Sockets.PipeServer(active)

julia> listen("\\\\.\\pipe\\testsocket") # Listens on a Windows named pipe
Sockets.PipeServer(active)
```

Tenga en cuenta que el tipo de retorno de la última invocación es diferente. Esto se debe a que este servidor no escucha en TCP, sino en un pipe con nombre (Windows) o en un socket de dominio UNIX. También note que el formato del pipe con nombre de Windows debe seguir un patrón específico de tal manera que el prefijo del nombre (`\\.\pipe\`) identifique de manera única el [file type](https://docs.microsoft.com/windows/desktop/ipc/pipe-names). La diferencia entre TCP y los pipes con nombre o los sockets de dominio UNIX es sutil y tiene que ver con los métodos [`accept`](@ref) y [`connect`](@ref). El método `4d61726b646f776e2e436f64652822222c20226163636570742229_40726566` recupera una conexión con el cliente que se está conectando al servidor que acabamos de crear, mientras que la función `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` se conecta a un servidor utilizando el método especificado. La función `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` toma los mismos argumentos que [`listen`](@ref), así que, asumiendo que el entorno (es decir, host, cwd, etc.) es el mismo, deberías poder pasar los mismos argumentos a `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` que usaste para escuchar y establecer la conexión. Así que probemos eso (después de haber creado el servidor anterior):

```julia-repl
julia> connect(2000)
TCPSocket(open, 0 bytes waiting)

julia> Hello World
```

Como se esperaba, vimos "Hello World" impreso. Así que, analicemos realmente lo que sucedió detrás de escena. Cuando llamamos [`connect`](@ref), nos conectamos al servidor que acabamos de crear. Mientras tanto, la función accept devuelve una conexión del lado del servidor al socket recién creado e imprime "Hello World" para indicar que la conexión fue exitosa.

Una gran fortaleza de Julia es que, dado que la API se expone de manera sincrónica a pesar de que la E/S realmente ocurre de manera asincrónica, no tuvimos que preocuparnos por los callbacks o incluso por asegurarnos de que el servidor pudiera ejecutarse. Cuando llamamos a [`connect`](@ref), la tarea actual esperó a que se estableciera la conexión y solo continuó ejecutándose después de que eso se completó. En esta pausa, la tarea del servidor reanudó la ejecución (porque ahora había una solicitud de conexión disponible), aceptó la conexión, imprimió el mensaje y esperó al siguiente cliente. Leer y escribir funciona de la misma manera. Para ver esto, considera el siguiente servidor de eco simple:

```julia-repl
julia> errormonitor(@async begin
           server = listen(2001)
           while true
               sock = accept(server)
               @async while isopen(sock)
                   write(sock, readline(sock, keep=true))
               end
           end
       end)
Task (runnable) @0x00007fd31dc12e60

julia> clientside = connect(2001)
TCPSocket(RawFD(28) open, 0 bytes waiting)

julia> errormonitor(@async while isopen(clientside)
           write(stdout, readline(clientside, keep=true))
       end)
Task (runnable) @0x00007fd31dc11870

julia> println(clientside,"Hello World from the Echo Server")
Hello World from the Echo Server
```

Como con otros flujos, utiliza [`close`](@ref) para desconectar el socket:

```julia-repl
julia> close(clientside)
```

## Resolving IP Addresses

Uno de los métodos [`connect`](@ref) que no sigue los métodos [`listen`](@ref) es `connect(host::String,port)`, que intentará conectarse al host dado por el parámetro `host` en el puerto dado por el parámetro `port`. Te permite hacer cosas como:

```julia-repl
julia> connect("google.com", 80)
TCPSocket(RawFD(30) open, 0 bytes waiting)
```

En la base de esta funcionalidad está [`getaddrinfo`](@ref), que realizará la resolución de direcciones apropiada:

```julia-repl
julia> getaddrinfo("google.com")
ip"74.125.226.225"
```

## Asynchronous I/O

Todas las operaciones de entrada/salida expuestas por [`Base.read`](@ref) y [`Base.write`](@ref) se pueden realizar de forma asíncrona mediante el uso de [coroutines](@ref man-tasks). Puedes crear una nueva coroutine para leer o escribir en un flujo utilizando el macro [`@async`](@ref):

```julia-repl
julia> task = @async open("foo.txt", "w") do io
           write(io, "Hello, World!")
       end;

julia> wait(task)

julia> readlines("foo.txt")
1-element Array{String,1}:
 "Hello, World!"
```

Es común encontrarse en situaciones donde deseas realizar múltiples operaciones asíncronas de manera concurrente y esperar hasta que todas hayan finalizado. Puedes usar el macro [`@sync`](@ref) para hacer que tu programa se bloquee hasta que todas las corutinas que envuelve hayan salido:

```julia-repl
julia> using Sockets

julia> @sync for hostname in ("google.com", "github.com", "julialang.org")
           @async begin
               conn = connect(hostname, 80)
               write(conn, "GET / HTTP/1.1\r\nHost:$(hostname)\r\n\r\n")
               readline(conn, keep=true)
               println("Finished connection to $(hostname)")
           end
       end
Finished connection to google.com
Finished connection to julialang.org
Finished connection to github.com
```

## Multicast

Julia soporta [multicast](https://datatracker.ietf.org/doc/html/rfc1112) sobre IPv4 e IPv6 utilizando el Protocolo de Datagramas de Usuario ([UDP](https://datatracker.ietf.org/doc/html/rfc768)) como transporte.

A diferencia del Protocolo de Control de Transmisión ([TCP](https://datatracker.ietf.org/doc/html/rfc793)), UDP no hace casi ninguna suposición sobre las necesidades de la aplicación. TCP proporciona control de flujo (acelera y desacelera para maximizar el rendimiento), fiabilidad (los paquetes perdidos o corruptos se retransmiten automáticamente), secuenciación (los paquetes se ordenan por el sistema operativo antes de ser entregados a la aplicación), tamaño de segmento y configuración y finalización de sesión. UDP no proporciona tales características.

Un uso común de UDP es en aplicaciones de multidifusión. TCP es un protocolo con estado para la comunicación entre exactamente dos dispositivos. UDP puede utilizar direcciones de multidifusión especiales para permitir la comunicación simultánea entre muchos dispositivos.

### Receiving IP Multicast Packets

Para transmitir datos a través de multicast UDP, simplemente `recv` en el socket, y el primer paquete recibido será devuelto. ¡Ten en cuenta que puede no ser el primer paquete que enviaste!

```julia
using Sockets
group = ip"228.5.6.7"
socket = Sockets.UDPSocket()
bind(socket, ip"0.0.0.0", 6789)
join_multicast_group(socket, group)
println(String(recv(socket)))
leave_multicast_group(socket, group)
close(socket)
```

### Sending IP Multicast Packets

Para transmitir datos a través de UDP multicast, simplemente `send` al socket. Tenga en cuenta que no es necesario que un emisor se una al grupo multicast.

```julia
using Sockets
group = ip"228.5.6.7"
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv4")
close(socket)
```

### IPv6 Example

Este ejemplo ofrece la misma funcionalidad que el programa anterior, pero utiliza IPv6 como el protocolo de capa de red.

Escucha:

```julia
using Sockets
group = Sockets.IPv6("ff05::5:6:7")
socket = Sockets.UDPSocket()
bind(socket, Sockets.IPv6("::"), 6789)
join_multicast_group(socket, group)
println(String(recv(socket)))
leave_multicast_group(socket, group)
close(socket)
```

Remitente:

```julia
using Sockets
group = Sockets.IPv6("ff05::5:6:7")
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv6")
close(socket)
```
