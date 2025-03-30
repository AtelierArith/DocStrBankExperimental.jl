```
skipchars(predicate, io::IO; linecomment=nothing)
```

스트림 `io`를 진행시켜 다음에 읽을 문자가 `predicate`가 `false`를 반환하는 첫 번째 남은 문자로 설정됩니다. 키워드 인수 `linecomment`가 지정된 경우, 해당 문자부터 다음 줄의 시작까지의 모든 문자는 무시됩니다.

# 예제

```jldoctest
julia> buf = IOBuffer("    text")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=1, mark=-1)

julia> skipchars(isspace, buf)
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=5, mark=-1)

julia> String(readavailable(buf))
"text"
```
