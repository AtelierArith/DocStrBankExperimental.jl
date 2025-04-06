```
LogLevel(level)
```

로그 레코드의 심각도/상세도.

로그 레벨은 잠재적인 로그 레코드를 필터링할 수 있는 기준을 제공하며, 로그 레코드 데이터 구조를 구성하기 위한 다른 작업이 수행되기 전에 필터링됩니다.

# 예제

```julia-repl
julia> Logging.LogLevel(0) == Logging.Info
true
```
