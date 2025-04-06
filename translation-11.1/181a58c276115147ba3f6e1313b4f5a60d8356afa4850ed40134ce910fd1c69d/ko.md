```
redirect_stdio(f; stdin=nothing, stderr=nothing, stdout=nothing)
```

`stdin`, `stderr`, `stdout`의 하위 집합을 리디렉션하고 `f()`를 호출한 후 각 스트림을 복원합니다.

각 스트림에 대한 가능한 값은 다음과 같습니다:

  * `nothing`은 스트림이 리디렉션되지 않아야 함을 나타냅니다.
  * `path::AbstractString`은 스트림을 `path`에 있는 파일로 리디렉션합니다.
  * `io`는 `IOStream`, `TTY`, [`Pipe`](@ref), 소켓 또는 `devnull`입니다.

# 예제

```julia-repl
julia> redirect_stdio(stdout="stdout.txt", stderr="stderr.txt") do
           print("hello stdout")
           print(stderr, "hello stderr")
       end

julia> read("stdout.txt", String)
"hello stdout"

julia> read("stderr.txt", String)
"hello stderr"
```

# 엣지 케이스

`stdout`과 `stderr`에 동일한 인수를 전달하는 것이 가능합니다:

```julia-repl
julia> redirect_stdio(stdout="log.txt", stderr="log.txt", stdin=devnull) do
    ...
end
```

그러나 동일한 파일의 두 개의 서로 다른 설명자를 전달하는 것은 지원되지 않습니다.

```julia-repl
julia> io1 = open("same/path", "w")

julia> io2 = open("same/path", "w")

julia> redirect_stdio(f, stdout=io1, stderr=io2) # 지원되지 않음
```

또한 `stdin` 인수는 `stdout` 또는 `stderr`와 동일한 설명자가 될 수 없습니다.

```julia-repl
julia> io = open(...)

julia> redirect_stdio(f, stdout=io, stdin=io) # 지원되지 않음
```

!!! compat "Julia 1.7"
    `redirect_stdio`는 Julia 1.7 이상이 필요합니다.

