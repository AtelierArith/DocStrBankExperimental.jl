```
readlines(io::IO=stdin; keep::Bool=false)
readlines(filename::AbstractString; keep::Bool=false)
```

I/O 스트림 또는 파일의 모든 줄을 문자열 벡터로 읽습니다. 동작은 [`readline`](@ref) 함수를 동일한 인수로 반복적으로 호출하고 결과로 얻은 줄을 문자열 벡터로 저장하는 것과 동일합니다. 모든 줄을 한 번에 읽지 않고 반복하려면 [`eachline`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readlines("my_file.txt")
2-element Vector{String}:
 "JuliaLang is a GitHub organization."
 "It has many members."

julia> readlines("my_file.txt", keep=true)
2-element Vector{String}:
 "JuliaLang is a GitHub organization.\n"
 "It has many members.\n"

julia> rm("my_file.txt")
```
