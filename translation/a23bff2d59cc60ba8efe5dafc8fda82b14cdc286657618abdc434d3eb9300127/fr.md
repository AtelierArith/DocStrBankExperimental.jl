```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/TOML/docs/src/index.md"
```

# TOML

TOML.jl is a Julia standard library for parsing and writing [TOML v1.0](https://toml.io/en/) files.

## Parsing TOML data

```jldoctest
julia> using TOML

julia> data = """
           [database]
           server = "192.168.1.1"
           ports = [ 8001, 8001, 8002 ]
       """;

julia> TOML.parse(data)
Dict{String, Any} with 1 entry:
  "database" => Dict{String, Any}("server"=>"192.168.1.1", "ports"=>[8001, 8001…
```

Pour analyser un fichier, utilisez [`TOML.parsefile`](@ref). Si le fichier contient une erreur de syntaxe, une exception est levée :

```jldoctest
julia> using TOML

julia> TOML.parse("""
           value = 0.0.0
       """)
ERROR: TOML Parser error:
none:1:16 error: failed to parse value
      value = 0.0.0
                 ^
[...]
```

Il existe d'autres versions des fonctions de parsing ([`TOML.tryparse`](@ref) et [`TOML.tryparsefile`](@ref)) qui, au lieu de lancer des exceptions en cas d'erreur de parsing, retournent un [`TOML.ParserError`](@ref) avec des informations :

```jldoctest
julia> using TOML

julia> err = TOML.tryparse("""
           value = 0.0.0
       """);

julia> err.type
ErrGenericValueError::ErrorType = 14

julia> err.line
1

julia> err.column
16
```

## Exporting data to TOML file

La fonction [`TOML.print`](@ref) est utilisée pour imprimer (ou sérialiser) des données au format TOML.

```jldoctest
julia> using TOML

julia> data = Dict(
          "names" => ["Julia", "Julio"],
          "age" => [10, 20],
       );

julia> TOML.print(data)
names = ["Julia", "Julio"]
age = [10, 20]

julia> fname = tempname();

julia> open(fname, "w") do io
           TOML.print(io, data)
       end

julia> TOML.parsefile(fname)
Dict{String, Any} with 2 entries:
  "names" => ["Julia", "Julio"]
  "age"   => [10, 20]
```

Les clés peuvent être triées en fonction d'une certaine valeur.

```jldoctest
julia> using TOML

julia> TOML.print(Dict(
       "abc"  => 1,
       "ab"   => 2,
       "abcd" => 3,
       ); sorted=true, by=length)
ab = 2
abc = 1
abcd = 3
```

Pour les structures personnalisées, passez une fonction qui convertit la structure en un type pris en charge.

```jldoctest
julia> using TOML

julia> struct MyStruct
           a::Int
           b::String
       end

julia> TOML.print(Dict("foo" => MyStruct(5, "bar"))) do x
           x isa MyStruct && return [x.a, x.b]
           error("unhandled type $(typeof(x))")
       end
foo = [5, "bar"]
```

## References

```@docs
TOML.parse
TOML.parsefile
TOML.tryparse
TOML.tryparsefile
TOML.print
TOML.Parser
TOML.ParserError
```
