```
readdir(dir::AbstractString=pwd();
    join::Bool = false,
    sort::Bool = true,
) -> Vector{String}
```

디렉토리 `dir`의 이름을 반환하거나 주어지지 않은 경우 현재 작업 디렉토리의 이름을 반환합니다. `join`이 false인 경우, `readdir`은 디렉토리의 이름만 그대로 반환합니다. `join`이 true인 경우, 각 `name`에 대해 `joinpath(dir, name)`을 반환하여 반환된 문자열이 전체 경로가 되도록 합니다. 절대 경로를 얻으려면 절대 디렉토리 경로와 `join`을 true로 설정하여 `readdir`을 호출하십시오.

기본적으로 `readdir`은 반환하는 이름 목록을 정렬합니다. 이름 정렬을 건너뛰고 파일 시스템이 나열하는 순서로 얻으려면 `readdir(dir, sort=false)`를 사용하여 정렬을 선택 해제할 수 있습니다.

또한 참조: [`walkdir`](@ref).

!!! compat "Julia 1.4"
    `join` 및 `sort` 키워드 인수는 최소한 Julia 1.4가 필요합니다.


# 예제

```julia-repl
julia> cd("/home/JuliaUser/dev/julia")

julia> readdir()
30-element Array{String,1}:
 ".appveyor.yml"
 ".git"
 ".gitattributes"
 ⋮
 "ui"
 "usr"
 "usr-staging"

julia> readdir(join=true)
30-element Array{String,1}:
 "/home/JuliaUser/dev/julia/.appveyor.yml"
 "/home/JuliaUser/dev/julia/.git"
 "/home/JuliaUser/dev/julia/.gitattributes"
 ⋮
 "/home/JuliaUser/dev/julia/ui"
 "/home/JuliaUser/dev/julia/usr"
 "/home/JuliaUser/dev/julia/usr-staging"

julia> readdir("base")
145-element Array{String,1}:
 ".gitignore"
 "Base.jl"
 "Enums.jl"
 ⋮
 "version_git.sh"
 "views.jl"
 "weakkeydict.jl"

julia> readdir("base", join=true)
145-element Array{String,1}:
 "base/.gitignore"
 "base/Base.jl"
 "base/Enums.jl"
 ⋮
 "base/version_git.sh"
 "base/views.jl"
 "base/weakkeydict.jl"

julia> readdir(abspath("base"), join=true)
145-element Array{String,1}:
 "/home/JuliaUser/dev/julia/base/.gitignore"
 "/home/JuliaUser/dev/julia/base/Base.jl"
 "/home/JuliaUser/dev/julia/base/Enums.jl"
 ⋮
 "/home/JuliaUser/dev/julia/base/version_git.sh"
 "/home/JuliaUser/dev/julia/base/views.jl"
 "/home/JuliaUser/dev/julia/base/weakkeydict.jl"
```
