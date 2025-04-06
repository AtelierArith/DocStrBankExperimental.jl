```
displaysize([io::IO]) -> (lines, columns)
```

이 `IO` 객체에 출력을 렌더링하는 데 사용할 수 있는 화면의 명목 크기를 반환합니다. 입력이 제공되지 않으면 환경 변수 `LINES`와 `COLUMNS`가 읽힙니다. 이 값들이 설정되어 있지 않으면 기본 크기 `(24, 80)`이 반환됩니다.

# 예제

```jldoctest
julia> withenv("LINES" => 30, "COLUMNS" => 100) do
           displaysize()
       end
(30, 100)
```

TTY 크기를 얻으려면,

```julia-repl
julia> displaysize(stdout)
(34, 147)
```
