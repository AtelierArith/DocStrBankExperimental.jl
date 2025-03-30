```
@test_skip ex
@test_skip f(args...) key=val ...
```

실행되지 않아야 하지만 테스트 요약 보고서에는 `Broken`으로 포함되어야 하는 테스트를 표시합니다. 이는 간헐적으로 실패하는 테스트나 아직 구현되지 않은 기능의 테스트에 유용할 수 있습니다. 이는 [`@test ex skip=true`](@ref @test)와 동일합니다.

`@test_skip f(args...) key=val...` 형식은 `@test` 매크로와 동일하게 작동합니다.

# 예시

```jldoctest
julia> @test_skip 1 == 2
Test Broken
  Skipped: 1 == 2

julia> @test_skip 1 == 2 atol=0.1
Test Broken
  Skipped: ==(1, 2, atol = 0.1)
```
