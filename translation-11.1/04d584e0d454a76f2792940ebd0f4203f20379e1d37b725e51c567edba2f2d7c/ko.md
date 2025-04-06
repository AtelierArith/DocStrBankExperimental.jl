```
open(filename::AbstractString, [mode::AbstractString]; lock = true) -> IOStream
```

문자열 기반 모드 지정자가 사용되는 open의 대체 구문. `mode`의 값은 `fopen(3)` 또는 Perl `open`의 값에 해당하며, 다음 부울 그룹을 설정하는 것과 동일합니다:

| 모드   | 설명               | 키워드                            |
|:---- |:---------------- |:------------------------------ |
| `r`  | 읽기               | 없음                             |
| `w`  | 쓰기, 생성, 잘라내기     | `write = true`                 |
| `a`  | 쓰기, 생성, 추가       | `append = true`                |
| `r+` | 읽기, 쓰기           | `read = true, write = true`    |
| `w+` | 읽기, 쓰기, 생성, 잘라내기 | `truncate = true, read = true` |
| `a+` | 읽기, 쓰기, 생성, 추가   | `append = true, read = true`   |

`lock` 키워드 인자는 안전한 다중 스레드 접근을 위해 작업이 잠길지 여부를 제어합니다.

# 예제

```jldoctest
julia> io = open("myfile.txt", "w");

julia> write(io, "Hello world!");

julia> close(io);

julia> io = open("myfile.txt", "r");

julia> read(io, String)
"Hello world!"

julia> write(io, "This file is read only")
ERROR: ArgumentError: write failed, IOStream is not writeable
[...]

julia> close(io)

julia> io = open("myfile.txt", "a");

julia> write(io, "This stream is not read only")
28

julia> close(io)

julia> rm("myfile.txt")
```

!!! compat "Julia 1.5"
    `lock` 인자는 Julia 1.5부터 사용할 수 있습니다.

