```
copyline(out::IO, io::IO=stdin; keep::Bool=false)
copyline(out::IO, filename::AbstractString; keep::Bool=false)
```

I/O `스트림` 또는 파일에서 `out` 스트림으로 단일 텍스트 라인을 복사하고 `out`을 반환합니다.

파일에서 읽을 때, 텍스트는 UTF-8로 인코딩된 것으로 가정됩니다. 입력의 라인은 `'\n'` 또는 `"\r\n"` 또는 입력 스트림의 끝으로 끝납니다. `keep`이 false일 때(기본값), 이러한 후행 개행 문자는 반환되기 전에 라인에서 제거됩니다. `keep`이 true일 때, 이들은 라인의 일부로 반환됩니다.

[`readline`](@ref)와 유사하며, `String`을 반환합니다. 반면에 `copyline`은 문자열을 할당하지 않고 직접 `out`에 씁니다. (예를 들어, 미리 할당된 [`IOBuffer`](@ref)로 데이터를 읽는 데 사용할 수 있습니다.)

보다 일반적인 구분 기호까지 읽기 위해 [`copyuntil`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> String(take!(copyline(IOBuffer(), "my_file.txt")))
"JuliaLang is a GitHub organization."

julia> String(take!(copyline(IOBuffer(), "my_file.txt", keep=true)))
"JuliaLang is a GitHub organization.\n"

julia> rm("my_file.txt")
```
