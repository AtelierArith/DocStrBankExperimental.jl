```
@nref N A indexexpr
```

`A[i_1, i_2, ...]`와 같은 표현식을 생성합니다. `indexexpr`는 반복 기호 접두사이거나 익명 함수 표현식일 수 있습니다.

# 예시

```jldoctest
julia> @macroexpand Base.Cartesian.@nref 3 A i
:(A[i_1, i_2, i_3])
```
