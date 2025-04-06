```
mkpath(path::AbstractString; mode::Unsigned = 0o777)
```

필요에 따라 `path`의 모든 중간 디렉토리를 생성합니다. 디렉토리는 기본값이 `0o777`인 `mode` 권한으로 생성되며, 현재 파일 생성 마스크에 의해 수정됩니다. [`mkdir`](@ref)와 달리, `mkpath`는 `path`(또는 그 일부)가 이미 존재하는 경우 오류를 발생시키지 않습니다. 그러나 `path`(또는 그 일부)가 기존 파일을 가리키는 경우 오류가 발생합니다. `path`를 반환합니다.

`path`에 파일 이름이 포함되어 있다면, 파일 이름을 사용하여 디렉토리를 생성하지 않도록 `mkpath(dirname(path))`를 사용하는 것이 좋습니다.

# 예제

```julia-repl
julia> cd(mktempdir())

julia> mkpath("my/test/dir") # 세 개의 디렉토리를 생성합니다.
"my/test/dir"

julia> readdir()
1-element Array{String,1}:
 "my"

julia> cd("my")

julia> readdir()
1-element Array{String,1}:
 "test"

julia> readdir("test")
1-element Array{String,1}:
 "dir"

julia> mkpath("intermediate_dir/actually_a_directory.txt") # 두 개의 디렉토리를 생성합니다.
"intermediate_dir/actually_a_directory.txt"

julia> isdir("intermediate_dir/actually_a_directory.txt")
true

```
