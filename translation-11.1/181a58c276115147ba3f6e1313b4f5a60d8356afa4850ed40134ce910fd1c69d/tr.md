```
redirect_stdio(f; stdin=nothing, stderr=nothing, stdout=nothing)
```

`stdin`, `stderr`, `stdout` akışlarının bir alt kümesini yönlendirin, `f()` çağırın ve her akışı geri yükleyin.

Her akış için olası değerler:

  * `nothing` akışın yönlendirilmemesi gerektiğini belirtir.
  * `path::AbstractString` akışı `path`'teki dosyaya yönlendirir.
  * `io` bir `IOStream`, `TTY`, [`Pipe`](@ref), soket veya `devnull`.

# Örnekler

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

# Kenar durumları

`stdout` ve `stderr` için aynı argümanı geçmek mümkündür:

```julia-repl
julia> redirect_stdio(stdout="log.txt", stderr="log.txt", stdin=devnull) do
    ...
end
```

Ancak, aynı dosyanın iki farklı tanımlayıcısını geçmek desteklenmez.

```julia-repl
julia> io1 = open("same/path", "w")

julia> io2 = open("same/path", "w")

julia> redirect_stdio(f, stdout=io1, stderr=io2) # desteklenmiyor
```

Ayrıca `stdin` argümanı `stdout` veya `stderr` ile aynı tanımlayıcı olamaz.

```julia-repl
julia> io = open(...)

julia> redirect_stdio(f, stdout=io, stdin=io) # desteklenmiyor
```

!!! compat "Julia 1.7"
    `redirect_stdio` Julia 1.7 veya daha yenisini gerektirir.

