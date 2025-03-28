```
redirect_stdio(f; stdin=nothing, stderr=nothing, stdout=nothing)
```

Leitet eine Teilmenge der Streams `stdin`, `stderr`, `stdout um, ruft`f()` auf und stellt jeden Stream wieder her.

Mögliche Werte für jeden Stream sind:

  * `nothing`, was bedeutet, dass der Stream nicht umgeleitet werden soll.
  * `path::AbstractString`, der den Stream auf die Datei unter `path` umleitet.
  * `io`, ein `IOStream`, `TTY`, [`Pipe`](@ref), Socket oder `devnull`.

# Beispiele

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

# Randfälle

Es ist möglich, dass dasselbe Argument an `stdout` und `stderr` übergeben wird:

```julia-repl
julia> redirect_stdio(stdout="log.txt", stderr="log.txt", stdin=devnull) do
    ...
end
```

Es wird jedoch nicht unterstützt, zwei unterschiedliche Deskriptoren derselben Datei zu übergeben.

```julia-repl
julia> io1 = open("same/path", "w")

julia> io2 = open("same/path", "w")

julia> redirect_stdio(f, stdout=io1, stderr=io2) # nicht unterstützt
```

Außerdem darf das Argument `stdin` nicht derselbe Deskriptor wie `stdout` oder `stderr` sein.

```julia-repl
julia> io = open(...)

julia> redirect_stdio(f, stdout=io, stdin=io) # nicht unterstützt
```

!!! compat "Julia 1.7"
    `redirect_stdio` erfordert Julia 1.7 oder höher.

