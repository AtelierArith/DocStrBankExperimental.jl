```
AssertionError([msg])
```

주장된 조건이 `true`로 평가되지 않았습니다. 선택적 인수 `msg`는 설명적인 오류 문자열입니다.

# 예제

```jldoctest
julia> @assert false "this is not true"
ERROR: AssertionError: this is not true
```

`AssertionError`는 일반적으로 [`@assert`](@ref)에서 발생합니다. ```
