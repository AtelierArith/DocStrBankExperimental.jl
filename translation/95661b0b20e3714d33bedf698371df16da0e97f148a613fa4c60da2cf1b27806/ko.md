```
readchomp(x)
```

`x`의 전체를 문자열로 읽고, 만약 있다면 단일 개행 문자를 제거합니다. `chomp(read(x, String))`와 동일합니다.

# 예제

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readchomp("my_file.txt")
"JuliaLang is a GitHub organization.\nIt has many members."

julia> rm("my_file.txt");
```
