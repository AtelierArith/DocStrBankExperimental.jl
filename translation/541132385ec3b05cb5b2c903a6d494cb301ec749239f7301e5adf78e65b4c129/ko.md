```
walkdir(dir; topdown=true, follow_symlinks=false, onerror=throw)
```

디렉토리의 디렉토리 트리를 탐색하는 반복자를 반환합니다. 반복자는 `(rootpath, dirs, files)`를 포함하는 튜플을 반환합니다. 디렉토리 트리는 위에서 아래로 또는 아래에서 위로 탐색할 수 있습니다. `walkdir` 또는 `stat`가 `IOError`를 만나면 기본적으로 오류를 다시 발생시킵니다. 사용자 정의 오류 처리 함수를 `onerror` 키워드 인수를 통해 제공할 수 있습니다. `onerror`는 `IOError`를 인수로 호출됩니다.

참고: [`readdir`](@ref).

# 예제

```julia
for (root, dirs, files) in walkdir(".")
    println("Directories in $root")
    for dir in dirs
        println(joinpath(root, dir)) # 디렉토리 경로
    end
    println("Files in $root")
    for file in files
        println(joinpath(root, file)) # 파일 경로
    end
end
```

```julia-repl
julia> mkpath("my/test/dir");

julia> itr = walkdir("my");

julia> (root, dirs, files) = first(itr)
("my", ["test"], String[])

julia> (root, dirs, files) = first(itr)
("my/test", ["dir"], String[])

julia> (root, dirs, files) = first(itr)
("my/test/dir", String[], String[])
```
