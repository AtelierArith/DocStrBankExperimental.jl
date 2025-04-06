```
isbinaryoperator(s::Symbol)
```

기호가 이진(중위) 연산자로 사용될 수 있으면 `true`를 반환하고, 그렇지 않으면 `false`를 반환합니다.

# 예시

```jldoctest
julia> Meta.isbinaryoperator(:-), Meta.isbinaryoperator(:√), Meta.isbinaryoperator(:f)
(true, false, false)
```
