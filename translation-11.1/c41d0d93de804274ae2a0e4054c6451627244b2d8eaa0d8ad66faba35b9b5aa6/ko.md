```
@test ex
@test f(args...) key=val ...
@test ex broken=true
@test ex skip=true
```

표현식 `ex`가 `true`로 평가되는지 테스트합니다. `@testset` 내에서 실행되면, `true`일 경우 `Pass` `Result`를 반환하고, `false`일 경우 `Fail` `Result`를 반환하며, 평가할 수 없을 경우 `Error` `Result`를 반환합니다. `@testset` 외부에서 실행되면, `Fail` 또는 `Error`를 반환하는 대신 예외를 발생시킵니다.

# 예제

```jldoctest
julia> @test true
Test Passed

julia> @test [1, 2] + [2, 1] == [3, 3]
Test Passed
```

`@test f(args...) key=val...` 형태는 `@test f(args..., key=val...)`를 작성하는 것과 동등하며, 이는 표현식이 약식 비교와 같은 중위 구문을 사용하는 호출인 경우 유용할 수 있습니다:

```jldoctest
julia> @test π ≈ 3.14 atol=0.01
Test Passed
```

이는 더 복잡한 테스트인 `@test ≈(π, 3.14, atol=0.01)`와 동등합니다. 첫 번째가 호출 표현식이고 나머지가 할당(`k=v`)인 경우를 제외하고는 두 개 이상의 표현식을 제공하는 것은 오류입니다.

`key=val` 인수에 대해 어떤 키를 사용할 수 있지만, `broken`과 `skip`은 `@test`의 맥락에서 특별한 의미를 가지므로 사용할 수 없습니다:

  * `broken=cond`는 `cond==true`일 때 현재 일관되게 실패해야 하는 테스트를 나타냅니다. 표현식 `ex`가 `false`로 평가되거나 예외를 발생시키는 경우. `true`로 평가되면 `Broken` `Result`를 반환하고, `true`로 평가되면 `Error` `Result`를 반환합니다. `cond==false`일 때 일반 `@test ex`가 평가됩니다.
  * `skip=cond`는 `cond==true`일 때 실행되지 않아야 하지만 테스트 요약 보고서에 `Broken`으로 포함되어야 하는 테스트를 표시합니다. 이는 간헐적으로 실패하는 테스트나 아직 구현되지 않은 기능의 테스트에 유용할 수 있습니다. `cond==false`일 때 일반 `@test ex`가 평가됩니다.

# 예제

```jldoctest
julia> @test 2 + 2 ≈ 6 atol=1 broken=true
Test Broken
  Expression: ≈(2 + 2, 6, atol = 1)

julia> @test 2 + 2 ≈ 5 atol=1 broken=false
Test Passed

julia> @test 2 + 2 == 5 skip=true
Test Broken
  Skipped: 2 + 2 == 5

julia> @test 2 + 2 == 4 skip=false
Test Passed
```

!!! compat "Julia 1.7"
    `broken` 및 `skip` 키워드 인수는 최소한 Julia 1.7이 필요합니다.

