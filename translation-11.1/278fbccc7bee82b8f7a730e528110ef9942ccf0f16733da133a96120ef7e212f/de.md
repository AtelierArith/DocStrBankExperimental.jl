```
mv(src::AbstractString, dst::AbstractString; force::Bool=false)
```

Bewege die Datei, den Link oder das Verzeichnis von `src` nach `dst`. `force=true` entfernt zuerst ein vorhandenes `dst`. Gibt `dst` zurück.

# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> write("hello.txt", "world");

julia> mv("hello.txt", "goodbye.txt")
"goodbye.txt"

julia> "hello.txt" in readdir()
false

julia> readline("goodbye.txt")
"world"

julia> write("hello.txt", "world2");

julia> mv("hello.txt", "goodbye.txt")
ERROR: ArgumentError: 'goodbye.txt' existiert. `force=true` ist erforderlich, um 'goodbye.txt' vor dem Verschieben zu entfernen.
Stacktrace:
 [1] #checkfor_mv_cp_cptree#10(::Bool, ::Function, ::String, ::String, ::String) at ./file.jl:293
[...]

julia> mv("hello.txt", "goodbye.txt", force=true)
"goodbye.txt"

julia> rm("goodbye.txt");

```
