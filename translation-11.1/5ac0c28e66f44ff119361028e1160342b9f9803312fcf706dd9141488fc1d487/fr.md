```
countlines(io::IO; eol::AbstractChar = '\n')
countlines(filename::AbstractString; eol::AbstractChar = '\n')
```

Lire `io` jusqu'à la fin du flux/fichier et compter le nombre de lignes. Pour spécifier un fichier, passez le nom du fichier comme premier argument. Les marqueurs EOL autres que `'\n'` sont pris en charge en les passant comme deuxième argument. La dernière ligne non vide de `io` est comptée même si elle ne se termine pas par l'EOL, correspondant à la longueur renvoyée par [`eachline`](@ref) et [`readlines`](@ref).

Pour compter les lignes d'une `String`, `countlines(IOBuffer(str))` peut être utilisé.

# Exemples

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.\n");

julia> countlines(io)
1

julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> countlines(io)
1

julia> eof(io) # compter les lignes déplace le pointeur de fichier
true

julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> countlines(io, eol = '.')
1
```

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\n")
36

julia> countlines("my_file.txt")
1

julia> countlines("my_file.txt", eol = 'n')
4

julia> rm("my_file.txt")

```
