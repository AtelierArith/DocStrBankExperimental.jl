```
open(filename::AbstractString, [mode::AbstractString]; lock = true) -> IOStream
```

Alternative Syntax für open, bei der ein stringbasierter Modus-Spezifizierer anstelle der fünf Booleans verwendet wird. Die Werte von `mode` entsprechen denen von `fopen(3)` oder Perl `open` und sind äquivalent zu den folgenden booleschen Gruppen:

| Modus | Beschreibung                            | Schlüsselwörter                |
|:----- |:--------------------------------------- |:------------------------------ |
| `r`   | lesen                                   | keine                          |
| `w`   | schreiben, erstellen, truncieren        | `write = true`                 |
| `a`   | schreiben, erstellen, anhängen          | `append = true`                |
| `r+`  | lesen, schreiben                        | `read = true, write = true`    |
| `w+`  | lesen, schreiben, erstellen, truncieren | `truncate = true, read = true` |
| `a+`  | lesen, schreiben, erstellen, anhängen   | `append = true, read = true`   |

Das Schlüsselwortargument `lock` steuert, ob Operationen für einen sicheren Multi-Thread-Zugriff gesperrt werden.

# Beispiele

```jldoctest
julia> io = open("myfile.txt", "w");

julia> write(io, "Hello world!");

julia> close(io);

julia> io = open("myfile.txt", "r");

julia> read(io, String)
"Hello world!"

julia> write(io, "This file is read only")
ERROR: ArgumentError: write failed, IOStream is not writeable
[...]

julia> close(io)

julia> io = open("myfile.txt", "a");

julia> write(io, "This stream is not read only")
28

julia> close(io)

julia> rm("myfile.txt")
```

!!! compat "Julia 1.5"
    Das `lock`-Argument ist seit Julia 1.5 verfügbar.

