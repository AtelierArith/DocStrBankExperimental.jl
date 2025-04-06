```
readline(io::IO=stdin; keep::Bool=false)
readline(filename::AbstractString; keep::Bool=false)
```

주어진 I/O 스트림 또는 파일에서 한 줄의 텍스트를 읽습니다(기본값은 `stdin`). 파일에서 읽을 때, 텍스트는 UTF-8로 인코딩된 것으로 가정됩니다. 입력의 줄은 `'\n'` 또는 `"\r\n"` 또는 입력 스트림의 끝으로 끝납니다. `keep`이 false(기본값)인 경우, 이러한 후행 개행 문자는 반환되기 전에 줄에서 제거됩니다. `keep`이 true인 경우, 이들은 줄의 일부로 반환됩니다.

`String`을 반환합니다. 대신 다른 스트림에 제자리에서 쓰려면 [`copyline`](@ref)을 참조하십시오(이는 미리 할당된 [`IOBuffer`](@ref)가 될 수 있습니다).

보다 일반적인 구분 기호까지 읽으려면 [`readuntil`](@ref)을 참조하십시오.

# 예제

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readline("my_file.txt")
"JuliaLang is a GitHub organization."

julia> readline("my_file.txt", keep=true)
"JuliaLang is a GitHub organization.\n"

julia> rm("my_file.txt")
```

```julia-repl
julia> print("Enter your name: ")
Enter your name:

julia> your_name = readline()
Logan
"Logan"
```
