```
ErrorException(msg)
```

일반적인 오류 유형입니다. `.msg` 필드에 있는 오류 메시지는 더 구체적인 세부정보를 제공할 수 있습니다.

# 예시

```jldoctest
julia> ex = ErrorException("I've done a bad thing");

julia> ex.msg
"I've done a bad thing"
```
