```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Random/docs/src/index.md"
```

# Random Numbers

```@meta
DocTestSetup = :(using Random)
```

줄리아에서의 난수 생성은 기본적으로 [Xoshiro256++](https://prng.di.unimi.it/) 알고리즘을 사용하며, `Task`별 상태를 가집니다. 다른 RNG 유형은 `AbstractRNG` 유형을 상속하여 플러그인할 수 있으며, 이를 통해 여러 개의 난수 스트림을 얻을 수 있습니다.

`Random` 패키지에서 내보내는 PRNG(의사 난수 생성기)는 다음과 같습니다:

  * `TaskLocalRNG`: 현재 활성화된 작업 로컬 스트림의 사용을 나타내는 토큰으로, 부모 작업에서 결정적으로 시드가 생성되거나 프로그램 시작 시 `RandomDevice`(시스템 무작위성 사용)로 시드가 생성됩니다.
  * `Xoshiro`: Xoshiro256++ 알고리즘을 사용하여 작은 상태 벡터와 높은 성능으로 고품질의 난수 스트림을 생성합니다.
  * `RandomDevice`: OS에서 제공하는 엔트로피. 이는 암호학적으로 안전한 난수(CS(P)RNG)에 사용될 수 있습니다.
  * `MersenneTwister`: 이전 버전의 Julia에서 기본값이었던 대체 고품질 PRNG로, 꽤 빠르지만 상태 벡터를 저장하고 난수 시퀀스를 생성하는 데 훨씬 더 많은 공간이 필요합니다.

대부분의 랜덤 생성과 관련된 함수는 선택적 `AbstractRNG` 객체를 첫 번째 인수로 받아들입니다. 일부는 랜덤 값의 배열을 생성하기 위해 차원 사양 `dims...` (튜플로 제공될 수도 있음)도 허용합니다. 다중 스레드 프로그램에서는 일반적으로 스레드나 작업마다 서로 다른 RNG 객체를 사용하여 스레드 안전성을 확보해야 합니다. 그러나 기본 RNG는 Julia 1.3부터 스레드 안전하며(버전 1.6까지는 스레드별 RNG를 사용하고, 그 이후에는 작업별 RNG를 사용합니다).

제공된 RNG는 다음 유형의 균일 난수를 생성할 수 있습니다: [`Float16`](@ref), [`Float32`](@ref), [`Float64`](@ref), [`BigFloat`](@ref), [`Bool`](@ref), [`Int8`](@ref), [`UInt8`](@ref), [`Int16`](@ref), [`UInt16`](@ref), [`Int32`](@ref), [`UInt32`](@ref), [`Int64`](@ref), [`UInt64`](@ref), [`Int128`](@ref), [`UInt128`](@ref), [`BigInt`](@ref) (또는 이러한 유형의 복소수). 난수 부동 소수점 숫자는 $[0, 1)$에서 균일하게 생성됩니다. `BigInt`가 무한 정수를 나타내므로, 구간을 지정해야 합니다 (예: `rand(big.(1:6))`).

또한, 일부 `AbstractFloat` 및 `Complex` 유형에 대해 정규 분포 및 지수 분포가 구현되어 있습니다. 자세한 내용은 [`randn`](@ref) 및 [`randexp`](@ref)를 참조하십시오.

다른 분포에서 무작위 숫자를 생성하려면 [Distributions.jl](https://juliastats.org/Distributions.jl/stable/) 패키지를 참조하세요.

!!! warning
    무작위 숫자가 생성되는 정확한 방식은 구현 세부사항으로 간주되기 때문에, 버전 변경 후 생성되는 숫자 스트림이 버그 수정 및 속도 개선으로 인해 변경될 수 있습니다. 단위 테스트 중 특정 시드나 생성된 숫자 스트림에 의존하는 것은 권장되지 않으며, 대신 해당 메서드의 속성을 테스트하는 것을 고려해야 합니다.


## Random numbers module

```@docs
Random.Random
```

## Random generation functions

```@docs
Random.rand
Random.rand!
Random.bitrand
Random.randn
Random.randn!
Random.randexp
Random.randexp!
Random.randstring
```

## Subsequences, permutations and shuffling

```@docs
Random.randsubseq
Random.randsubseq!
Random.randperm
Random.randperm!
Random.randcycle
Random.randcycle!
Random.shuffle
Random.shuffle!
```

## Generators (creation and seeding)

```@docs
Random.default_rng
Random.seed!
Random.AbstractRNG
Random.TaskLocalRNG
Random.Xoshiro
Random.MersenneTwister
Random.RandomDevice
```

## [Hooking into the `Random` API](@id rand-api-hook)

`Random` 기능을 확장하는 주로 두 가지 직교적인 방법이 있습니다:

1. 사용자 정의 유형의 임의 값 생성
2. 새로운 생성기 만들기

1)의 API는 꽤 기능적이지만, 비교적 최근에 도입되었기 때문에 `Random` 모듈의 후속 릴리스에서 여전히 발전해야 할 수 있습니다. 예를 들어, 일반적으로 모든 다른 일반적인 메서드가 자동으로 작동하도록 하려면 하나의 `rand` 메서드를 구현하는 것으로 충분합니다.

2)의 API는 여전히 기본적이며, 일반적으로 생성된 값의 유형을 지원하기 위해 구현자가 필요 이상으로 더 많은 작업을 요구할 수 있습니다.

### Generating random values of custom types

무작위 값을 생성하는 것은 다양한 분포에 대해 여러 가지 트레이드오프를 수반할 수 있습니다. *미리 계산된* 값, 예를 들어 이산 분포를 위한 [alias table](https://en.wikipedia.org/wiki/Alias_method) 또는 단변량 분포를 위한 [“squeezing” functions](https://en.wikipedia.org/wiki/Rejection_sampling)는 샘플링 속도를 상당히 높일 수 있습니다. 미리 계산해야 할 정보의 양은 우리가 분포에서 추출할 값의 수에 따라 달라질 수 있습니다. 또한, 일부 난수 생성기는 다양한 알고리즘이 활용하고자 할 수 있는 특정 속성을 가질 수 있습니다.

`Random` 모듈은 이러한 문제를 해결할 수 있는 무작위 값을 얻기 위한 사용자 정의 가능한 프레임워크를 정의합니다. `rand`의 각 호출은 위의 트레이드오프를 염두에 두고 사용자 정의할 수 있는 *샘플러*를 생성하며, 이는 `Sampler`에 메서드를 추가함으로써 이루어집니다. `Sampler`는 무작위 수 생성기, 분포를 특징짓는 객체, 반복 횟수에 대한 제안을 기반으로 분배할 수 있습니다. 현재 후자의 경우, `Val{1}`(단일 샘플용)과 `Val{Inf}`(임의의 수용)를 사용하며, `Random.Repetition`은 두 가지 모두에 대한 별칭입니다.

`Sampler`가 반환하는 객체는 무작위 값을 생성하는 데 사용됩니다. 샘플링할 수 있는 값 `X`에 대한 무작위 생성 인터페이스를 구현할 때, 구현자는 다음 메서드를 정의해야 합니다.

```julia
rand(rng, sampler)
```

특정 `sampler`는 `Sampler(rng, X, repetition)`에 의해 반환됩니다.

샘플러는 `rand(rng, sampler)`를 구현하는 임의의 값일 수 있지만, 대부분의 애플리케이션에서는 다음과 같은 미리 정의된 샘플러가 충분할 수 있습니다:

1. `SamplerType{T}()`는 타입 `T`에서 샘플을 추출하는 샘플러를 구현하는 데 사용할 수 있습니다 (예: `rand(Int)`). 이것은 *타입*에 대해 `Sampler`가 반환하는 기본값입니다.
2. `SamplerTrivial(self)`는 `self`에 대한 간단한 래퍼로, `[]`를 사용하여 접근할 수 있습니다. 이는 사전 계산된 정보가 필요하지 않을 때(예: `rand(1:3)`) 권장되는 샘플러이며, *값*에 대해 `Sampler`가 반환하는 기본값입니다.
3. `SamplerSimple(self, data)`는 또한 임의의 미리 계산된 값을 저장하는 데 사용할 수 있는 추가 `data` 필드를 포함하고 있으며, 이는 `Sampler`의 *사용자 정의 메서드*에서 계산되어야 합니다.

각각에 대한 예제를 제공합니다. 여기서는 알고리즘의 선택이 RNG와 독립적이라고 가정하므로, 서명에서 `AbstractRNG`를 사용합니다.

```@docs
Random.Sampler
Random.SamplerType
Random.SamplerTrivial
Random.SamplerSimple
```

사전 계산을 실제 값 생성과 분리하는 것은 API의 일부이며, 사용자에게도 제공됩니다. 예를 들어, `rand(rng, 1:20)`를 루프에서 반복적으로 호출해야 한다고 가정해 보겠습니다. 이 분리를 활용하는 방법은 다음과 같습니다:

```julia
rng = Xoshiro()
sp = Random.Sampler(rng, 1:20) # or Random.Sampler(Xoshiro, 1:20)
for x in X
    n = rand(rng, sp) # similar to n = rand(rng, 1:20)
    # use n
end
```

이것은 표준 라이브러리에서도 사용되는 메커니즘으로, 예를 들어 기본 구현인 랜덤 배열 생성(`rand(1:20, 10)`와 같은)에서 사용됩니다.

#### Generating values from a type

주어진 타입 `T`에 대해, 현재 `rand(T)`가 정의되어 있다면 타입 `T`의 객체가 생성될 것이라고 가정합니다. `SamplerType`은 *타입에 대한 기본 샘플러*입니다. 타입 `T`의 값의 무작위 생성을 정의하기 위해서는 `rand(rng::AbstractRNG, ::Random.SamplerType{T})` 메서드를 정의해야 하며, 이 메서드는 `rand(rng, T)`가 반환할 것으로 예상되는 값을 반환해야 합니다.

다음 예를 들어 보겠습니다: 우리는 `1`부터 `n`까지 번호가 매겨진 가변적인 면의 수 `n`을 가진 `Die` 타입을 구현합니다. 우리는 `rand(Die)`가 최소 4면에서 최대 20면까지의 무작위 수를 가진 `Die`를 생성하기를 원합니다.

```jldoctest Die
struct Die
    nsides::Int # number of sides
end

Random.rand(rng::AbstractRNG, ::Random.SamplerType{Die}) = Die(rand(rng, 4:20))

# output

```

`Die`의 스칼라 및 배열 메서드가 이제 예상대로 작동합니다:

```jldoctest Die; setup = :(Random.seed!(1))
julia> rand(Die)
Die(5)

julia> rand(Xoshiro(0), Die)
Die(10)

julia> rand(Die, 3)
3-element Vector{Die}:
 Die(9)
 Die(15)
 Die(14)

julia> a = Vector{Die}(undef, 3); rand!(a)
3-element Vector{Die}:
 Die(19)
 Die(7)
 Die(17)
```

#### A simple sampler without pre-computed data

여기에서 우리는 컬렉션에 대한 샘플러를 정의합니다. 사전 계산된 데이터가 필요하지 않은 경우, 실제로는 *값에 대한 기본 대체*인 `SamplerTrivial` 샘플러로 구현할 수 있습니다.

`S` 유형의 객체에서 무작위 생성을 정의하기 위해 다음과 같은 메서드를 정의해야 합니다: `rand(rng::AbstractRNG, sp::Random.SamplerTrivial{S})`. 여기서 `sp`는 단순히 `S` 유형의 객체를 래핑하며, `sp[]`를 통해 접근할 수 있습니다. `Die` 예제를 계속해서, 이제 `rand(d::Die)`를 정의하여 `d`의 면 중 하나에 해당하는 `Int`를 생성하고자 합니다:

```jldoctest Die; setup = :(Random.seed!(1))
julia> Random.rand(rng::AbstractRNG, d::Random.SamplerTrivial{Die}) = rand(rng, 1:d[].nsides);

julia> rand(Die(4))
1

julia> rand(Die(4), 3)
3-element Vector{Any}:
 2
 3
 3
```

주어진 컬렉션 타입 `S`에 대해, 현재 `rand(::S)`가 정의되어 있다면 `eltype(S)` 타입의 객체가 생성될 것이라고 가정하고 있습니다. 마지막 예제에서는 `Vector{Any}`가 생성되었는데, 그 이유는 `eltype(Die) == Any`이기 때문입니다. 해결책은 `Base.eltype(::Type{Die}) = Int`를 정의하는 것입니다.

#### Generating values for an `AbstractFloat` type

`AbstractFloat` 유형은 특별한 경우로 처리됩니다. 기본적으로 무작위 값은 전체 유형 도메인에서 생성되지 않고, 대신 `[0,1)` 범위에서 생성됩니다. 다음 메서드는 `T <: AbstractFloat`에 대해 구현되어야 합니다: `Random.rand(::AbstractRNG, ::Random.SamplerTrivial{Random.CloseOpen01{T}})`

#### An optimized sampler with pre-computed data

이산 분포를 고려해 보십시오. 여기서 숫자 `1:n`은 합이 1이 되는 주어진 확률로 추출됩니다. 이 분포에서 많은 값을 필요로 할 때 가장 빠른 방법은 [alias table](https://en.wikipedia.org/wiki/Alias_method)를 사용하는 것입니다. 여기서는 그러한 테이블을 구축하는 알고리즘을 제공하지 않지만, 대신 `make_alias_table(probabilities)`에서 사용할 수 있다고 가정하고, `draw_number(rng, alias_table)`를 사용하여 그로부터 무작위 숫자를 추출할 수 있습니다.

분포가 다음과 같이 설명된다고 가정해 보겠습니다.

```julia
struct DiscreteDistribution{V <: AbstractVector}
    probabilities::V
end
```

그리고 우리는 필요한 값의 수에 관계없이 *항상* 별칭 테이블을 구축하고자 합니다(아래에서 이를 사용자 정의하는 방법을 배웁니다). 방법들

```julia
Random.eltype(::Type{<:DiscreteDistribution}) = Int

function Random.Sampler(::Type{<:AbstractRNG}, distribution::DiscreteDistribution, ::Repetition)
    SamplerSimple(distribution, make_alias_table(distribution.probabilities))
end
```

샘플러를 반환하도록 정의되어야 하며, 미리 계산된 데이터를 사용해야 합니다.

```julia
function rand(rng::AbstractRNG, sp::SamplerSimple{<:DiscreteDistribution})
    draw_number(rng, sp.data)
end
```

값을 그리는 데 사용됩니다.

#### Custom sampler types

`SamplerSimple` 유형은 미리 계산된 데이터와 함께 대부분의 사용 사례에 충분합니다. 그러나 사용자 정의 샘플러 유형을 사용하는 방법을 보여주기 위해 여기에서 `SamplerSimple`과 유사한 것을 구현합니다.

우리의 `Die` 예제로 돌아가면: `rand(::Die)`는 범위에서 무작위 생성을 사용하므로 이 최적화를 위한 기회가 있습니다. 우리는 우리의 사용자 정의 샘플러를 `SamplerDie`라고 부릅니다.

```julia
import Random: Sampler, rand

struct SamplerDie <: Sampler{Int} # generates values of type Int
    die::Die
    sp::Sampler{Int} # this is an abstract type, so this could be improved
end

Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerDie(die, Sampler(RNG, 1:die.nsides, r))
# the `r` parameter will be explained later on

rand(rng::AbstractRNG, sp::SamplerDie) = rand(rng, sp.sp)
```

이제 `sp = Sampler(rng, die)`로 샘플러를 얻을 수 있으며, `rng`와 관련된 모든 `rand` 호출에서 `die` 대신 `sp`를 사용할 수 있습니다. 위의 단순한 예에서 `die`는 `SamplerDie`에 저장할 필요가 없지만, 실제로는 종종 그런 경우가 많습니다.

물론, 이 패턴은 매우 빈번하게 발생하므로 위에서 사용된 헬퍼 타입인 `Random.SamplerSimple`이 제공되어 `SamplerDie`의 정의를 생략할 수 있습니다: 우리는 다음과 같이 우리의 분리를 구현할 수 있었습니다:

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerSimple(die, Sampler(RNG, 1:die.nsides, r))

rand(rng::AbstractRNG, sp::SamplerSimple{Die}) = rand(rng, sp.data)
```

여기서 `sp.data`는 `SamplerSimple` 생성자 호출의 두 번째 매개변수를 나타내며(이 경우 `Sampler(rng, 1:die.nsides, r)`와 같습니다), `Die` 객체는 `sp[]`를 통해 접근할 수 있습니다.

`SamplerDie`와 마찬가지로, 모든 사용자 정의 샘플러는 `Sampler{T}`의 하위 유형이어야 하며, 여기서 `T`는 생성된 값의 유형입니다. `SamplerSimple(x, data) isa Sampler{eltype(x)}`임을 주목하세요. 따라서 이는 `SamplerSimple`의 첫 번째 인수가 무엇일 수 있는지를 제한합니다(샘플러 메서드를 정의할 때 `x`가 단순히 전달되는 `Die` 예제와 같이 `SamplerSimple`을 사용하는 것이 권장됩니다). 유사하게, `SamplerTrivial(x) isa Sampler{eltype(x)}`입니다.

다른 경우에 사용할 수 있는 또 다른 헬퍼 유형은 `Random.SamplerTag`이며, 내부 API로 간주되며 적절한 사용 중단 없이 언제든지 중단될 수 있습니다.

#### Using distinct algorithms for scalar or array generation

일부 경우, 소수의 값만 생성할지 또는 많은 값을 생성할지를 선택하는 것이 알고리즘 선택에 영향을 미칠 수 있습니다. 이는 `Sampler` 생성자의 세 번째 매개변수로 처리됩니다. `Die`에 대해 두 개의 도우미 유형을 정의했다고 가정해 보겠습니다. `SamplerDie1`은 소수의 무작위 값을 생성하는 데 사용해야 하고, `SamplerDieMany`는 많은 값을 생성하는 데 사용해야 합니다. 이러한 유형을 다음과 같이 사용할 수 있습니다:

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{1}) = SamplerDie1(...)
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{Inf}) = SamplerDieMany(...)
```

물론, `rand`는 이러한 타입에서도 정의되어야 합니다 (즉, `rand(::AbstractRNG, ::SamplerDie1)` 및 `rand(::AbstractRNG, ::SamplerDieMany)`). 일반적으로 `SamplerTrivial` 및 `SamplerSimple`는 사용자 정의 타입이 필요하지 않은 경우 사용할 수 있습니다.

참고: `Sampler(rng, x)`는 단순히 `Sampler(rng, x, Val(Inf))`의 약어이며, `Random.Repetition`은 `Union{Val{1}, Val{Inf}}`의 별칭입니다.

### Creating new generators

API는 아직 명확하게 정의되지 않았지만, 일반적인 규칙으로:

1. 특정 RNG에 대해 필요한 경우, "기본" 유형(`isbitstype` 정수 및 부동 소수점 유형)으로 생성되는 모든 `rand` 메서드는 정의되어야 합니다;
2. 다른 문서화된 `rand` 메서드는 `AbstractRNG`를 받아들이며, (1)에서 의존하는 메서드가 구현되어 있다면 즉시 작동해야 합니다. 그러나 최적화를 위한 여지가 있다면 이 RNG에 맞게 특수화할 수 있습니다.
3. `copy`는 의사 난수 생성기(pseudo-RNG)에 대해 호출된 시점부터 원본과 정확히 동일한 난수 시퀀스를 생성하는 독립적인 복사본을 반환해야 합니다. 이것이 불가능한 경우(예: 하드웨어 기반 난수 생성기), `copy`는 구현되어서는 안 됩니다.

Concerning 1), a `rand` method may happen to work automatically, but it's not officially supported and may break without warnings in a subsequent release.

새로운 `rand` 메서드를 가상의 `MyRNG` 생성기와 값 사양 `s` (예: `s == Int` 또는 `s == 1:10`)에 대해 정의하려면, `S==typeof(s)` 또는 `S==Type{s}` (만약 `s`가 타입인 경우)와 같은 두 가지 메서드를 이전에 보았던 것처럼 정의해야 합니다:

1. `Sampler(::Type{MyRNG}, ::S, ::Repetition)`은 `SamplerS`와 같은 유형의 객체를 반환합니다.
2. `rand(rng::MyRNG, sp::SamplerS)`

`Sampler(rng::AbstractRNG, ::S, ::Repetition)`가 `Random` 모듈에 이미 정의되어 있을 수 있습니다. 이 경우, 특정 RNG 유형에 대한 생성을 전문화하려는 경우 실제로 1단계를 건너뛸 수 있지만, 해당 `SamplerS` 유형은 내부 세부 사항으로 간주되며, 경고 없이 변경될 수 있습니다.

#### Specializing array generation

일부 경우, 특정 RNG 유형에 대해 무작위 값 배열을 생성하는 것이 이전에 설명한 분리 기법을 단순히 사용하는 것보다 특수화된 방법으로 더 효율적일 수 있습니다. 예를 들어, `MersenneTwister`의 경우, 무작위 값을 배열에 원래대로 작성합니다.

`MyRNG`에 대한 이 특수화를 구현하고 `s`라는 사양에 대해 `S` 유형의 요소를 생성하기 위해 다음과 같은 메서드를 정의할 수 있습니다: `rand!(rng::MyRNG, a::AbstractArray{S}, ::SamplerS)`, 여기서 `SamplerS`는 `Sampler(MyRNG, s, Val(Inf))`에 의해 반환되는 샘플러의 유형입니다. `AbstractArray` 대신, 기능을 `Array{S}`와 같은 하위 유형에 대해서만 구현할 수 있습니다. `rand`의 비변이 배열 메서드는 내부적으로 이 특수화를 자동으로 호출합니다.

```@meta
DocTestSetup = nothing
```

# Reproducibility

주어진 시드로 초기화된 RNG 매개변수를 사용하면 프로그램을 여러 번 실행할 때 동일한 의사 난수 시퀀스를 재현할 수 있습니다. 그러나 Julia의 소규모 릴리스(예: 1.3에서 1.4로)에서는 특정 시드에서 생성된 의사 난수 시퀀스가 *변경될 수* 있습니다. 특히 `MersenneTwister`가 사용되는 경우에 그렇습니다. (저수준 함수인 [`rand`](@ref)가 생성하는 시퀀스가 변경되지 않더라도, 고수준 함수인 [`randsubseq`](@ref)의 출력은 알고리즘 업데이트로 인해 변경될 수 있습니다.) 이유: 의사 난수 스트림이 절대 변경되지 않도록 보장하는 것은 많은 알고리즘 개선을 금지합니다.

무작위 데이터의 정확한 재현성을 보장해야 하는 경우, *데이터를 저장*하는 것이 좋습니다(예: 과학 출판물의 보조 첨부 파일로). (물론 특정 Julia 버전과 패키지 매니페스트를 지정할 수도 있으며, 특히 비트 재현성이 필요한 경우에는 더욱 그렇습니다.)

특정 "무작위" 데이터에 의존하는 소프트웨어 테스트는 일반적으로 데이터를 저장하거나 테스트 코드에 포함시키거나 [StableRNGs.jl](https://github.com/JuliaRandom/StableRNGs.jl)와 같은 서드파티 패키지를 사용해야 합니다. 반면, 대부분의 무작위 데이터에 대해 통과해야 하는 테스트(예: 무작위 행렬 `A = randn(n,n)`에 대해 `A \ (A*x) ≈ x` 테스트)는 고정된 시드를 가진 RNG를 사용하여 테스트를 여러 번 실행해도 매우 불확실한 데이터(예: 극도로 잘못된 조건의 행렬)로 인해 실패하지 않도록 할 수 있습니다.

무작위 샘플이 추출되는 통계적 *분포*는 모든 사소한 줄리아 릴리스에서 동일할 것이라고 보장됩니다.
