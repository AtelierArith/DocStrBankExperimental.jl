```
readuntil(stream::IO, delim; keep::Bool = false)
readuntil(filename::AbstractString, delim; keep::Bool = false)
```

주어진 구분자까지 I/O `stream` 또는 파일에서 문자열을 읽습니다. 구분자는 `UInt8`, `AbstractChar`, 문자열 또는 벡터일 수 있습니다. 키워드 인수 `keep`는 결과에 구분자가 포함되는지 여부를 제어합니다. 텍스트는 UTF-8로 인코딩된 것으로 가정됩니다.

`delim`이 `AbstractChar` 또는 문자열인 경우 `String`을 반환하고, 그렇지 않으면 `Vector{typeof(delim)}`를 반환합니다. 대신 다른 스트림(미리 할당된 [`IOBuffer`](@ref)일 수 있음)에 제자리에서 쓰려면 [`copyuntil`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readuntil("my_file.txt", 'L')
"Julia"

julia> readuntil("my_file.txt", '.', keep = true)
"JuliaLang is a GitHub organization."

julia> rm("my_file.txt")
```
