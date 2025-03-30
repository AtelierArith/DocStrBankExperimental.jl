```
fetch(c::Channel)
```

`Channel`에서 첫 번째로 사용 가능한 항목을 기다리고 반환합니다(제거하지 않음). 참고: `fetch`는 버퍼가 없는(0 크기) `Channel`에서는 지원되지 않습니다.

# 예제

버퍼가 있는 채널:

```jldoctest
julia> c = Channel(3) do ch
           foreach(i -> put!(ch, i), 1:3)
       end;

julia> fetch(c)
1

julia> collect(c)  # 항목이 제거되지 않음
3-element Vector{Any}:
 1
 2
 3
```
