```
copyuntil(out::IO, stream::IO, delim; keep::Bool = false)
copyuntil(out::IO, filename::AbstractString, delim; keep::Bool = false)
```

주어진 구분자까지 I/O `stream` 또는 파일에서 문자열을 `out` 스트림으로 복사하고 `out`을 반환합니다. 구분자는 `UInt8`, `AbstractChar`, 문자열 또는 벡터일 수 있습니다. 키워드 인수 `keep`는 결과에 구분자가 포함되는지 여부를 제어합니다. 텍스트는 UTF-8로 인코딩된 것으로 가정됩니다.

[`readuntil`](@ref)와 유사하지만, `copyuntil`은 문자열을 할당하지 않고 직접 `out`에 씁니다. (예를 들어, 미리 할당된 [`IOBuffer`](@ref)로 데이터를 읽는 데 사용할 수 있습니다.)

# 예제

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", 'L')))
"Julia"

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", '.', keep = true)))
"JuliaLang is a GitHub organization."

julia> rm("my_file.txt")
```
