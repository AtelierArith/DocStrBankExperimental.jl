```
rm(path::AbstractString; force::Bool=false, recursive::Bool=false)
```

주어진 경로에서 파일, 링크 또는 빈 디렉토리를 삭제합니다. `force=true`가 전달되면 존재하지 않는 경로는 오류로 처리되지 않습니다. `recursive=true`가 전달되고 경로가 디렉토리인 경우 모든 내용이 재귀적으로 제거됩니다.

# 예제

```jldoctest
julia> mkpath("my/test/dir");

julia> rm("my", recursive=true)

julia> rm("this_file_does_not_exist", force=true)

julia> rm("this_file_does_not_exist")
ERROR: IOError: unlink("this_file_does_not_exist"): no such file or directory (ENOENT)
Stacktrace:
[...]
```
