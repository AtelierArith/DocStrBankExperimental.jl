```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/TOML/docs/src/index.md"
```

# TOML

TOML.jl, bir Julia standart kütüphanesidir ve [TOML v1.0](https://toml.io/en/) dosyalarını ayrıştırmak ve yazmak için kullanılır.

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

Bir dosyayı ayrıştırmak için [`TOML.parsefile`](@ref) kullanın. Dosyada bir sözdizimi hatası varsa, bir istisna fırlatılır:

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

Diğer parse fonksiyonlarının ([`TOML.tryparse`](@ref) ve [`TOML.tryparsefile`](@ref)) versiyonları, parser hatası durumunda istisna fırlatmak yerine [`TOML.ParserError`](@ref) ile bilgi döndürmektedir:

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

[`TOML.print`](@ref) fonksiyonu verileri TOML formatında yazdırmak (veya serileştirmek) için kullanılır.

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

Anahtarlar, bazı değerlere göre sıralanabilir.

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

Özel yapılar için, yapıyı desteklenen bir türe dönüştüren bir fonksiyon geçirin.

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
