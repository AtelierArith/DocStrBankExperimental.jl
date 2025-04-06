```
@assert cond [text]
```

`cond`가 `false`인 경우 [`AssertionError`](@ref)를 발생시킵니다. 이는 주로 디버깅을 돕기 위해 사용자가 확인할 수 있는 조건인 주장을 작성하기 위한 선호되는 구문입니다. 선택적 메시지 `text`는 주장 실패 시 표시됩니다.

!!! 경고     assert는 일부 최적화 수준에서 비활성화될 수 있습니다. 따라서 assert는 디버깅 도구로만 사용해야 하며 인증 검증(예: 비밀번호 확인 또는 배열 경계 확인)에는 사용되지 않아야 합니다. 코드는 함수의 올바른 동작을 위해 `cond` 실행의 부작용에 의존해서는 안 됩니다.

# 예제

```jldoctest
julia> @assert iseven(3) "3은 홀수입니다!"
ERROR: AssertionError: 3은 홀수입니다!

julia> @assert isodd(3) "짝수란 대체 무엇인가요?"
```
