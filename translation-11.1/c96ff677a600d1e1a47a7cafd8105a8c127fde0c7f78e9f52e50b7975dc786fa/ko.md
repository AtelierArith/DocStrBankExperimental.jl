```
@test_throws exception expr
```

표현식 `expr`이 `exception`을 발생시키는지 테스트합니다. 예외는 타입, 문자열, 표시된 오류 메시지에 발생하는 정규 표현식 또는 문자열 목록, 일치하는 함수 또는 값(필드를 비교하여 동등성을 테스트함)으로 지정할 수 있습니다. `@test_throws`는 후행 키워드 형식을 지원하지 않습니다.

!!! compat "Julia 1.8"
    타입이나 값을 제외한 다른 것을 `exception`으로 지정하는 기능은 Julia v1.8 이상이 필요합니다.


# 예제

```jldoctest
julia> @test_throws BoundsError [1, 2, 3][4]
Test Passed
      Thrown: BoundsError

julia> @test_throws DimensionMismatch [1, 2, 3] + [1, 2]
Test Passed
      Thrown: DimensionMismatch

julia> @test_throws "Try sqrt(Complex" sqrt(-1)
Test Passed
     Message: "DomainError with -1.0:\nsqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x))."
```

마지막 예제에서는 단일 문자열과 일치하는 대신 다음과 같이 수행할 수 있었습니다:

  * `["Try", "Complex"]` (문자열 목록)
  * `r"Try sqrt\([Cc]omplex"` (정규 표현식)
  * `str -> occursin("complex", str)` (일치하는 함수)
