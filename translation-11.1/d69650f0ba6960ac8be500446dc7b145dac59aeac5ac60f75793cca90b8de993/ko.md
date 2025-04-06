```
read(filename::AbstractString)
```

파일의 전체 내용을 `Vector{UInt8}`로 읽습니다.

```
read(filename::AbstractString, String)
```

파일의 전체 내용을 문자열로 읽습니다.

```
read(filename::AbstractString, args...)
```

파일을 열고 그 내용을 읽습니다. `args`는 `read`에 전달됩니다: 이는 `open(io->read(io, args...), filename)`과 동일합니다.
