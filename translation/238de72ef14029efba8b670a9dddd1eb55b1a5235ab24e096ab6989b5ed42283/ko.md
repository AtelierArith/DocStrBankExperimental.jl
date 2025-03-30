```
mkdir(path::AbstractString; mode::Unsigned = 0o777)
```

`path`라는 이름과 `mode`라는 권한으로 새 디렉토리를 만듭니다. `mode`는 기본적으로 `0o777`이며, 현재 파일 생성 마스크에 의해 수정됩니다. 이 함수는 한 개의 디렉토리만 생성합니다. 디렉토리가 이미 존재하거나 일부 중간 디렉토리가 존재하지 않으면 이 함수는 오류를 발생시킵니다. 필요한 모든 중간 디렉토리를 생성하는 함수에 대한 내용은 [`mkpath`](@ref)를 참조하세요. `path`를 반환합니다.

# 예제

```julia-repl
julia> mkdir("testingdir")
"testingdir"

julia> cd("testingdir")

julia> pwd()
"/home/JuliaUser/testingdir"
```
