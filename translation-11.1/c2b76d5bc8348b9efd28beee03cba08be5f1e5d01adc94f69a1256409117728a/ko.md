```
Sys.username() -> String
```

현재 사용자의 사용자 이름을 반환합니다. 사용자 이름을 확인할 수 없거나 비어 있는 경우 이 함수는 오류를 발생시킵니다.

환경 변수를 통해 재정의할 수 있는 사용자 이름을 검색하려면, 예를 들어 `USER`, 다음을 사용하는 것이 좋습니다.

```julia
user = get(Sys.username, ENV, "USER")
```

!!! compat "Julia 1.11"
    이 함수는 최소한 Julia 1.11이 필요합니다.


또한 [`homedir`](@ref)를 참조하십시오.
