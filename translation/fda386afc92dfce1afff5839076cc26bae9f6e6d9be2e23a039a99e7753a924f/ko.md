```
Base64EncodePipe(ostream)
```

새로운 쓰기 전용 I/O 스트림을 반환하며, 이 스트림에 기록된 모든 바이트를 `ostream`에 기록된 base64 인코딩된 ASCII 바이트로 변환합니다. `Base64EncodePipe` 스트림에서 [`close`](@ref)를 호출하는 것은 인코딩을 완료하는 데 필요합니다(하지만 `ostream`은 닫지 않습니다).

# 예제

```jldoctest
julia> io = IOBuffer();

julia> iob64_encode = Base64EncodePipe(io);

julia> write(iob64_encode, "Hello!")
6

julia> close(iob64_encode);

julia> str = String(take!(io))
"SGVsbG8h"

julia> String(base64decode(str))
"Hello!"
```
