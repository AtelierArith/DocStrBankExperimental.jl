```
@test_broken ex
@test_broken f(args...) key=val ...
```

현재 일관되게 실패하는 테스트를 나타냅니다. 표현식 `ex`가 `false`로 평가되거나 예외를 발생시키는지 테스트합니다. 만약 그렇다면 `Broken` `Result`를 반환하고, 표현식이 `true`로 평가되면 `Error` `Result`를 반환합니다. 이는 [`@test ex broken=true`](@ref @test)와 동등합니다.

`@test_broken f(args...) key=val...` 형식은 `@test` 매크로와 동일하게 작동합니다.

# 예제

```jldoctest
julia> @test_broken 1 == 2
Test Broken
  Expression: 1 == 2

julia> @test_broken 1 == 2 atol=0.1
Test Broken
  Expression: ==(1, 2, atol = 0.1)
```
