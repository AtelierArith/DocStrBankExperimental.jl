```
@testset [CustomTestSet] [options...] ["설명"] begin test_ex end
@testset [CustomTestSet] [options...] ["설명 $v"] for v in itr test_ex end
@testset [CustomTestSet] [options...] ["설명 $v, $w"] for v in itrv, w in itrw test_ex end
@testset [CustomTestSet] [options...] ["설명"] test_func()
@testset let v = v, w = w; test_ex; end
```

# begin/end 또는 함수 호출과 함께

@testset가 사용될 때, begin/end 또는 단일 함수 호출과 함께 매크로는 주어진 표현식을 평가하기 위한 새로운 테스트 세트를 시작합니다.

사용자가 지정한 테스트 세트 유형이 없으면 기본적으로 `DefaultTestSet`이 생성됩니다. `DefaultTestSet`은 모든 결과를 기록하며, `Fail` 또는 `Error`가 있는 경우 최상위(비중첩) 테스트 세트의 끝에서 예외를 발생시키고 테스트 결과 요약을 함께 제공합니다.

사용자가 지정한 테스트 세트 유형(`AbstractTestSet`의 하위 유형)을 제공할 수 있으며, 이는 모든 중첩된 `@testset` 호출에도 사용됩니다. 주어진 옵션은 제공된 테스트 세트에만 적용됩니다. 기본 테스트 세트 유형은 세 가지 부울 옵션을 수용합니다:

  * `verbose`: `true`인 경우, 모든 테스트가 통과하더라도 중첩된 테스트 세트의 결과 요약이 표시됩니다(기본값은 `false`입니다).
  * `showtiming`: `true`인 경우, 표시된 각 테스트 세트의 지속 시간이 표시됩니다(기본값은 `true`입니다).
  * `failfast`: `true`인 경우, 테스트 실패 또는 오류가 발생하면 테스트 세트와 모든 자식 테스트 세트가 즉시 반환됩니다(기본값은 `false`입니다). 이는 환경 변수 `JULIA_TEST_FAILFAST`를 통해 전역적으로 설정할 수도 있습니다.

!!! compat "Julia 1.8"
    `@testset test_func()`는 최소한 Julia 1.8이 필요합니다.


!!! compat "Julia 1.9"
    `failfast`는 최소한 Julia 1.9가 필요합니다.


설명 문자열은 루프 인덱스에서 보간을 허용합니다. 설명이 제공되지 않으면 변수에 따라 하나가 구성됩니다. 함수 호출이 제공되면 해당 이름이 사용됩니다. 명시적 설명 문자열은 이 동작을 무시합니다.

기본적으로 `@testset` 매크로는 테스트 세트 객체 자체를 반환하지만, 이 동작은 다른 테스트 세트 유형에서 사용자 정의할 수 있습니다. `for` 루프가 사용되면 매크로는 `finish` 메서드의 반환 값 목록을 수집하고 반환하며, 기본적으로는 각 반복에서 사용된 테스트 세트 객체의 목록을 반환합니다.

`@testset` 본문 실행 전에 `Random.seed!(seed)`에 대한 암시적 호출이 있으며, 여기서 `seed`는 전역 RNG의 현재 시드입니다. 또한 본문 실행 후 전역 RNG의 상태는 `@testset` 이전 상태로 복원됩니다. 이는 실패 시 재현성을 용이하게 하고, 전역 RNG 상태에 대한 부작용과 관계없이 `@testset`의 원활한 재배치를 허용하기 위한 것입니다.

## 예시

```jldoctest; filter = r"trigonometric identities |    4      4  [0-9\.]+s"
julia> @testset "삼각 함수 항등식" begin
           θ = 2/3*π
           @test sin(-θ) ≈ -sin(θ)
           @test cos(-θ) ≈ cos(θ)
           @test sin(2θ) ≈ 2*sin(θ)*cos(θ)
           @test cos(2θ) ≈ cos(θ)^2 - sin(θ)^2
       end;
테스트 요약:            | 통과  총계  시간
삼각 함수 항등식 |    4      4  0.2s
```

# `@testset for`

`@testset for`가 사용될 때, 매크로는 제공된 루프의 각 반복에 대해 새로운 테스트를 시작합니다. 각 테스트 세트의 의미는 `begin/end` 경우와 동일합니다(각 루프 반복에 대해 사용된 것처럼).

# `@testset let`

`@testset let`이 사용될 때, 매크로는 주어진 객체를 포함하여 실패한 테스트에 대한 컨텍스트 객체로 추가된 *투명한* 테스트 세트를 시작합니다. 이는 하나의 더 큰 객체에 대해 관련된 테스트 세트를 수행할 때 유용하며, 개별 테스트 중 하나라도 실패할 경우 이 더 큰 객체를 인쇄하는 것이 바람직합니다. 투명한 테스트 세트는 테스트 세트 계층에서 추가적인 중첩 수준을 도입하지 않으며, 부모 테스트 세트로 직접 전달됩니다(컨텍스트 객체가 실패한 테스트에 추가됨).

!!! compat "Julia 1.9"
    `@testset let`은 최소한 Julia 1.9가 필요합니다.


!!! compat "Julia 1.10"
    여러 `let` 할당은 Julia 1.10부터 지원됩니다.


## 예시

```jldoctest
julia> @testset let logi = log(im)
           @test imag(logi) == π/2
           @test !iszero(real(logi))
       end
테스트 실패: none:3
  표현식: !(iszero(real(logi)))
     컨텍스트: logi = 0.0 + 1.5707963267948966im

ERROR: 테스트 중 오류가 발생했습니다.

julia> @testset let logi = log(im), op = !iszero
           @test imag(logi) == π/2
           @test op(real(logi))
       end
테스트 실패: none:3
  표현식: op(real(logi))
     컨텍스트: logi = 0.0 + 1.5707963267948966im
              op = !iszero

ERROR: 테스트 중 오류가 발생했습니다.
```
