# Networking and Streams

Julia bietet eine umfangreiche Schnittstelle zur Verarbeitung von Streaming-I/O-Objekten wie Terminals, Pipes und TCP-Sockets. Diese Objekte ermöglichen es, Daten in einem streamähnlichen Format zu senden und zu empfangen, was bedeutet, dass Daten sequenziell verarbeitet werden, sobald sie verfügbar sind. Diese Schnittstelle, obwohl auf Systemebene asynchron, wird dem Programmierer in einer synchronen Weise präsentiert. Dies wird erreicht, indem die Funktionalität des kooperativen Threadings von Julia ([coroutine](@ref man-tasks)) intensiv genutzt wird.

## Basic Stream I/O

Alle Julia-Streams bieten mindestens eine [`read`](@ref) und eine [`write`](@ref) Methode an, die den Stream als erstes Argument nimmt, z.B.:

```julia-repl
julia> write(stdout, "Hello World");  # suppress return value 11 with ;
Hello World
julia> read(stdin, Char)

'\n': ASCII/Unicode U+000a (category Cc: Other, control)
```

Beachten Sie, dass [`write`](@ref) 11 zurückgibt, die Anzahl der Bytes (in `"Hello World"`), die in [`stdout`](@ref) geschrieben wurden, aber dieser Rückgabewert wird mit dem `;` unterdrückt.

Hier wurde erneut die Eingabetaste gedrückt, damit Julia die neue Zeile liest. Wie Sie aus diesem Beispiel sehen können, nimmt [`write`](@ref) die zu schreibenden Daten als zweiten Parameter, während [`read`](@ref) den Typ der zu lesenden Daten als zweiten Parameter übernimmt.

Um beispielsweise ein einfaches Byte-Array zu lesen, könnten wir Folgendes tun:

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

Allerdings ist dies etwas umständlich, daher gibt es mehrere praktische Methoden. Zum Beispiel hätten wir das Obige so schreiben können:

```julia-repl
julia> read(stdin, 4)
abcd
4-element Array{UInt8,1}:
 0x61
 0x62
 0x63
 0x64
```

oder wenn wir die gesamte Zeile lesen wollten:

```julia-repl
julia> readline(stdin)
abcd
"abcd"
```

Beachten Sie, dass je nach Ihren Terminaleinstellungen Ihr TTY ("Teletype-Terminal") zeilenpuffert sein kann und daher möglicherweise ein zusätzliches Enter erforderlich ist, bevor die `stdin`-Daten an Julia gesendet werden. Wenn Sie Julia von der Befehlszeile in einem TTY ausführen, wird die Ausgabe standardmäßig an die Konsole gesendet, und die Standardeingabe wird von der Tastatur gelesen.

Um jede Zeile von [`stdin`](@ref) zu lesen, können Sie [`eachline`](@ref) verwenden:

```julia
for line in eachline(stdin)
    print("Found $line")
end
```

oder [`read`](@ref), wenn Sie es zeichenweise lesen möchten:

```julia
while !eof(stdin)
    x = read(stdin, Char)
    println("Found: $x")
end
```

## Text I/O

Beachten Sie, dass die oben erwähnte [`write`](@ref) Methode auf binären Streams arbeitet. Insbesondere werden Werte nicht in eine kanonische Textdarstellung umgewandelt, sondern so ausgegeben, wie sie sind:

```jldoctest
julia> write(stdout, 0x61);  # suppress return value 1 with ;
a
```

Beachten Sie, dass `a` von der Funktion [`stdout`](@ref) in [`write`](@ref) geschrieben wird und dass der zurückgegebene Wert `1` ist (da `0x61` ein Byte ist).

Für die Text-Eingabe/Ausgabe verwenden Sie die [`print`](@ref) oder [`show`](@ref) Methoden, je nach Ihren Bedürfnissen (siehe die Dokumentation für diese beiden Methoden für eine detaillierte Diskussion über die Unterschiede zwischen ihnen):

```jldoctest
julia> print(stdout, 0x61)
97
```

Siehe [Custom pretty-printing](@ref man-custom-pretty-printing) für weitere Informationen zur Implementierung von Anzeige-Methoden für benutzerdefinierte Typen.

## IO Output Contextual Properties

Manchmal kann die IO-Ausgabe von der Möglichkeit profitieren, kontextuelle Informationen in die Anzeigemethoden zu übergeben. Das [`IOContext`](@ref)-Objekt bietet dieses Framework, um beliebige Metadaten mit einem IO-Objekt zu verknüpfen. Zum Beispiel fügt `:compact => true` dem IO-Objekt einen Hinweisparameter hinzu, dass die aufgerufene Anzeigemethode eine kürzere Ausgabe drucken sollte (sofern zutreffend). Siehe die Dokumentation des `4d61726b646f776e2e436f64652822222c2022494f436f6e746578742229_40726566` für eine Liste gängiger Eigenschaften.

## Working with Files

Sie können Inhalte mit der Methode `write(filename::String, content)` in eine Datei schreiben:

```julia-repl
julia> write("hello.txt", "Hello, World!")
13
```

*(`13` ist die Anzahl der geschriebenen Bytes.)*

Sie können den Inhalt einer Datei mit der Methode `read(filename::String)` lesen, oder `read(filename::String, String)`, um den Inhalt als String zu lesen:

```julia-repl
julia> read("hello.txt", String)
"Hello, World!"
```

### Advanced: streaming files

Die `read`- und `write`-Methoden oben ermöglichen es Ihnen, den Inhalt von Dateien zu lesen und zu schreiben. Wie in vielen anderen Umgebungen hat Julia auch eine [`open`](@ref)-Funktion, die einen Dateinamen entgegennimmt und ein [`IOStream`](@ref)-Objekt zurückgibt, das Sie verwenden können, um Dinge aus der Datei zu lesen und zu schreiben. Zum Beispiel, wenn wir eine Datei `hello.txt` haben, deren Inhalt `Hello, World!` ist:

```julia-repl
julia> f = open("hello.txt")
IOStream(<file hello.txt>)

julia> readlines(f)
1-element Array{String,1}:
 "Hello, World!"
```

Wenn Sie in eine Datei schreiben möchten, können Sie sie mit dem Schreib- (`"w"`) Flag öffnen:

```julia-repl
julia> f = open("hello.txt","w")
IOStream(<file hello.txt>)

julia> write(f,"Hello again.")
12
```

Wenn Sie den Inhalt von `hello.txt` zu diesem Zeitpunkt überprüfen, werden Sie feststellen, dass es leer ist; es wurde noch nichts auf die Festplatte geschrieben. Dies liegt daran, dass der `IOStream` geschlossen werden muss, bevor der Schreibvorgang tatsächlich auf die Festplatte übertragen wird:

```julia-repl
julia> close(f)
```

Das Überprüfen von `hello.txt` erneut zeigt, dass sich der Inhalt geändert hat.

Das Öffnen einer Datei, das Bearbeiten ihres Inhalts und das anschließende Schließen ist ein sehr häufiges Muster. Um dies zu erleichtern, gibt es einen weiteren Aufruf von [`open`](@ref), der eine Funktion als erstes Argument und den Dateinamen als zweites Argument nimmt, die Datei öffnet, die Funktion mit der Datei als Argument aufruft und sie dann wieder schließt. Zum Beispiel, gegeben eine Funktion:

```julia
function read_and_capitalize(f::IOStream)
    return uppercase(read(f, String))
end
```

Du kannst anrufen:

```julia-repl
julia> open(read_and_capitalize, "hello.txt")
"HELLO AGAIN."
```

Um `hello.txt` zu öffnen, rufen Sie `read_and_capitalize` darauf auf, schließen Sie `hello.txt` und geben Sie den kapitalisierten Inhalt zurück.

Um zu vermeiden, dass man überhaupt eine benannte Funktion definieren muss, kann man die `do`-Syntax verwenden, die eine anonyme Funktion im Handumdrehen erstellt:

```julia-repl
julia> open("hello.txt") do f
           uppercase(read(f, String))
       end
"HELLO AGAIN."
```

Wenn Sie stdout in eine Datei umleiten möchten

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

Die Umleitung von stdout in eine Datei kann Ihnen helfen, Programmausgaben zu speichern und zu analysieren, Prozesse zu automatisieren und Compliance-Anforderungen zu erfüllen.

## A simple TCP example

Lass uns direkt mit einem einfachen Beispiel zu TCP-Sockets einsteigen. Diese Funktionalität befindet sich in einem Standardbibliothekspaket namens `Sockets`. Lassen Sie uns zunächst einen einfachen Server erstellen:

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

Für diejenigen, die mit der Unix-Socket-API vertraut sind, werden die Methodennamen vertraut erscheinen, obwohl ihre Verwendung etwas einfacher ist als bei der rohen Unix-Socket-API. Der erste Aufruf von [`listen`](@ref) erstellt einen Server, der auf eingehende Verbindungen an dem angegebenen Port (2000) in diesem Fall wartet. Dieselbe Funktion kann auch verwendet werden, um verschiedene andere Arten von Servern zu erstellen:

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

Beachten Sie, dass der Rückgabewert des letzten Aufrufs unterschiedlich ist. Dies liegt daran, dass dieser Server nicht über TCP hört, sondern über eine benannte Pipe (Windows) oder einen UNIX-Domänensocket. Beachten Sie auch, dass das Format der Windows-benannten Pipe einem bestimmten Muster folgen muss, sodass das Namenspräfix (`\\.\pipe\`) die [file type](https://docs.microsoft.com/windows/desktop/ipc/pipe-names) eindeutig identifiziert. Der Unterschied zwischen TCP und benannten Pipes oder UNIX-Domänensockets ist subtil und hat mit den Methoden [`accept`](@ref) und [`connect`](@ref) zu tun. Die Methode `4d61726b646f776e2e436f64652822222c20226163636570742229_40726566` ruft eine Verbindung zum Client ab, der sich mit dem Server verbindet, den wir gerade erstellt haben, während die Funktion `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` eine Verbindung zu einem Server unter Verwendung der angegebenen Methode herstellt. Die Funktion `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` nimmt die gleichen Argumente wie [`listen`](@ref) entgegen, sodass Sie, vorausgesetzt die Umgebung (d.h. Host, cwd usw.) ist dieselbe, in der Lage sein sollten, die gleichen Argumente an `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` zu übergeben, wie Sie es getan haben, um die Verbindung herzustellen. Lassen Sie uns das ausprobieren (nachdem wir den oben genannten Server erstellt haben):

```julia-repl
julia> connect(2000)
TCPSocket(open, 0 bytes waiting)

julia> Hello World
```

Wie erwartet sahen wir "Hello World" ausgegeben. Lassen Sie uns also tatsächlich analysieren, was hinter den Kulissen passiert ist. Als wir [`connect`](@ref) aufgerufen haben, haben wir eine Verbindung zu dem Server hergestellt, den wir gerade erstellt hatten. In der Zwischenzeit gibt die Accept-Funktion eine serverseitige Verbindung zu dem neu erstellten Socket zurück und druckt "Hello World", um anzuzeigen, dass die Verbindung erfolgreich war.

Eine große Stärke von Julia ist, dass die API synchron exponiert ist, obwohl die E/A tatsächlich asynchron erfolgt. Wir mussten uns also keine Gedanken über Rückrufe machen oder sicherstellen, dass der Server läuft. Als wir [`connect`](@ref) aufgerufen haben, wartete die aktuelle Aufgabe darauf, dass die Verbindung hergestellt wurde, und setzte die Ausführung erst fort, nachdem dies geschehen war. In dieser Pause setzte die Serveraufgabe die Ausführung fort (da jetzt eine Verbindungsanfrage verfügbar war), akzeptierte die Verbindung, druckte die Nachricht aus und wartete auf den nächsten Client. Lesen und Schreiben funktioniert auf die gleiche Weise. Um dies zu sehen, betrachten Sie den folgenden einfachen Echo-Server:

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

Wie bei anderen Streams verwenden Sie [`close`](@ref), um die Verbindung zu trennen:

```julia-repl
julia> close(clientside)
```

## Resolving IP Addresses

Eine der [`connect`](@ref) Methoden, die nicht den [`listen`](@ref) Methoden folgt, ist `connect(host::String,port)`, die versucht, eine Verbindung zum Host herzustellen, der durch den `host`-Parameter angegeben ist, über den Port, der durch den `port`-Parameter angegeben ist. Es ermöglicht Ihnen, Dinge zu tun wie:

```julia-repl
julia> connect("google.com", 80)
TCPSocket(RawFD(30) open, 0 bytes waiting)
```

Am Fuße dieser Funktionalität steht [`getaddrinfo`](@ref), das die entsprechende Adressauflösung durchführt:

```julia-repl
julia> getaddrinfo("google.com")
ip"74.125.226.225"
```

## Asynchronous I/O

Alle I/O-Operationen, die von [`Base.read`](@ref) und [`Base.write`](@ref) bereitgestellt werden, können asynchron durch die Verwendung von [coroutines](@ref man-tasks) durchgeführt werden. Sie können eine neue Coroutine erstellen, um von einem Stream zu lesen oder in einen Stream zu schreiben, indem Sie das [`@async`](@ref)-Makro verwenden:

```julia-repl
julia> task = @async open("foo.txt", "w") do io
           write(io, "Hello, World!")
       end;

julia> wait(task)

julia> readlines("foo.txt")
1-element Array{String,1}:
 "Hello, World!"
```

Es ist üblich, auf Situationen zu stoßen, in denen Sie mehrere asynchrone Operationen gleichzeitig ausführen und warten möchten, bis sie alle abgeschlossen sind. Sie können das [`@sync`](@ref)-Makro verwenden, um Ihr Programm zu blockieren, bis alle Coroutinen, die es umschließt, beendet sind:

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

Julia unterstützt [multicast](https://datatracker.ietf.org/doc/html/rfc1112) über IPv4 und IPv6 unter Verwendung des User Datagram Protocols ([UDP](https://datatracker.ietf.org/doc/html/rfc768)) als Transport.

Im Gegensatz zum Transmission Control Protocol ([TCP](https://datatracker.ietf.org/doc/html/rfc793)) trifft UDP fast keine Annahmen über die Bedürfnisse der Anwendung. TCP bietet Flusskontrolle (es beschleunigt und verlangsamt, um die Durchsatzrate zu maximieren), Zuverlässigkeit (verlorene oder beschädigte Pakete werden automatisch erneut gesendet), Sequenzierung (Pakete werden vom Betriebssystem in der Reihenfolge angeordnet, bevor sie der Anwendung übergeben werden), Segmentgröße sowie Sitzungsaufbau und -abbau. UDP bietet keine solchen Funktionen.

Ein häufiger Anwendungsfall für UDP sind Multicast-Anwendungen. TCP ist ein zustandsbehaftetes Protokoll für die Kommunikation zwischen genau zwei Geräten. UDP kann spezielle Multicast-Adressen verwenden, um eine gleichzeitige Kommunikation zwischen vielen Geräten zu ermöglichen.

### Receiving IP Multicast Packets

Um Daten über UDP-Multicast zu übertragen, rufen Sie einfach `recv` auf dem Socket auf, und das erste empfangene Paket wird zurückgegeben. Beachten Sie, dass es jedoch möglicherweise nicht das erste Paket ist, das Sie gesendet haben!

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

Um Daten über UDP-Multicast zu übertragen, senden Sie einfach an den Socket. Beachten Sie, dass es für einen Sender nicht erforderlich ist, der Multicast-Gruppe beizutreten.

```julia
using Sockets
group = ip"228.5.6.7"
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv4")
close(socket)
```

### IPv6 Example

Dieses Beispiel bietet die gleiche Funktionalität wie das vorherige Programm, verwendet jedoch IPv6 als Protokoll der Netzwerkschicht.

Zuhörer:

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

Absender:

```julia
using Sockets
group = Sockets.IPv6("ff05::5:6:7")
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv6")
close(socket)
```
