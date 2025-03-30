```
circcopy!(dest, src)
```

`src`를 `dest`로 복사하며, 각 차원을 그 길이에 따라 모듈로 인덱싱합니다. `src`와 `dest`는 같은 크기를 가져야 하지만, 인덱스에서 오프셋을 가질 수 있습니다; 어떤 오프셋도 (원형) 래핑을 초래합니다. 배열이 겹치는 인덱스를 가지면, 겹치는 영역에서 `dest`는 `src`와 일치합니다.

!!! warning
    어떤 변형된 인자가 다른 인자와 메모리를 공유할 때 동작이 예기치 않게 나타날 수 있습니다.


참고: [`circshift`](@ref).

# 예제

```julia-repl
julia> src = reshape(Vector(1:16), (4,4))
4×4 Array{Int64,2}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> dest = OffsetArray{Int}(undef, (0:3,2:5))

julia> circcopy!(dest, src)
OffsetArrays.OffsetArray{Int64,2,Array{Int64,2}} with indices 0:3×2:5:
 8  12  16  4
 5   9  13  1
 6  10  14  2
 7  11  15  3

julia> dest[1:3,2:4] == src[1:3,2:4]
true
```
