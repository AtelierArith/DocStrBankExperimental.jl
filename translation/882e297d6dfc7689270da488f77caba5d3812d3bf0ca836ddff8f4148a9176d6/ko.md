```
join([io::IO,] iterator [, delim [, last]])
```

주어진 구분자(있는 경우)를 인접 항목 사이에 삽입하여 모든 `iterator`를 단일 문자열로 결합합니다. `last`가 주어지면 마지막 두 항목 사이에 `delim` 대신 사용됩니다. `iterator`의 각 항목은 `print(io::IOBuffer, x)`를 통해 문자열로 변환됩니다. `io`가 주어지면 결과는 `String`으로 반환되는 대신 `io`에 기록됩니다.

# 예제

```jldoctest
julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"

julia> join([1,2,3,4,5])
"12345"
```
