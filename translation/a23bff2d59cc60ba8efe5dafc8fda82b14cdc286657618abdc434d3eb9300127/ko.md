```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/TOML/docs/src/index.md"
```

# TOML

TOML.jl은 [TOML v1.0](https://toml.io/en/) 파일을 파싱하고 쓰기 위한 Julia 표준 라이브러리입니다.

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

파일을 파싱하려면 [`TOML.parsefile`](@ref)를 사용하세요. 파일에 구문 오류가 있는 경우 예외가 발생합니다:

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

다른 버전의 파서 함수([`TOML.tryparse`](@ref) 및 [`TOML.tryparsefile`](@ref))는 파서 오류가 발생할 때 예외를 던지는 대신 [`TOML.ParserError`](@ref)를 반환하여 정보를 제공합니다:

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

[`TOML.print`](@ref) 함수는 데이터를 TOML 형식으로 출력(또는 직렬화)하는 데 사용됩니다.

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

키는 특정 값에 따라 정렬될 수 있습니다.

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

사용자 정의 구조체의 경우, 구조체를 지원되는 유형으로 변환하는 함수를 전달하십시오.

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
