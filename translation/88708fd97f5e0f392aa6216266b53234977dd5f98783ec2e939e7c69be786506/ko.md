# Base.Cartesian

(비수출) 카르테시안 모듈은 다차원 알고리즘 작성을 용이하게 하는 매크로를 제공합니다. 대부분의 경우 [straightforward techniques](https://julialang.org/blog/2016/02/iteration)을 사용하여 이러한 알고리즘을 작성할 수 있지만, `Base.Cartesian`이 여전히 유용하거나 필요한 몇 가지 경우가 있습니다.

## Principles of usage

사용의 간단한 예는:

```julia
@nloops 3 i A begin
    s += @nref 3 A i
end
```

어떤 코드를 생성하는지:

```julia
for i_3 = axes(A, 3)
    for i_2 = axes(A, 2)
        for i_1 = axes(A, 1)
            s += A[i_1, i_2, i_3]
        end
    end
end
```

일반적으로 Cartesian은 이 예제의 중첩 루프와 같은 반복 요소를 포함하는 일반 코드를 작성할 수 있게 해줍니다. 다른 응용 프로그램으로는 반복 표현식(예: 루프 전개)이나 "스플랫" 구성(`i...`)을 사용하지 않고 가변 개수의 인수를 가진 함수 호출을 생성하는 것이 포함됩니다.

## Basic syntax

`@nloops`의 (기본) 구문은 다음과 같습니다:

  * 첫 번째 인수는 루프의 수를 지정하는 정수(*변수가 아님)여야 합니다.
  * 두 번째 인자는 반복자 변수에 사용되는 기호 접두사입니다. 여기서는 `i`를 사용했으며, 변수 `i_1, i_2, i_3`가 생성되었습니다.
  * 세 번째 인자는 각 반복자 변수의 범위를 지정합니다. 여기에서 변수를 (기호) 사용하면 `axes(A, dim)`으로 간주됩니다. 더 유연하게, 아래에 설명된 익명 함수 표현식 구문을 사용할 수 있습니다.
  * 루프의 마지막 인자는 루프의 본문입니다. 여기서 `begin...end` 사이에 나타나는 것이 그것입니다.

`@nloops`의 추가 기능은 [reference section](@ref dev-cartesian-reference)에 설명되어 있습니다.

`@nref`는 비슷한 패턴을 따르며, `@nref 3 A i`에서 `A[i_1,i_2,i_3]`를 생성합니다. 일반적인 관행은 왼쪽에서 오른쪽으로 읽는 것이므로 `@nloops`는 `@nloops 3 i A expr`입니다(예: `for i_2 = axes(A, 2)`에서 `i_2`는 왼쪽에 있고 범위는 오른쪽에 있음). 반면 `@nref`는 `@nref 3 A i`입니다(예: `A[i_1,i_2,i_3]`에서 배열이 먼저 나옵니다).

Cartesian으로 코드를 개발하는 경우, `@macroexpand`를 사용하여 생성된 코드를 검사하면 디버깅이 더 쉬워질 수 있습니다:

```@meta
DocTestSetup = quote
    import Base.Cartesian: @nref
end
```

```jldoctest
julia> @macroexpand @nref 2 A i
:(A[i_1, i_2])
```

```@meta
DocTestSetup = nothing
```

### Supplying the number of expressions

이 두 매크로의 첫 번째 인수는 표현식의 수로, 정수여야 합니다. 여러 차원에서 작동할 의도로 함수를 작성할 때, 이것을 하드코딩하는 것은 원하지 않을 수 있습니다. 권장되는 접근 방식은 `@generated function`을 사용하는 것입니다. 다음은 예시입니다:

```julia
@generated function mysum(A::Array{T,N}) where {T,N}
    quote
        s = zero(T)
        @nloops $N i A begin
            s += @nref $N A i
        end
        s
    end
end
```

자연스럽게, `quote` 블록 전에 표현식을 준비하거나 계산을 수행할 수도 있습니다.

### Anonymous-function expressions as macro arguments

`Cartesian`에서 가장 강력한 기능 중 하나는 파싱 시간에 평가되는 익명 함수 표현식을 제공할 수 있는 능력입니다. 간단한 예를 살펴보겠습니다:

```julia
@nexprs 2 j->(i_j = 1)
```

`@nexprs`는 패턴을 따르는 `n` 개의 표현식을 생성합니다. 이 코드는 다음과 같은 문장을 생성합니다:

```julia
i_1 = 1
i_2 = 1
```

각 생성된 문장에서 "고립된" `j` (익명 함수의 변수)는 `1:2` 범위의 값으로 대체됩니다. 일반적으로 Cartesian은 LaTeX와 유사한 구문을 사용합니다. 이를 통해 인덱스 `j`에 대해 수학적 연산을 수행할 수 있습니다. 다음은 배열의 보폭을 계산하는 예입니다:

```julia
s_1 = 1
@nexprs 3 j->(s_{j+1} = s_j * size(A, j))
```

표현을 생성할 것입니다.

```julia
s_1 = 1
s_2 = s_1 * size(A, 1)
s_3 = s_2 * size(A, 2)
s_4 = s_3 * size(A, 3)
```

익명 함수 표현식은 실제로 많은 용도가 있습니다.

#### [Macro reference](@id dev-cartesian-reference)

```@docs
Base.Cartesian.@nloops
Base.Cartesian.@nref
Base.Cartesian.@nextract
Base.Cartesian.@nexprs
Base.Cartesian.@ncall
Base.Cartesian.@ncallkw
Base.Cartesian.@ntuple
Base.Cartesian.@nall
Base.Cartesian.@nany
Base.Cartesian.@nif
```
