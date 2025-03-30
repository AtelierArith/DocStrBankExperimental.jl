```
touch(path::AbstractString)
touch(fd::File)
```

파일의 마지막 수정 타임스탬프를 현재 시간으로 업데이트합니다.

파일이 존재하지 않으면 새 파일이 생성됩니다.

`path`를 반환합니다.

# 예시

```julia-repl
julia> write("my_little_file", 2);

julia> mtime("my_little_file")
1.5273815391135583e9

julia> touch("my_little_file");

julia> mtime("my_little_file")
1.527381559163435e9
```

[`mtime`](@ref)가 `touch`에 의해 수정된 것을 볼 수 있습니다.
