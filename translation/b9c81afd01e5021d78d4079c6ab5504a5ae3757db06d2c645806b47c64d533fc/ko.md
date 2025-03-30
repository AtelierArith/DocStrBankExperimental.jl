```
cd(f::Function, dir::AbstractString=homedir())
```

현재 작업 디렉토리를 `dir`로 일시적으로 변경하고, 함수 `f`를 적용한 후 원래 디렉토리로 돌아갑니다.

# 예제

```julia-repl
julia> pwd()
"/home/JuliaUser"

julia> cd(readdir, "/home/JuliaUser/Projects/julia")
34-element Array{String,1}:
 ".circleci"
 ".freebsdci.sh"
 ".git"
 ".gitattributes"
 ".github"
 ⋮
 "test"
 "ui"
 "usr"
 "usr-staging"

julia> pwd()
"/home/JuliaUser"
```
