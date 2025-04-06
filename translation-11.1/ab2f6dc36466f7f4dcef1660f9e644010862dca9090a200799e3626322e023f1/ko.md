```
Main
```

`Main`은 최상위 모듈이며, Julia는 `Main`을 현재 모듈로 설정하여 시작합니다. 프롬프트에서 정의된 변수는 `Main`에 들어가고, `varinfo`는 `Main`의 변수를 나열합니다.

```jldoctest
julia> @__MODULE__
Main
```
