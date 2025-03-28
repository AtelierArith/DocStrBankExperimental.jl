```
redirect_stdio(;stdin=stdin, stderr=stderr, stdout=stdout)
```

Leitet eine Teilmenge der Streams `stdin`, `stderr`, `stdout` um. Jedes Argument muss ein `IOStream`, `TTY`, [`Pipe`](@ref), Socket oder `devnull` sein.

!!! compat "Julia 1.7"
    `redirect_stdio` erfordert Julia 1.7 oder höher.

