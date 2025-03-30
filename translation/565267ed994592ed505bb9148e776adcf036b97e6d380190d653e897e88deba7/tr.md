# Networking and Streams

Julia, terminal, borular, boru hatları ve TCP soketleri gibi akış I/O nesneleriyle başa çıkmak için zengin bir arayüz sağlar. Bu nesneler, verilerin akış benzeri bir şekilde gönderilip alınmasına olanak tanır; bu, verilerin mevcut oldukça sıralı bir şekilde işlendiği anlamına gelir. Bu arayüz, sistem düzeyinde asenkron olmasına rağmen, programcıya senkron bir şekilde sunulmaktadır. Bu, Julia'nın işbirlikçi iş parçacığı ([coroutine](@ref man-tasks)) işlevselliğinden yoğun bir şekilde yararlanarak başarılmaktadır.

## Basic Stream I/O

Tüm Julia akışları en az bir [`read`](@ref) ve bir [`write`](@ref) yöntemi sunar, akışı ilk argüman olarak alır, örneğin:

```julia-repl
julia> write(stdout, "Hello World");  # suppress return value 11 with ;
Hello World
julia> read(stdin, Char)

'\n': ASCII/Unicode U+000a (category Cc: Other, control)
```

Not edin ki [`write`](@ref) `11` döndürür, bu `"Hello World"` içindeki bayt sayısıdır ve [`stdout`](@ref)'ye yazılmıştır, ancak bu dönüş değeri `;` ile bastırılmıştır.

Burada Enter tuşuna tekrar basıldı, böylece Julia yeni satırı okuyabilecekti. Şimdi, bu örnekten görebileceğiniz gibi, [`write`](@ref) yazılacak veriyi ikinci argüman olarak alırken, [`read`](@ref) okunacak verinin türünü ikinci argüman olarak alır.

Örneğin, basit bir bayt dizisini okumak için şunları yapabiliriz:

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

Ancak, bu biraz zahmetli olduğu için, birkaç pratik yöntem sağlanmıştır. Örneğin, yukarıdakini şöyle yazabilirdik:

```julia-repl
julia> read(stdin, 4)
abcd
4-element Array{UInt8,1}:
 0x61
 0x62
 0x63
 0x64
```

ya da tüm satırı okumak istemiş olsaydık:

```julia-repl
julia> readline(stdin)
abcd
"abcd"
```

Not edin ki terminal ayarlarınıza bağlı olarak, TTY'niz ("teletype terminal") satır tamponlu olabilir ve bu nedenle `stdin` verisinin Julia'ya gönderilmeden önce ek bir enter tuşuna basılması gerekebilir. TTY'de komut satırından Julia çalıştırıldığında, çıktı varsayılan olarak konsola gönderilir ve standart girdi klavyeden okunur.

Her satırı okumak için [`stdin`](@ref) kullanabilirsiniz: [`eachline`](@ref):

```julia
for line in eachline(stdin)
    print("Found $line")
end
```

veya [`read`](@ref) karakter bazında okumak isterseniz:

```julia
while !eof(stdin)
    x = read(stdin, Char)
    println("Found: $x")
end
```

## Text I/O

Not edin ki [`write`](@ref) yukarıda bahsedilen yöntem ikili akışlar üzerinde çalışır. Özellikle, değerler herhangi bir kanonik metin temsilinde dönüştürülmez, olduğu gibi yazılır:

```jldoctest
julia> write(stdout, 0x61);  # suppress return value 1 with ;
a
```

Not edin ki `a`, [`stdout`](@ref) tarafından [`write`](@ref) fonksiyonu ile yazılır ve döndürülen değer `1`'dir (çünkü `0x61` bir bayttır).

Metin girişi/çıkışı için ihtiyaçlarınıza bağlı olarak [`print`](@ref) veya [`show`](@ref) yöntemlerini kullanın (bu iki yöntem arasındaki farkın ayrıntılı tartışması için belgeleri inceleyin):

```jldoctest
julia> print(stdout, 0x61)
97
```

[Custom pretty-printing](@ref man-custom-pretty-printing) hakkında özel türler için görüntüleme yöntemlerini nasıl uygulayacağınıza dair daha fazla bilgi için bakın.

## IO Output Contextual Properties

Bazen IO çıktısı, gösterim yöntemlerine bağlamsal bilgi geçirme yeteneğinden faydalanabilir. [`IOContext`](@ref) nesnesi, bir IO nesnesi ile keyfi meta verileri ilişkilendirmek için bu çerçeveyi sağlar. Örneğin, `:compact => true` IO nesnesine, çağrılan gösterim yönteminin daha kısa bir çıktı vermesi gerektiğine dair bir ipucu ekler (uygulanabilir olduğunda). Yaygın özelliklerin bir listesi için `4d61726b646f776e2e436f64652822222c2022494f436f6e746578742229_40726566` belgelerine bakın.

## Working with Files

Bir dosyaya içerik yazmak için `write(filename::String, content)` yöntemini kullanabilirsiniz:

```julia-repl
julia> write("hello.txt", "Hello, World!")
13
```

*(`13` yazılan bayt sayısıdır.)*

Bir dosyanın içeriğini `read(filename::String)` yöntemiyle okuyabilir veya içeriği bir dize olarak almak için `read(filename::String, String)` yöntemini kullanabilirsiniz:

```julia-repl
julia> read("hello.txt", String)
"Hello, World!"
```

### Advanced: streaming files

`read` ve `write` yöntemleri yukarıda dosya içeriklerini okumanıza ve yazmanıza olanak tanır. Diğer birçok ortamda olduğu gibi, Julia'nın da bir [`open`](@ref) fonksiyonu vardır; bu fonksiyon bir dosya adı alır ve dosyadan şeyler okumak ve yazmak için kullanabileceğiniz bir [`IOStream`](@ref) nesnesi döndürür. Örneğin, `Hello, World!` içeriğine sahip `hello.txt` adında bir dosyamız varsa:

```julia-repl
julia> f = open("hello.txt")
IOStream(<file hello.txt>)

julia> readlines(f)
1-element Array{String,1}:
 "Hello, World!"
```

Bir dosyaya yazmak istiyorsanız, onu yazma (`"w"`) bayrağı ile açabilirsiniz:

```julia-repl
julia> f = open("hello.txt","w")
IOStream(<file hello.txt>)

julia> write(f,"Hello again.")
12
```

Eğer şu anda `hello.txt` dosyasının içeriğini incelerseniz, boş olduğunu göreceksiniz; aslında diske hiçbir şey yazılmamıştır. Bunun nedeni, yazmanın gerçekten diske aktarılmadan önce `IOStream`'in kapatılması gerektiğidir:

```julia-repl
julia> close(f)
```

`hello.txt` dosyasını tekrar incelemek, içeriğinin değiştiğini gösterecektir.

Bir dosya açmak, içeriği üzerinde bir şeyler yapmak ve ardından tekrar kapatmak çok yaygın bir kalıptır. Bunu daha kolay hale getirmek için, ilk argüman olarak bir fonksiyon ve ikinci argüman olarak dosya adı alan [`open`](@ref) adlı başka bir çağrı vardır. Bu, dosyayı açar, dosyayı bir argüman olarak fonksiyona çağırır ve ardından tekrar kapatır. Örneğin, bir fonksiyon verildiğinde:

```julia
function read_and_capitalize(f::IOStream)
    return uppercase(read(f, String))
end
```

Bunu arayabilirsiniz:

```julia-repl
julia> open(read_and_capitalize, "hello.txt")
"HELLO AGAIN."
```

`hello.txt`'ı açmak için, üzerinde `read_and_capitalize` çağrısı yapın, `hello.txt`'ı kapatın ve büyük harflerle yazılmış içeriği döndürün.

Tanımlı bir fonksiyonu tanımlamak zorunda kalmamak için, anında anonim bir fonksiyon oluşturan `do` sözdizimini kullanabilirsiniz:

```julia-repl
julia> open("hello.txt") do f
           uppercase(read(f, String))
       end
"HELLO AGAIN."
```

Eğer stdout'u bir dosyaya yönlendirmek istiyorsanız

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

stdout'u bir dosyaya yönlendirmek, program çıktısını kaydetmenize ve analiz etmenize, süreçleri otomatikleştirmenize ve uyumluluk gereksinimlerini karşılamanıza yardımcı olabilir.

## A simple TCP example

Hadi hemen TCP soketleri ile ilgili basit bir örneğe geçelim. Bu işlevsellik, `Sockets` adlı standart bir kütüphane paketinde bulunmaktadır. Öncelikle basit bir sunucu oluşturalım:

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

Unix soket API'sine aşina olanlar için, yöntem adları tanıdık gelecektir, ancak kullanımları ham Unix soket API'sinden biraz daha basittir. [`listen`](@ref) çağrısı, bu durumda belirtilen portta (2000) gelen bağlantıları bekleyen bir sunucu oluşturacaktır. Aynı işlev, çeşitli diğer sunucu türlerini oluşturmak için de kullanılabilir:

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

Sonuç türünün son çağrısının farklı olduğunu unutmayın. Bunun nedeni, bu sunucunun TCP dinlememesi, bunun yerine bir adlandırılmış boru (Windows) veya UNIX alan soketi üzerinde dinlemesidir. Ayrıca, Windows adlandırılmış boru formatının, ad öneki (`\\.\pipe\`) ile birlikte, [file type](https://docs.microsoft.com/windows/desktop/ipc/pipe-names)'ü benzersiz bir şekilde tanımlayacak belirli bir desene sahip olması gerektiğini unutmayın. TCP ile adlandırılmış borular veya UNIX alan soketleri arasındaki fark ince bir ayrıntıdır ve [`accept`](@ref) ve [`connect`](@ref) yöntemleriyle ilgilidir. `4d61726b646f776e2e436f64652822222c20226163636570742229_40726566` yöntemi, yeni oluşturduğumuz sunucuya bağlanan istemciye bir bağlantı alırken, `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` fonksiyonu belirtilen yöntemi kullanarak bir sunucuya bağlanır. `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` fonksiyonu, [`listen`](@ref) ile aynı argümanları alır, bu nedenle ortamın (yani, ana bilgisayar, cwd, vb.) aynı olduğunu varsayarsak, `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566`'ya, bağlantıyı kurmak için dinlemeye verdiğiniz aynı argümanları geçebilmelisiniz. O halde bunu deneyelim (yukarıda sunucuyu oluşturduktan sonra):

```julia-repl
julia> connect(2000)
TCPSocket(open, 0 bytes waiting)

julia> Hello World
```

Beklendiği gibi "Hello World" yazdırıldığını gördük. Şimdi, sahne arkasında neler olduğunu gerçekten analiz edelim. [`connect`](@ref) çağrıldığında, yeni oluşturduğumuz sunucuya bağlanıyoruz. Bu arada, accept fonksiyonu yeni oluşturulan sokete sunucu tarafında bir bağlantı döndürür ve bağlantının başarılı olduğunu belirtmek için "Hello World" yazdırır.

Julia'nın büyük bir gücü, API'nin senkron olarak açığa çıkarılmasıdır; bu, I/O'nun aslında asenkron gerçekleşmesine rağmen, geri çağırmalar veya sunucunun çalıştığından emin olma konusunda endişelenmemiz gerekmediği anlamına gelir. [`connect`](@ref) çağrıldığında, mevcut görev bağlantının kurulmasını bekledi ve bu tamamlandıktan sonra yalnızca yürütmeye devam etti. Bu duraklama sırasında, sunucu görevi yürütmeye devam etti (çünkü artık bir bağlantı isteği mevcuttu), bağlantıyı kabul etti, mesajı yazdırdı ve bir sonraki istemciyi bekledi. Okuma ve yazma aynı şekilde çalışır. Bunu görmek için, aşağıdaki basit yankı sunucusunu düşünün:

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

Diğer akışlarda olduğu gibi, soketi kapatmak için [`close`](@ref) kullanın:

```julia-repl
julia> close(clientside)
```

## Resolving IP Addresses

[`connect`](@ref) yöntemlerinden biri, [`listen`](@ref) yöntemlerini takip etmeyen `connect(host::String,port)` yöntemidir. Bu yöntem, `host` parametresiyle verilen ana bilgisayara, `port` parametresiyle verilen port üzerinden bağlanmaya çalışır. Size şunları yapma imkanı tanır:

```julia-repl
julia> connect("google.com", 80)
TCPSocket(RawFD(30) open, 0 bytes waiting)
```

Bu işlevselliğin temelinde [`getaddrinfo`](@ref) bulunmaktadır; bu, uygun adres çözümlemesini gerçekleştirecektir:

```julia-repl
julia> getaddrinfo("google.com")
ip"74.125.226.225"
```

## Asynchronous I/O

Tüm I/O işlemleri [`Base.read`](@ref) ve [`Base.write`](@ref) tarafından serbestçe gerçekleştirilebilir ve [coroutines](@ref man-tasks) kullanılarak asenkron olarak yapılabilir. Bir akıştan okumak veya yazmak için yeni bir coroutine oluşturmak üzere [`@async`](@ref) makrosunu kullanabilirsiniz:

```julia-repl
julia> task = @async open("foo.txt", "w") do io
           write(io, "Hello, World!")
       end;

julia> wait(task)

julia> readlines("foo.txt")
1-element Array{String,1}:
 "Hello, World!"
```

Birden fazla asenkron işlemi eşzamanlı olarak gerçekleştirmek ve hepsinin tamamlanmasını beklemek istediğiniz durumlarla karşılaşmak yaygındır. Programınızın, etrafında sarılı tüm korotinler çıkana kadar engellenmesini sağlamak için [`@sync`](@ref) makrosunu kullanabilirsiniz:

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

Julia, [multicast](https://datatracker.ietf.org/doc/html/rfc1112) IPv4 ve IPv6'yı Kullanıcı Datagram Protokolü ([UDP](https://datatracker.ietf.org/doc/html/rfc768)) üzerinden taşımaktadır.

Transmission Control Protocol ([TCP](https://datatracker.ietf.org/doc/html/rfc793)) ile karşılaştırıldığında, UDP uygulamanın ihtiyaçları hakkında neredeyse hiç varsayımda bulunmaz. TCP akış kontrolü sağlar (verimliliği maksimize etmek için hızlanır ve yavaşlar), güvenilirlik (kayıp veya bozuk paketler otomatik olarak yeniden iletilir), sıralama (paketler, uygulamaya verilmeden önce işletim sistemi tarafından sıralanır), segment boyutu ve oturum kurma ve kapatma işlemleri sunar. UDP bu tür özellikler sunmaz.

UDP'nin yaygın bir kullanımı çoklu yayın uygulamalarıdır. TCP, tam olarak iki cihaz arasında iletişim için durum bilgisi olan bir protokoldür. UDP, birçok cihaz arasında eşzamanlı iletişimi sağlamak için özel çoklu yayın adreslerini kullanabilir.

### Receiving IP Multicast Packets

UDP çoklu yayını üzerinden veri iletmek için, soket üzerinde basitçe `recv` yapın ve alınan ilk paket döndürülecektir. Ancak, bu paketin gönderdiğiniz ilk paket olmayabileceğini unutmayın!

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

UDP çoklu yayını üzerinden veri iletmek için, sadece `send` komutunu sokete gönderin. Gönderenin çoklu yayın grubuna katılması gerekmediğine dikkat edin.

```julia
using Sockets
group = ip"228.5.6.7"
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv4")
close(socket)
```

### IPv6 Example

Bu örnek, önceki programla aynı işlevselliği sağlar, ancak ağ katmanı protokolü olarak IPv6 kullanır.

Dinleyici:

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

Gönderen:

```julia
using Sockets
group = Sockets.IPv6("ff05::5:6:7")
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv6")
close(socket)
```
