```
redirect_stdio(f; stdin=nothing, stderr=nothing, stdout=nothing)
```

Redirige un sous-ensemble des flux `stdin`, `stderr`, `stdout`, appelle `f()` et restaure chaque flux.

Les valeurs possibles pour chaque flux sont :

  * `nothing` indiquant que le flux ne doit pas être redirigé.
  * `path::AbstractString` redirigeant le flux vers le fichier à `path`.
  * `io` un `IOStream`, `TTY`, [`Pipe`](@ref), socket, ou `devnull`.

# Exemples

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

# Cas particuliers

Il est possible de passer le même argument à `stdout` et `stderr` :

```julia-repl
julia> redirect_stdio(stdout="log.txt", stderr="log.txt", stdin=devnull) do
    ...
end
```

Cependant, il n'est pas supporté de passer deux descripteurs distincts du même fichier.

```julia-repl
julia> io1 = open("same/path", "w")

julia> io2 = open("same/path", "w")

julia> redirect_stdio(f, stdout=io1, stderr=io2) # non supporté
```

De plus, l'argument `stdin` ne peut pas être le même descripteur que `stdout` ou `stderr`.

```julia-repl
julia> io = open(...)

julia> redirect_stdio(f, stdout=io, stdin=io) # non supporté
```

!!! compat "Julia 1.7"
    `redirect_stdio` nécessite Julia 1.7 ou une version ultérieure.

