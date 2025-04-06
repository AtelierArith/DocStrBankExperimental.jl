```
nextind(str::AbstractString, i::Integer, n::Integer=1) -> Int
```

  * 경우 `n == 1`

    만약 `i`가 `s`의 범위 내에 있다면, `i` 인덱스 이후에 시작하는 문자 인코딩의 시작 인덱스를 반환합니다. 다시 말해, 만약 `i`가 문자의 시작이라면, 다음 문자의 시작을 반환하고; 만약 `i`가 문자의 시작이 아니라면, 문자의 시작까지 앞으로 이동하여 그 인덱스를 반환합니다. 만약 `i`가 `0`과 같다면 `1`을 반환합니다. 만약 `i`가 범위 내에 있지만 `lastindex(str)`보다 크거나 같다면 `ncodeunits(str)+1`을 반환합니다. 그렇지 않으면 `BoundsError`를 발생시킵니다.
  * 경우 `n > 1`

    `n==1`에 대해 `nextind`를 `n`번 적용하는 것처럼 동작합니다. 유일한 차이점은 `n`이 너무 커서 `nextind`를 적용하면 `ncodeunits(str)+1`에 도달할 경우, 남은 각 반복은 반환된 값을 `1`씩 증가시킵니다. 이는 이 경우 `nextind`가 `ncodeunits(str)+1`보다 큰 값을 반환할 수 있음을 의미합니다.
  * 경우 `n == 0`

    `i`가 `s`의 유효한 인덱스이거나 `0`과 같을 경우에만 `i`를 반환합니다. 그렇지 않으면 `StringIndexError` 또는 `BoundsError`가 발생합니다.

# 예제

```jldoctest
julia> nextind("α", 0)
1

julia> nextind("α", 1)
3

julia> nextind("α", 3)
ERROR: BoundsError: attempt to access 2-codeunit String at index [3]
[...]

julia> nextind("α", 0, 2)
3

julia> nextind("α", 1, 2)
4
```
