# Networking and Streams

Julia fournit une interface riche pour gérer des objets d'E/S en streaming tels que des terminaux, des tuyaux et des sockets TCP. Ces objets permettent d'envoyer et de recevoir des données de manière fluide, ce qui signifie que les données sont traitées séquentiellement au fur et à mesure qu'elles deviennent disponibles. Cette interface, bien qu'asynchrone au niveau du système, est présentée de manière synchrone au programmeur. Cela est réalisé en utilisant largement la fonctionnalité de threading coopératif de Julia ([coroutine](@ref man-tasks)).

## Basic Stream I/O

Tous les flux Julia exposent au moins une méthode [`read`](@ref) et une méthode [`write`](@ref), prenant le flux comme leur premier argument, par exemple :

```julia-repl
julia> write(stdout, "Hello World");  # suppress return value 11 with ;
Hello World
julia> read(stdin, Char)

'\n': ASCII/Unicode U+000a (category Cc: Other, control)
```

Notez que [`write`](@ref) renvoie 11, le nombre d'octets (dans `"Hello World"`) écrits dans [`stdout`](@ref), mais cette valeur de retour est supprimée avec le `;`.

Ici, la touche Entrée a été pressée à nouveau afin que Julia puisse lire la nouvelle ligne. Maintenant, comme vous pouvez le voir dans cet exemple, [`write`](@ref) prend les données à écrire comme son deuxième argument, tandis que [`read`](@ref) prend le type des données à lire comme son deuxième argument.

Par exemple, pour lire un tableau d'octets simple, nous pourrions faire :

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

Cependant, comme cela est légèrement encombrant, plusieurs méthodes de commodité sont fournies. Par exemple, nous aurions pu écrire ce qui précède comme :

```julia-repl
julia> read(stdin, 4)
abcd
4-element Array{UInt8,1}:
 0x61
 0x62
 0x63
 0x64
```

ou si nous avions voulu lire toute la ligne à la place :

```julia-repl
julia> readline(stdin)
abcd
"abcd"
```

Notez qu'en fonction de vos paramètres de terminal, votre TTY ("terminal teletype") peut être en mode tampon de ligne et peut donc nécessiter une entrée supplémentaire avant que les données `stdin` ne soient envoyées à Julia. Lorsque vous exécutez Julia depuis la ligne de commande dans un TTY, la sortie est envoyée à la console par défaut, et l'entrée standard est lue à partir du clavier.

Pour lire chaque ligne de [`stdin`](@ref), vous pouvez utiliser [`eachline`](@ref) :

```julia
for line in eachline(stdin)
    print("Found $line")
end
```

ou [`read`](@ref) si vous vouliez lire par caractère à la place :

```julia
while !eof(stdin)
    x = read(stdin, Char)
    println("Found: $x")
end
```

## Text I/O

Notez que la méthode [`write`](@ref) mentionnée ci-dessus fonctionne sur des flux binaires. En particulier, les valeurs ne sont pas converties en aucune représentation textuelle canonique mais sont écrites telles quelles :

```jldoctest
julia> write(stdout, 0x61);  # suppress return value 1 with ;
a
```

Notez que `a` est écrit dans [`stdout`](@ref) par la fonction [`write`](@ref) et que la valeur retournée est `1` (puisque `0x61` est un octet).

Pour l'entrée/sortie de texte, utilisez les méthodes [`print`](@ref) ou [`show`](@ref), selon vos besoins (voir la documentation pour ces deux méthodes pour une discussion détaillée de la différence entre elles) :

```jldoctest
julia> print(stdout, 0x61)
97
```

Voir [Custom pretty-printing](@ref man-custom-pretty-printing) pour plus d'informations sur la façon d'implémenter des méthodes d'affichage pour des types personnalisés.

## IO Output Contextual Properties

Parfois, la sortie IO peut bénéficier de la capacité à passer des informations contextuelles dans les méthodes d'affichage. L'objet [`IOContext`](@ref) fournit ce cadre pour associer des métadonnées arbitraires à un objet IO. Par exemple, `:compact => true` ajoute un paramètre d'indication à l'objet IO indiquant que la méthode d'affichage invoquée devrait imprimer une sortie plus courte (si applicable). Consultez la documentation de `4d61726b646f776e2e436f64652822222c2022494f436f6e746578742229_40726566` pour une liste des propriétés courantes.

## Working with Files

Vous pouvez écrire du contenu dans un fichier avec la méthode `write(filename::String, content)` :

```julia-repl
julia> write("hello.txt", "Hello, World!")
13
```

*(`13` est le nombre d'octets écrits.)*

Vous pouvez lire le contenu d'un fichier avec la méthode `read(filename::String)`, ou `read(filename::String, String)` pour obtenir le contenu sous forme de chaîne :

```julia-repl
julia> read("hello.txt", String)
"Hello, World!"
```

### Advanced: streaming files

Les méthodes `read` et `write` ci-dessus vous permettent de lire et d'écrire le contenu des fichiers. Comme dans de nombreux autres environnements, Julia dispose également d'une fonction [`open`](@ref), qui prend un nom de fichier et renvoie un objet [`IOStream`](@ref) que vous pouvez utiliser pour lire et écrire des choses à partir du fichier. Par exemple, si nous avons un fichier, `hello.txt`, dont le contenu est `Hello, World!` :

```julia-repl
julia> f = open("hello.txt")
IOStream(<file hello.txt>)

julia> readlines(f)
1-element Array{String,1}:
 "Hello, World!"
```

Si vous souhaitez écrire dans un fichier, vous pouvez l'ouvrir avec le drapeau d'écriture (`"w"`) :

```julia-repl
julia> f = open("hello.txt","w")
IOStream(<file hello.txt>)

julia> write(f,"Hello again.")
12
```

Si vous examinez le contenu de `hello.txt` à ce stade, vous remarquerez qu'il est vide ; rien n'a réellement été écrit sur le disque pour l'instant. Cela est dû au fait que le `IOStream` doit être fermé avant que l'écriture ne soit réellement vidée sur le disque :

```julia-repl
julia> close(f)
```

Examiner à nouveau `hello.txt` montrera que son contenu a été modifié.

Ouvrir un fichier, faire quelque chose avec son contenu, puis le fermer à nouveau est un motif très courant. Pour faciliter cela, il existe une autre invocation de [`open`](@ref) qui prend une fonction comme premier argument et le nom du fichier comme second, ouvre le fichier, appelle la fonction avec le fichier comme argument, puis le ferme à nouveau. Par exemple, étant donné une fonction :

```julia
function read_and_capitalize(f::IOStream)
    return uppercase(read(f, String))
end
```

Vous pouvez appeler :

```julia-repl
julia> open(read_and_capitalize, "hello.txt")
"HELLO AGAIN."
```

pour ouvrir `hello.txt`, appelez `read_and_capitalize` dessus, fermez `hello.txt` et renvoyez le contenu en majuscules.

Pour éviter même d'avoir à définir une fonction nommée, vous pouvez utiliser la syntaxe `do`, qui crée une fonction anonyme à la volée :

```julia-repl
julia> open("hello.txt") do f
           uppercase(read(f, String))
       end
"HELLO AGAIN."
```

Si vous souhaitez rediriger stdout vers un fichier

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

Rediriger stdout vers un fichier peut vous aider à sauvegarder et analyser la sortie du programme, automatiser des processus et répondre aux exigences de conformité.

## A simple TCP example

Plongeons directement dans un exemple simple impliquant des sockets TCP. Cette fonctionnalité se trouve dans un package de bibliothèque standard appelé `Sockets`. Créons d'abord un serveur simple :

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

Pour ceux qui sont familiers avec l'API des sockets Unix, les noms des méthodes sembleront familiers, bien que leur utilisation soit quelque peu plus simple que l'API des sockets Unix brute. Le premier appel à [`listen`](@ref) créera un serveur attendant des connexions entrantes sur le port spécifié (2000) dans ce cas. La même fonction peut également être utilisée pour créer divers autres types de serveurs :

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

Notez que le type de retour de la dernière invocation est différent. Cela est dû au fait que ce serveur n'écoute pas sur TCP, mais plutôt sur un pipe nommé (Windows) ou un socket de domaine UNIX. Notez également que le format du pipe nommé Windows doit suivre un modèle spécifique afin que le préfixe de nom (`\\.\pipe\`) identifie de manière unique le [file type](https://docs.microsoft.com/windows/desktop/ipc/pipe-names). La différence entre TCP et les pipes nommés ou les sockets de domaine UNIX est subtile et concerne les méthodes [`accept`](@ref) et [`connect`](@ref). La méthode `4d61726b646f776e2e436f64652822222c20226163636570742229_40726566` récupère une connexion au client qui se connecte au serveur que nous venons de créer, tandis que la fonction `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` se connecte à un serveur en utilisant la méthode spécifiée. La fonction `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` prend les mêmes arguments que [`listen`](@ref), donc, en supposant que l'environnement (c'est-à-dire l'hôte, le cwd, etc.) est le même, vous devriez être en mesure de passer les mêmes arguments à `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` que vous l'avez fait pour écouter afin d'établir la connexion. Essayons cela (après avoir créé le serveur ci-dessus) :

```julia-repl
julia> connect(2000)
TCPSocket(open, 0 bytes waiting)

julia> Hello World
```

Comme prévu, nous avons vu "Hello World" imprimé. Analysons donc ce qui s'est passé en coulisses. Lorsque nous avons appelé [`connect`](@ref), nous nous connectons au serveur que nous venions de créer. Pendant ce temps, la fonction accept renvoie une connexion côté serveur au socket nouvellement créé et imprime "Hello World" pour indiquer que la connexion a réussi.

Une grande force de Julia est que, puisque l'API est exposée de manière synchrone même si l'I/O se produit en réalité de manière asynchrone, nous n'avons pas eu à nous soucier des callbacks ou même de nous assurer que le serveur puisse s'exécuter. Lorsque nous avons appelé [`connect`](@ref), la tâche actuelle a attendu que la connexion soit établie et n'a continué à s'exécuter qu'après cela. Pendant cette pause, la tâche du serveur a repris son exécution (car une demande de connexion était maintenant disponible), a accepté la connexion, a imprimé le message et a attendu le prochain client. La lecture et l'écriture fonctionnent de la même manière. Pour voir cela, considérons le serveur écho simple suivant :

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

Comme avec d'autres flux, utilisez [`close`](@ref) pour déconnecter le socket :

```julia-repl
julia> close(clientside)
```

## Resolving IP Addresses

L'une des méthodes [`connect`](@ref) qui ne suit pas les méthodes [`listen`](@ref) est `connect(host::String,port)`, qui tentera de se connecter à l'hôte donné par le paramètre `host` sur le port donné par le paramètre `port`. Cela vous permet de faire des choses comme :

```julia-repl
julia> connect("google.com", 80)
TCPSocket(RawFD(30) open, 0 bytes waiting)
```

À la base de cette fonctionnalité se trouve [`getaddrinfo`](@ref), qui effectuera la résolution d'adresse appropriée :

```julia-repl
julia> getaddrinfo("google.com")
ip"74.125.226.225"
```

## Asynchronous I/O

Toutes les opérations d'E/S exposées par [`Base.read`](@ref) et [`Base.write`](@ref) peuvent être effectuées de manière asynchrone grâce à l'utilisation de [coroutines](@ref man-tasks). Vous pouvez créer une nouvelle coroutine pour lire ou écrire dans un flux en utilisant le macro [`@async`](@ref) :

```julia-repl
julia> task = @async open("foo.txt", "w") do io
           write(io, "Hello, World!")
       end;

julia> wait(task)

julia> readlines("foo.txt")
1-element Array{String,1}:
 "Hello, World!"
```

Il est courant de se retrouver dans des situations où vous souhaitez effectuer plusieurs opérations asynchrones simultanément et attendre qu'elles soient toutes terminées. Vous pouvez utiliser la macro [`@sync`](@ref) pour faire en sorte que votre programme se bloque jusqu'à ce que toutes les coroutines qu'elle encapsule aient quitté :

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

Julia prend en charge [multicast](https://datatracker.ietf.org/doc/html/rfc1112) sur IPv4 et IPv6 en utilisant le protocole de datagramme utilisateur ([UDP](https://datatracker.ietf.org/doc/html/rfc768)) comme transport.

Contrairement au protocole de contrôle de transmission ([TCP](https://datatracker.ietf.org/doc/html/rfc793)), UDP ne fait presque aucune supposition sur les besoins de l'application. TCP fournit un contrôle de flux (il accélère et décélère pour maximiser le débit), une fiabilité (les paquets perdus ou corrompus sont automatiquement retransmis), un séquençage (les paquets sont ordonnés par le système d'exploitation avant d'être remis à l'application), une taille de segment et une configuration et une terminaison de session. UDP ne fournit pas de telles fonctionnalités.

Une utilisation courante de l'UDP est dans les applications de multicast. Le TCP est un protocole orienté connexion pour la communication entre exactement deux appareils. L'UDP peut utiliser des adresses multicast spéciales pour permettre une communication simultanée entre de nombreux appareils.

### Receiving IP Multicast Packets

Pour transmettre des données via multicast UDP, il suffit de `recv` sur le socket, et le premier paquet reçu sera retourné. Notez cependant qu'il se peut que ce ne soit pas le premier paquet que vous avez envoyé !

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

Pour transmettre des données via un multicast UDP, il suffit de `send` au socket. Notez qu'il n'est pas nécessaire qu'un expéditeur rejoigne le groupe multicast.

```julia
using Sockets
group = ip"228.5.6.7"
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv4")
close(socket)
```

### IPv6 Example

Cet exemple offre la même fonctionnalité que le programme précédent, mais utilise IPv6 comme protocole de couche réseau.

Auditeur :

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

Expéditeur :

```julia
using Sockets
group = Sockets.IPv6("ff05::5:6:7")
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv6")
close(socket)
```
