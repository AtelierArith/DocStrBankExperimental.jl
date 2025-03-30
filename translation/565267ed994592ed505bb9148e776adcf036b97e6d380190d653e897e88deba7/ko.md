# Networking and Streams

줄리아는 터미널, 파이프 및 TCP 소켓과 같은 스트리밍 I/O 객체를 처리하기 위한 풍부한 인터페이스를 제공합니다. 이러한 객체는 데이터가 스트림처럼 전송되고 수신될 수 있도록 하며, 이는 데이터가 사용 가능해짐에 따라 순차적으로 처리된다는 것을 의미합니다. 이 인터페이스는 시스템 수준에서 비동기적이지만 프로그래머에게는 동기적인 방식으로 제공됩니다. 이는 줄리아의 협동 스레딩([coroutine](@ref man-tasks)) 기능을 많이 활용하여 달성됩니다.

## Basic Stream I/O

모든 Julia 스트림은 최소한 [`read`](@ref) 및 [`write`](@ref) 메서드를 노출하며, 이 메서드는 스트림을 첫 번째 인수로 사용합니다. 예:

```julia-repl
julia> write(stdout, "Hello World");  # suppress return value 11 with ;
Hello World
julia> read(stdin, Char)

'\n': ASCII/Unicode U+000a (category Cc: Other, control)
```

[`write`](@ref)는 [`stdout`](@ref)에 쓰여진 `"Hello World"`의 바이트 수인 11을 반환합니다. 그러나 이 반환 값은 `;`로 억제됩니다.

여기에서 Enter가 다시 눌려서 Julia가 줄 바꿈을 읽게 되었습니다. 이제 이 예제에서 볼 수 있듯이, [`write`](@ref)는 두 번째 인수로 쓸 데이터를 가져오고, 반면 [`read`](@ref)는 두 번째 인수로 읽을 데이터의 유형을 가져옵니다.

예를 들어, 간단한 바이트 배열을 읽기 위해서는 다음과 같이 할 수 있습니다:

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

그러나 이것이 다소 번거롭기 때문에 여러 가지 편의 메서드가 제공됩니다. 예를 들어, 우리는 위의 내용을 다음과 같이 작성할 수 있습니다:

```julia-repl
julia> read(stdin, 4)
abcd
4-element Array{UInt8,1}:
 0x61
 0x62
 0x63
 0x64
```

또는 전체 줄을 읽고 싶었다면:

```julia-repl
julia> readline(stdin)
abcd
"abcd"
```

터미널 설정에 따라 TTY("teletype terminal")가 라인 버퍼링될 수 있으며, 이로 인해 `stdin` 데이터가 Julia로 전송되기 전에 추가적인 엔터가 필요할 수 있습니다. TTY에서 명령줄로 Julia를 실행할 때, 출력은 기본적으로 콘솔로 전송되며, 표준 입력은 키보드에서 읽습니다.

[`stdin`](@ref)의 모든 줄을 읽으려면 [`eachline`](@ref)를 사용할 수 있습니다:

```julia
for line in eachline(stdin)
    print("Found $line")
end
```

또는 [`read`](@ref)를 문자 단위로 읽고 싶다면:

```julia
while !eof(stdin)
    x = read(stdin, Char)
    println("Found: $x")
end
```

## Text I/O

[`write`](@ref) 메서드는 이진 스트림에서 작동합니다. 특히, 값은 어떤 표준 텍스트 표현으로 변환되지 않고 그대로 기록됩니다:

```jldoctest
julia> write(stdout, 0x61);  # suppress return value 1 with ;
a
```

`a`는 [`stdout`](@ref) 함수에 의해 [`write`](@ref)에 기록되며, 반환된 값은 `1`입니다 (왜냐하면 `0x61`은 한 바이트이기 때문입니다).

텍스트 I/O의 경우, 필요에 따라 [`print`](@ref) 또는 [`show`](@ref) 방법을 사용하세요 (이 두 방법의 차이에 대한 자세한 논의는 문서를 참조하세요):

```jldoctest
julia> print(stdout, 0x61)
97
```

[Custom pretty-printing](@ref man-custom-pretty-printing)에 대한 자세한 내용은 사용자 정의 유형에 대한 표시 방법을 구현하는 방법을 참조하십시오.

## IO Output Contextual Properties

때때로 IO 출력은 show 메서드에 컨텍스트 정보를 전달할 수 있는 기능으로 이점을 얻을 수 있습니다. [`IOContext`](@ref) 객체는 IO 객체와 임의의 메타데이터를 연결하는 프레임워크를 제공합니다. 예를 들어, `:compact => true`는 호출된 show 메서드가 더 짧은 출력을 인쇄해야 한다는 힌트 매개변수를 IO 객체에 추가합니다(해당되는 경우). 일반적인 속성 목록은 `4d61726b646f776e2e436f64652822222c2022494f436f6e746578742229_40726566` 문서를 참조하십시오.

## Working with Files

`write(filename::String, content)` 메서드를 사용하여 파일에 내용을 쓸 수 있습니다:

```julia-repl
julia> write("hello.txt", "Hello, World!")
13
```

*(`13`는 기록된 바이트 수입니다.)*

파일의 내용을 읽으려면 `read(filename::String)` 메서드를 사용하거나, `read(filename::String, String)`를 사용하여 내용을 문자열로 읽을 수 있습니다:

```julia-repl
julia> read("hello.txt", String)
"Hello, World!"
```

### Advanced: streaming files

`read` 및 `write` 메서드는 파일 내용을 읽고 쓸 수 있게 해줍니다. 많은 다른 환경과 마찬가지로, Julia에도 [`open`](@ref) 함수가 있으며, 이 함수는 파일 이름을 받아 [`IOStream`](@ref) 객체를 반환하여 파일에서 읽고 쓸 수 있도록 합니다. 예를 들어, `hello.txt`라는 파일이 있고 그 내용이 `Hello, World!`인 경우:

```julia-repl
julia> f = open("hello.txt")
IOStream(<file hello.txt>)

julia> readlines(f)
1-element Array{String,1}:
 "Hello, World!"
```

파일에 쓰고 싶다면, 쓰기(`"w"`) 플래그로 열 수 있습니다:

```julia-repl
julia> f = open("hello.txt","w")
IOStream(<file hello.txt>)

julia> write(f,"Hello again.")
12
```

`hello.txt`의 내용을 이 시점에서 살펴보면, 파일이 비어 있다는 것을 알 수 있습니다. 실제로 디스크에 아무것도 기록되지 않았습니다. 이는 `IOStream`이 닫히기 전에 쓰기가 실제로 디스크에 플러시되어야 하기 때문입니다.

```julia-repl
julia> close(f)
```

`hello.txt`를 다시 살펴보면 그 내용이 변경되었음을 알 수 있습니다.

파일을 열고, 그 내용에 대해 작업을 수행한 다음 다시 닫는 것은 매우 일반적인 패턴입니다. 이를 더 쉽게 만들기 위해, 첫 번째 인수로 함수를, 두 번째 인수로 파일 이름을 받는 [`open`](@ref)의 또 다른 호출이 존재합니다. 이 호출은 파일을 열고, 파일을 인수로 하여 함수를 호출한 다음 다시 닫습니다. 예를 들어, 주어진 함수:

```julia
function read_and_capitalize(f::IOStream)
    return uppercase(read(f, String))
end
```

당신은 호출할 수 있습니다:

```julia-repl
julia> open(read_and_capitalize, "hello.txt")
"HELLO AGAIN."
```

`hello.txt`를 열고, `read_and_capitalize`를 호출한 후, `hello.txt`를 닫고 대문자로 변환된 내용을 반환합니다.

이름이 있는 함수를 정의할 필요조차 없도록 `do` 구문을 사용할 수 있습니다. 이 구문은 즉석에서 익명 함수를 생성합니다:

```julia-repl
julia> open("hello.txt") do f
           uppercase(read(f, String))
       end
"HELLO AGAIN."
```

표준 출력을 파일로 리디렉션하려면

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

표준 출력을 파일로 리디렉션하면 프로그램 출력을 저장하고 분석하며, 프로세스를 자동화하고, 규정 준수 요구 사항을 충족하는 데 도움이 될 수 있습니다.

## A simple TCP example

간단한 TCP 소켓을 사용하는 예제로 바로 시작해 보겠습니다. 이 기능은 `Sockets`라는 표준 라이브러리 패키지에 포함되어 있습니다. 먼저 간단한 서버를 만들어 보겠습니다:

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

Unix 소켓 API에 익숙한 사람들에게는 메서드 이름이 친숙하게 느껴질 것이지만, 그 사용법은 원시 Unix 소켓 API보다 다소 간단합니다. [`listen`](@ref)에 대한 첫 번째 호출은 이 경우 지정된 포트(2000)에서 들어오는 연결을 기다리는 서버를 생성합니다. 동일한 함수를 사용하여 다양한 다른 종류의 서버를 생성할 수도 있습니다:

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

마지막 호출의 반환 유형이 다르다는 점에 유의하세요. 이는 이 서버가 TCP에서 수신하지 않고, 대신 명명된 파이프(Windows) 또는 UNIX 도메인 소켓에서 수신하기 때문입니다. 또한 Windows 명명된 파이프 형식은 특정 패턴이어야 하며, 이름 접두사(`\\.\pipe\`)가 [file type](https://docs.microsoft.com/windows/desktop/ipc/pipe-names)를 고유하게 식별해야 합니다. TCP와 명명된 파이프 또는 UNIX 도메인 소켓의 차이는 미세하며, [`accept`](@ref) 및 [`connect`](@ref) 메서드와 관련이 있습니다. `4d61726b646f776e2e436f64652822222c20226163636570742229_40726566` 메서드는 우리가 방금 생성한 서버에 연결하는 클라이언트에 대한 연결을 검색하는 반면, `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` 함수는 지정된 메서드를 사용하여 서버에 연결합니다. `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` 함수는 [`listen`](@ref)와 동일한 인수를 사용하므로, 환경(즉, 호스트, cwd 등)이 동일하다고 가정하면 `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566`에 연결을 설정하기 위해 사용한 것과 동일한 인수를 전달할 수 있어야 합니다. 그러니 위에서 서버를 생성한 후 이를 시도해 보겠습니다.

```julia-repl
julia> connect(2000)
TCPSocket(open, 0 bytes waiting)

julia> Hello World
```

예상대로 "Hello World"가 출력되는 것을 보았습니다. 이제 실제로 무슨 일이 있었는지 분석해 보겠습니다. [`connect`](@ref)를 호출했을 때, 우리는 방금 생성한 서버에 연결하게 됩니다. 그동안 accept 함수는 새로 생성된 소켓에 대한 서버 측 연결을 반환하고, 연결이 성공했음을 나타내기 위해 "Hello World"를 출력합니다.

줄리아의 큰 장점 중 하나는 API가 비동기적으로 I/O가 실제로 발생하고 있음에도 불구하고 동기적으로 노출된다는 점입니다. 덕분에 우리는 콜백이나 서버가 실행되도록 하는 것에 대해 걱정할 필요가 없었습니다. [`connect`](@ref)를 호출했을 때 현재 작업은 연결이 설정될 때까지 기다렸고, 그 작업이 완료된 후에만 계속 실행되었습니다. 이 대기 시간 동안 서버 작업은 실행을 재개하였고(이제 연결 요청이 가능해졌기 때문에), 연결을 수락하고 메시지를 출력한 후 다음 클라이언트를 기다렸습니다. 읽기와 쓰기는 같은 방식으로 작동합니다. 이를 보기 위해 다음의 간단한 에코 서버를 고려해 보십시오:

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

다른 스트림과 마찬가지로, 소켓을 끊으려면 [`close`](@ref)를 사용하세요:

```julia-repl
julia> close(clientside)
```

## Resolving IP Addresses

[`connect`](@ref) 메서드 중 하나로, [`listen`](@ref) 메서드를 따르지 않는 것은 `connect(host::String,port)`입니다. 이 메서드는 `host` 매개변수로 주어진 호스트에 `port` 매개변수로 주어진 포트에서 연결을 시도합니다. 이를 통해 다음과 같은 작업을 수행할 수 있습니다:

```julia-repl
julia> connect("google.com", 80)
TCPSocket(RawFD(30) open, 0 bytes waiting)
```

이 기능의 기본은 [`getaddrinfo`](@ref)이며, 이는 적절한 주소 해석을 수행합니다:

```julia-repl
julia> getaddrinfo("google.com")
ip"74.125.226.225"
```

## Asynchronous I/O

All I/O operations exposed by [`Base.read`](@ref) and [`Base.write`](@ref) can be performed asynchronously through the use of [coroutines](@ref man-tasks). You can create a new coroutine to read from or write to a stream using the [`@async`](@ref) macro:

```julia-repl
julia> task = @async open("foo.txt", "w") do io
           write(io, "Hello, World!")
       end;

julia> wait(task)

julia> readlines("foo.txt")
1-element Array{String,1}:
 "Hello, World!"
```

여러 비동기 작업을 동시에 수행하고 모든 작업이 완료될 때까지 기다려야 하는 상황에 자주 직면하게 됩니다. [`@sync`](@ref) 매크로를 사용하여 감싸고 있는 모든 코루틴이 종료될 때까지 프로그램이 차단되도록 할 수 있습니다:

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

줄리아는 [multicast](https://datatracker.ietf.org/doc/html/rfc1112)를 IPv4 및 IPv6에서 사용자 데이터그램 프로토콜([UDP](https://datatracker.ietf.org/doc/html/rfc768))을 전송 수단으로 지원합니다.

전송 제어 프로토콜([TCP](https://datatracker.ietf.org/doc/html/rfc793))과 달리, UDP는 애플리케이션의 필요에 대해 거의 아무런 가정을 하지 않습니다. TCP는 흐름 제어(최대 처리량을 극대화하기 위해 가속 및 감속), 신뢰성(손실되거나 손상된 패킷이 자동으로 재전송됨), 순서 지정(패킷이 애플리케이션에 전달되기 전에 운영 체제에 의해 정렬됨), 세그먼트 크기, 세션 설정 및 종료를 제공합니다. UDP는 이러한 기능을 제공하지 않습니다.

UDP의 일반적인 용도는 멀티캐스트 애플리케이션입니다. TCP는 정확히 두 장치 간의 통신을 위한 상태 유지 프로토콜입니다. UDP는 특별한 멀티캐스트 주소를 사용하여 여러 장치 간의 동시 통신을 허용할 수 있습니다.

### Receiving IP Multicast Packets

UDP 멀티캐스트를 통해 데이터를 전송하려면 소켓에서 단순히 `recv`를 호출하면 됩니다. 수신된 첫 번째 패킷이 반환됩니다. 그러나 이것이 당신이 보낸 첫 번째 패킷이 아닐 수도 있다는 점에 유의하세요!

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

UDP 멀티캐스트를 통해 데이터를 전송하려면, 단순히 소켓에 `send`하면 됩니다. 송신자가 멀티캐스트 그룹에 가입할 필요는 없다는 점에 유의하세요.

```julia
using Sockets
group = ip"228.5.6.7"
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv4")
close(socket)
```

### IPv6 Example

이 예제는 이전 프로그램과 동일한 기능을 제공하지만, 네트워크 계층 프로토콜로 IPv6를 사용합니다.

청취자:

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

발신자:

```julia
using Sockets
group = Sockets.IPv6("ff05::5:6:7")
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv6")
close(socket)
```
