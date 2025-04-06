```
hex2bytes!(dest::AbstractVector{UInt8}, itr)
```

16진수 문자열을 나타내는 바이트의 iterable `itr`을 이진 표현으로 변환합니다. [`hex2bytes`](@ref)와 유사하지만 출력이 `dest`에 제자리에서 작성됩니다. `dest`의 길이는 `itr`의 길이의 절반이어야 합니다.

!!! compat "Julia 1.7"
    UInt8을 생성하는 반복자를 사용하여 hex2bytes!를 호출하려면 버전 1.7이 필요합니다. 이전 버전에서는 호출하기 전에 iterable을 수집할 수 있습니다.

