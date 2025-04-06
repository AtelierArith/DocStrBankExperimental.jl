```
retry(f;  delays=ExponentialBackOff(), check=nothing) -> Function
```

익명 함수를 반환하여 함수 `f`를 호출합니다. 예외가 발생하면 `check`가 `true`를 반환할 때마다 `delays`에 지정된 초 수만큼 대기한 후 `f`가 반복적으로 호출됩니다. `check`는 `delays`의 현재 상태와 `Exception`을 입력으로 받아야 합니다.

!!! compat "Julia 1.2"
    Julia 1.2 이전에는 이 시그니처가 `f::Function`으로 제한되었습니다.


# 예제

```julia
retry(f, delays=fill(5.0, 3))
retry(f, delays=rand(5:10, 2))
retry(f, delays=Base.ExponentialBackOff(n=3, first_delay=5, max_delay=1000))
retry(http_get, check=(s,e)->e.status == "503")(url)
retry(read, check=(s,e)->isa(e, IOError))(io, 128; all=false)
```
