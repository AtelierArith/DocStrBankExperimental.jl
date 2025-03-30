# [Types](@id man-types)

타입 시스템은 전통적으로 두 가지 매우 다른 진영으로 나뉘어 왔습니다: 정적 타입 시스템에서는 모든 프로그램 표현식이 프로그램 실행 전에 계산 가능한 타입을 가져야 하고, 동적 타입 시스템에서는 프로그램이 조작하는 실제 값이 사용 가능해질 때까지 타입에 대한 정보가 없습니다. 객체 지향은 정적 타입 언어에서 코드가 컴파일 시간에 값의 정확한 타입을 알지 못한 채로 작성될 수 있도록 하여 어느 정도의 유연성을 허용합니다. 서로 다른 타입에서 작동할 수 있는 코드를 작성하는 능력을 다형성이라고 합니다. 고전적인 동적 타입 언어의 모든 코드는 다형적입니다: 타입을 명시적으로 확인하거나 객체가 런타임에 작업을 지원하지 않을 때만 값의 타입이 제한됩니다.

줄리아의 타입 시스템은 동적이지만, 특정 값이 특정 타입임을 나타낼 수 있게 함으로써 정적 타입 시스템의 몇 가지 장점을 얻습니다. 이는 효율적인 코드를 생성하는 데 큰 도움이 될 수 있지만, 더 중요한 것은 함수 인수의 타입에 따라 메서드 디스패치가 언어와 깊게 통합될 수 있게 한다는 점입니다. 메서드 디스패치는 [Methods](@ref)에서 자세히 탐구되지만, 여기서 제시된 타입 시스템에 뿌리를 두고 있습니다.

Julia에서 타입이 생략될 때의 기본 동작은 값이 어떤 타입이든 허용하는 것입니다. 따라서 타입을 명시적으로 사용하지 않고도 유용한 Julia 함수를 많이 작성할 수 있습니다. 그러나 추가적인 표현력이 필요할 때는 이전의 "타입이 없는" 코드에 명시적인 타입 주석을 점진적으로 도입하는 것이 쉽습니다. 주석을 추가하는 것은 세 가지 주요 목적을 가지고 있습니다: Julia의 강력한 다중 분기 메커니즘을 활용하고, 인간의 가독성을 향상시키며, 프로그래머의 오류를 잡는 것입니다.

줄리아를 [type systems](https://en.wikipedia.org/wiki/Type_system)의 용어로 설명하자면, 그것은: 동적, 명시적 및 매개변수적입니다. 제네릭 타입은 매개변수화할 수 있으며, 타입 간의 계층적 관계는 [explicitly declared](https://en.wikipedia.org/wiki/Nominal_type_system)로, [implied by compatible structure](https://en.wikipedia.org/wiki/Structural_type_system)가 아닙니다. 줄리아의 타입 시스템에서 특히 독특한 특징은 구체적인 타입이 서로 서브타입이 될 수 없다는 것입니다: 모든 구체적인 타입은 최종적이며, 그들의 수퍼타입으로는 추상 타입만 가질 수 있습니다. 처음에는 이것이 지나치게 제한적으로 보일 수 있지만, 놀랍도록 적은 단점으로 많은 유익한 결과를 가져옵니다. 행동을 상속할 수 있는 것이 구조를 상속할 수 있는 것보다 훨씬 더 중요하다는 것이 밝혀졌으며, 둘 다 상속하는 것은 전통적인 객체 지향 언어에서 상당한 어려움을 초래합니다. 줄리아의 타입 시스템에서 미리 언급해야 할 다른 고급 측면은 다음과 같습니다:

  * 객체와 비객체 값 사이에는 구분이 없습니다: 줄리아의 모든 값은 진정한 객체이며, 단일의 완전히 연결된 타입 그래프에 속하는 타입을 가지고 있으며, 이 그래프의 모든 노드는 타입으로서 동등하게 일급입니다.
  * "컴파일 타임 타입"이라는 의미 있는 개념은 존재하지 않습니다: 값이 가지는 유일한 타입은 프로그램이 실행될 때의 실제 타입입니다. 이는 정적 컴파일과 다형성이 결합되어 이 구분이 중요해지는 객체 지향 언어에서 "런타임 타입"이라고 불립니다.
  * 값만이 유형을 가지며, 변수는 단순히 값에 바인딩된 이름입니다. 간단히 말해 "변수의 유형"이라고 할 수 있지만, 이는 변수이 참조하는 값의 유형을 의미합니다.
  * 추상형과 구체형 모두 다른 유형으로 매개변수화될 수 있습니다. 또한 기호로 매개변수화되거나, [`isbits`](@ref)가 true를 반환하는 모든 유형의 값으로 매개변수화될 수 있습니다(본질적으로, C 유형처럼 저장된 숫자 및 불리언과 같은 것들 또는 다른 객체에 대한 포인터가 없는 `struct`와 같은 것들), 그리고 그 튜플로도 매개변수화될 수 있습니다. 유형 매개변수는 참조되거나 제한될 필요가 없을 때 생략할 수 있습니다.

줄리아의 타입 시스템은 강력하고 표현력이 뛰어나도록 설계되었지만, 명확하고 직관적이며 방해가 되지 않도록 되어 있습니다. 많은 줄리아 프로그래머들은 타입을 명시적으로 사용하는 코드를 작성할 필요성을 느끼지 못할 수도 있습니다. 그러나 일부 종류의 프로그래밍은 선언된 타입을 사용함으로써 더 명확하고, 간단하며, 빠르고, 더 견고해집니다.

## Type Declarations

`::` 연산자는 프로그램의 표현식과 변수에 타입 주석을 첨부하는 데 사용할 수 있습니다. 이를 수행하는 주된 두 가지 이유는 다음과 같습니다:

1. 프로그램이 예상대로 작동하는지 확인하는 데 도움이 되는 주장을 위해, 그리고
2. 컴파일러에 추가적인 타입 정보를 제공하여, 이로 인해 일부 경우 성능을 향상시킬 수 있습니다.

표현식의 값을 계산하는 데 추가될 때, `::` 연산자는 "인스턴스이다"로 읽힙니다. 이는 왼쪽의 표현식 값이 오른쪽의 타입의 인스턴스임을 주장하기 위해 어디에서나 사용할 수 있습니다. 오른쪽의 타입이 구체적일 때, 왼쪽의 값은 그 타입을 구현해야 합니다. 모든 구체적 타입은 최종적이므로, 어떤 구현도 다른 구현의 하위 타입이 될 수 없음을 기억하십시오. 타입이 추상적일 경우, 값이 추상 타입의 하위 타입인 구체적 타입에 의해 구현되기만 하면 충분합니다. 타입 주장이 참이 아닐 경우 예외가 발생하며, 그렇지 않으면 왼쪽 값이 반환됩니다:

```jldoctest
julia> (1+2)::AbstractFloat
ERROR: TypeError: in typeassert, expected AbstractFloat, got a value of type Int64

julia> (1+2)::Int
3
```

이것은 타입 단언을 어떤 표현식에든 제자리에서 첨부할 수 있게 해줍니다.

변수의 왼쪽에 할당할 때 또는 `local` 선언의 일부로 사용될 때, `::` 연산자는 약간 다른 의미를 가집니다: 이는 변수가 항상 지정된 유형을 가지도록 선언하며, C와 같은 정적 타입 언어의 타입 선언과 유사합니다. 변수에 할당된 모든 값은 [`convert`](@ref)를 사용하여 선언된 유형으로 변환됩니다:

```jldoctest
julia> function foo()
           x::Int8 = 100
           x
       end
foo (generic function with 1 method)

julia> x = foo()
100

julia> typeof(x)
Int8
```

이 기능은 변수에 대한 할당 중 하나가 예기치 않게 유형을 변경할 경우 발생할 수 있는 성능 "함정"을 피하는 데 유용합니다.

이 "선언" 동작은 특정 맥락에서만 발생합니다:

```julia
local x::Int8  # in a local declaration
x::Int8 = 10   # as the left-hand side of an assignment
```

그리고 선언 이전에도 현재 범위 전체에 적용됩니다.

Julia 1.8부터, 타입 선언이 전역 범위에서 사용할 수 있게 되었습니다. 즉, 타입 주석을 전역 변수에 추가하여 접근할 때 타입 안정성을 높일 수 있습니다.

```julia
julia> x::Int = 10
10

julia> x = 3.5
ERROR: InexactError: Int64(3.5)

julia> function foo(y)
           global x = 15.8    # throws an error when foo is called
           return x + y
       end
foo (generic function with 1 method)

julia> foo(10)
ERROR: InexactError: Int64(15.8)
```

선언은 함수 정의에 첨부될 수도 있습니다:

```julia
function sinc(x)::Float64
    if x == 0
        return 1
    end
    return sin(pi*x)/(pi*x)
end
```

이 함수에서 반환하는 것은 선언된 타입의 변수에 할당하는 것과 동일하게 동작합니다: 값은 항상 `Float64`로 변환됩니다.

## [Abstract Types](@id man-abstract-types)

추상 타입은 인스턴스화될 수 없으며, 타입 그래프의 노드로만 사용되어 관련된 구체적 타입의 집합을 설명합니다: 그들의 자손인 구체적 타입들입니다. 우리는 추상 타입으로 시작합니다. 비록 인스턴스화가 불가능하지만, 이들은 타입 시스템의 중추 역할을 합니다: 이들은 줄리아의 타입 시스템을 단순한 객체 구현의 집합 이상으로 만드는 개념적 계층을 형성합니다.

[Integers and Floating-Point Numbers](@ref)에서 우리는 다양한 구체적인 숫자 값의 유형을 소개했습니다: [`Int8`](@ref), [`UInt8`](@ref), [`Int16`](@ref), [`UInt16`](@ref), [`Int32`](@ref), [`UInt32`](@ref), [`Int64`](@ref), [`UInt64`](@ref), [`Int128`](@ref), [`UInt128`](@ref), [`Float16`](@ref), [`Float32`](@ref), 및 [`Float64`](@ref). 이들은 서로 다른 표현 크기를 가지고 있지만, `Int8`, `Int16`, `Int32`, `Int64` 및 `Int128`은 모두 부호 있는 정수 유형이라는 공통점이 있습니다. 마찬가지로 `UInt8`, `UInt16`, `UInt32`, `UInt64` 및 `UInt128`은 모두 부호 없는 정수 유형이며, `Float16`, `Float32` 및 `Float64`는 정수가 아닌 부동 소수점 유형이라는 점에서 다릅니다. 코드 조각이 의미를 가지려면, 예를 들어, 그 인수가 어떤 종류의 정수여야만 하는 경우가 흔하지만, 특정 *종류*의 정수에 의존하지는 않습니다. 예를 들어, 최대 공약수 알고리즘은 모든 종류의 정수에 대해 작동하지만, 부동 소수점 숫자에 대해서는 작동하지 않습니다. 추상 유형은 유형의 계층 구조를 구성할 수 있게 하여, 구체적인 유형이 적합할 수 있는 맥락을 제공합니다. 이를 통해 예를 들어, 특정 정수 유형에 제한하지 않고 정수인 모든 유형에 쉽게 프로그래밍할 수 있습니다.

추상 타입은 [`abstract type`](@ref) 키워드를 사용하여 선언됩니다. 추상 타입을 선언하는 일반적인 구문은 다음과 같습니다:

```
abstract type «name» end
abstract type «name» <: «supertype» end
```

`abstract type` 키워드는 `«name»`으로 주어진 새로운 추상 타입을 도입합니다. 이 이름은 선택적으로 [`<:`](@ref)와 이미 존재하는 타입이 뒤따를 수 있으며, 이는 새로 선언된 추상 타입이 이 "부모" 타입의 하위 타입임을 나타냅니다.

슈퍼타입이 주어지지 않으면 기본 슈퍼타입은 `Any`입니다. `Any`는 모든 객체가 인스턴스인 미리 정의된 추상 타입이며 모든 타입이 서브타입인 타입입니다. 타입 이론에서 `Any`는 타입 그래프의 정점에 있기 때문에 일반적으로 "top"이라고 불립니다. Julia는 또한 타입 그래프의 최하단에 있는 미리 정의된 추상 "bottom" 타입을 가지고 있으며, 이는 `Union{}`로 표기됩니다. 이는 `Any`의 정반대입니다: 어떤 객체도 `Union{}`의 인스턴스가 아니며 모든 타입이 `Union{}`의 슈퍼타입입니다.

줄리아의 수치 계층을 구성하는 몇 가지 추상 유형을 살펴보겠습니다:

```julia
abstract type Number end
abstract type Real          <: Number end
abstract type AbstractFloat <: Real end
abstract type Integer       <: Real end
abstract type Signed        <: Integer end
abstract type Unsigned      <: Integer end
```

[`Number`](@ref) 유형은 `Any`의 직접 자식 유형이며, [`Real`](@ref)는 그 자식입니다. 차례로, `Real`은 두 개의 자식을 가지고 있습니다(더 많은 자식이 있지만 여기서는 두 개만 표시됩니다; 나중에 다른 자식에 대해 다룰 것입니다): [`Integer`](@ref)와 [`AbstractFloat`](@ref)로, 세상을 정수의 표현과 실수의 표현으로 나누고 있습니다. 실수의 표현에는 부동 소수점 유형이 포함되지만, 유리수와 같은 다른 유형도 포함됩니다. `AbstractFloat`는 실수의 부동 소수점 표현만 포함합니다. 정수는 [`Signed`](@ref)와 [`Unsigned`](@ref) 종류로 더 세분화됩니다.

`<:` 연산자는 일반적으로 "하위 유형이다"라는 의미이며, 위와 같은 선언에서 사용될 때, 오른쪽 타입을 새로 선언된 타입의 즉각적인 상위 타입으로 선언합니다. 또한 표현식에서 하위 유형 연산자로 사용될 수 있으며, 이 경우 왼쪽 피연산자가 오른쪽 피연산자의 하위 유형일 때 `true`를 반환합니다:

```jldoctest
julia> Integer <: Number
true

julia> Integer <: AbstractFloat
false
```

추상 타입의 중요한 용도 중 하나는 구체적인 타입에 대한 기본 구현을 제공하는 것입니다. 간단한 예를 들어보면:

```julia
function myplus(x,y)
    x+y
end
```

첫 번째로 주목할 점은 위의 인수 선언이 `x::Any`와 `y::Any`와 동등하다는 것입니다. 이 함수가 `myplus(2,5)`와 같이 호출되면, 디스패처는 주어진 인수와 일치하는 가장 구체적인 `myplus` 메서드를 선택합니다. (여러 디스패치에 대한 자세한 내용은 [Methods](@ref)을 참조하세요.)

위의 방법보다 더 구체적인 방법이 발견되지 않는다고 가정할 때, Julia는 다음으로 위에서 주어진 일반 함수를 기반으로 두 개의 `Int` 인수에 대해 특별히 `myplus`라는 메서드를 내부적으로 정의하고 컴파일합니다. 즉, 암묵적으로 정의하고 컴파일합니다:

```julia
function myplus(x::Int,y::Int)
    x+y
end
```

마지막으로, 이 특정 메서드를 호출합니다.

따라서 추상 타입은 프로그래머가 나중에 많은 구체적 타입의 조합에 의해 기본 메서드로 사용될 수 있는 일반 함수를 작성할 수 있게 해줍니다. 다중 디스패치를 통해 프로그래머는 기본 메서드 또는 더 구체적인 메서드가 사용될지에 대한 완전한 제어권을 가집니다.

중요한 점은 프로그래머가 추상 타입의 인수를 가진 함수에 의존할 경우 성능 손실이 없다는 것입니다. 이는 호출되는 구체적인 인수 타입의 각 튜플에 대해 재컴파일되기 때문입니다. (그러나 추상 타입의 컨테이너인 함수 인수의 경우 성능 문제가 있을 수 있습니다; [Performance Tips](@ref man-performance-abstract-container)를 참조하십시오.)

## Primitive Types

!!! warning
    기존의 원시 타입을 새로운 복합 타입으로 감싸는 것이 자신의 원시 타입을 정의하는 것보다 거의 항상 바람직합니다.

    이 기능은 Julia가 LLVM이 지원하는 표준 원시 타입을 부트스트랩할 수 있도록 존재합니다. 일단 정의되면, 더 많은 것을 정의할 이유는 거의 없습니다.


원시 타입은 데이터가 일반적인 비트로 구성된 구체적인 타입입니다. 원시 타입의 고전적인 예로는 정수와 부동 소수점 값이 있습니다. 대부분의 언어와 달리, 줄리아는 고정된 내장 타입 집합만 제공하는 대신 사용자가 자신의 원시 타입을 선언할 수 있도록 허용합니다. 사실, 표준 원시 타입은 모두 언어 자체에서 정의됩니다:

```julia
primitive type Float16 <: AbstractFloat 16 end
primitive type Float32 <: AbstractFloat 32 end
primitive type Float64 <: AbstractFloat 64 end

primitive type Bool <: Integer 8 end
primitive type Char <: AbstractChar 32 end

primitive type Int8    <: Signed   8 end
primitive type UInt8   <: Unsigned 8 end
primitive type Int16   <: Signed   16 end
primitive type UInt16  <: Unsigned 16 end
primitive type Int32   <: Signed   32 end
primitive type UInt32  <: Unsigned 32 end
primitive type Int64   <: Signed   64 end
primitive type UInt64  <: Unsigned 64 end
primitive type Int128  <: Signed   128 end
primitive type UInt128 <: Unsigned 128 end
```

원시 타입을 선언하는 일반적인 구문은 다음과 같습니다:

```
primitive type «name» «bits» end
primitive type «name» <: «supertype» «bits» end
```

비트 수는 해당 타입이 요구하는 저장 용량을 나타내며, 이름은 새로운 타입에 이름을 부여합니다. 원시 타입은 선택적으로 어떤 슈퍼타입의 서브타입으로 선언될 수 있습니다. 슈퍼타입이 생략되면, 타입은 기본적으로 `Any`를 즉각적인 슈퍼타입으로 가집니다. 따라서 위의 [`Bool`](@ref) 선언은 불리언 값이 저장하는 데 여덟 비트를 필요로 하며, [`Integer`](@ref)를 즉각적인 슈퍼타입으로 가진다는 것을 의미합니다. 현재 지원되는 크기는 8비트의 배수만 가능하며, 위에서 사용된 것 외의 크기로는 LLVM 버그를 경험할 가능성이 높습니다. 따라서 불리언 값은 실제로는 단일 비트만 필요하지만, 여덟 비트보다 작게 선언될 수 없습니다.

타입 [`Bool`](@ref), [`Int8`](@ref) 및 [`UInt8`](@ref)는 모두 동일한 표현을 가지고 있습니다: 이들은 8비트 메모리 청크입니다. 그러나 줄리아의 타입 시스템은 명명적(nominative)이기 때문에, 동일한 구조를 가지고 있음에도 불구하고 서로 교환할 수 없습니다. 이들 사이의 근본적인 차이점은 서로 다른 슈퍼타입을 가지고 있다는 것입니다: `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566`의 직접 슈퍼타입은 [`Integer`](@ref), `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566`의 것은 [`Signed`](@ref), 그리고 `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566`의 것은 [`Unsigned`](@ref)입니다. `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566`, `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566`, 및 `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566` 간의 다른 모든 차이점은 동작의 문제입니다 – 이러한 타입의 객체가 인수로 주어졌을 때 함수가 작동하도록 정의된 방식입니다. 이것이 명명적 타입 시스템이 필요한 이유입니다: 구조가 타입을 결정하고, 그 타입이 행동을 지시한다면, `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566`가 `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` 또는 `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566`와 다르게 행동하도록 만드는 것은 불가능할 것입니다.

## Composite Types

[Composite types](https://en.wikipedia.org/wiki/Composite_data_type)는 다양한 언어에서 레코드, 구조체 또는 객체라고 불립니다. 복합 유형은 이름이 지정된 필드의 모음으로, 이의 인스턴스는 단일 값으로 취급될 수 있습니다. 많은 언어에서 복합 유형은 사용자 정의 유형의 유일한 종류이며, 이는 줄리아에서 가장 일반적으로 사용되는 사용자 정의 유형입니다.

주류 객체 지향 언어인 C++, Java, Python 및 Ruby에서는 복합 유형에도 이름이 있는 함수가 연결되어 있으며, 이 조합을 "객체"라고 합니다. Ruby나 Smalltalk과 같은 순수 객체 지향 언어에서는 모든 값이 객체이며, 복합체인지 여부에 관계없이 모두 객체입니다. C++와 Java와 같은 덜 순수한 객체 지향 언어에서는 정수 및 부동 소수점 값과 같은 일부 값은 객체가 아니지만, 사용자 정의 복합 유형의 인스턴스는 관련 메서드를 가진 진정한 객체입니다. Julia에서는 모든 값이 객체이지만, 함수는 작동하는 객체와 함께 묶이지 않습니다. 이는 Julia가 여러 배치를 통해 사용할 함수의 메서드를 선택하기 때문에 필요합니다. 즉, 메서드를 선택할 때 함수의 모든 인수의 유형이 고려되며, 첫 번째 인수만 고려되지 않습니다(메서드 및 배치에 대한 자세한 내용은 [Methods](@ref)을 참조하십시오). 따라서 함수가 첫 번째 인수에만 "속하는" 것은 부적절합니다. 메서드를 함수 객체로 구성하고 각 객체 "내부"에 이름이 있는 메서드 집합을 두는 것보다 이러한 방식이 언어 설계의 매우 유익한 측면이 됩니다.

복합 유형은 [`struct`](@ref) 키워드로 도입되며, 그 뒤에 필드 이름 블록이 옵니다. 이 필드 이름은 선택적으로 `::` 연산자를 사용하여 유형으로 주석을 달 수 있습니다:

```jldoctest footype
julia> struct Foo
           bar
           baz::Int
           qux::Float64
       end
```

타입 주석이 없는 필드는 기본적으로 `Any`로 설정되며, 따라서 어떤 타입의 값도 가질 수 있습니다.

새로운 `Foo` 유형의 객체는 `Foo` 유형 객체를 함수처럼 적용하여 해당 필드의 값에 대해 생성됩니다:

```jldoctest footype
julia> foo = Foo("Hello, world.", 23, 1.5)
Foo("Hello, world.", 23, 1.5)

julia> typeof(foo)
Foo
```

타입이 함수처럼 적용될 때 이를 *생성자*라고 합니다. 두 개의 생성자가 자동으로 생성됩니다(이를 *기본 생성자*라고 합니다). 하나는 모든 인수를 받아들이고 [`convert`](@ref)를 호출하여 이를 필드의 타입으로 변환하며, 다른 하나는 필드 타입과 정확히 일치하는 인수를 받아들입니다. 이 두 생성자가 모두 생성되는 이유는 새로운 정의를 추가할 때 기본 생성자를 무심코 대체하지 않도록 하기 위함입니다.

`bar` 필드는 타입에 제약이 없으므로 어떤 값이든 가능합니다. 그러나 `baz`의 값은 `Int`로 변환 가능해야 합니다:

```jldoctest footype
julia> Foo((), 23.5, 1)
ERROR: InexactError: Int64(23.5)
Stacktrace:
[...]
```

[`fieldnames`](@ref) 함수를 사용하여 필드 이름 목록을 찾을 수 있습니다.

```jldoctest footype
julia> fieldnames(Foo)
(:bar, :baz, :qux)
```

복합 객체의 필드 값에 접근하려면 전통적인 `foo.bar` 표기법을 사용합니다:

```jldoctest footype
julia> foo.bar
"Hello, world."

julia> foo.baz
23

julia> foo.qux
1.5
```

`struct`로 선언된 복합 객체는 *불변*입니다; 생성 후 수정할 수 없습니다. 처음에는 이상하게 보일 수 있지만, 여러 가지 장점이 있습니다:

  * 더 효율적일 수 있습니다. 일부 구조체는 배열에 효율적으로 패킹될 수 있으며, 경우에 따라 컴파일러는 불변 객체를 완전히 할당하지 않을 수 있습니다.
  * 타입의 생성자가 제공하는 불변성을 위반하는 것은 불가능하다.
  * 불변 객체를 사용하는 코드는 이해하기 더 쉬울 수 있습니다.

불변 객체는 배열과 같은 가변 객체를 필드로 포함할 수 있습니다. 포함된 객체는 여전히 가변적이며, 불변 객체 자체의 필드만 다른 객체를 가리키도록 변경할 수 없습니다.

필요한 경우, 변경 가능한 복합 객체는 키워드 [`mutable struct`](@ref)로 선언할 수 있으며, 이는 다음 섹션에서 논의될 것입니다.

모든 불변 구조체의 필드가 구별할 수 없을 경우(`===`), 해당 필드를 포함하는 두 개의 불변 값도 구별할 수 없습니다:

```jldoctest
julia> struct X
           a::Int
           b::Float64
       end

julia> X(1, 2) === X(1, 2)
true
```

복합 유형의 인스턴스가 어떻게 생성되는지에 대해 더 많은 이야기가 있지만, 그 논의는 [Parametric Types](@ref)와 [Methods](@ref) 모두에 의존하며, 충분히 중요하여 별도의 섹션에서 다루어져야 합니다: [Constructors](@ref man-constructors).

많은 사용자 정의 유형 `X`에 대해, 인스턴스가 [broadcasting](@ref Broadcasting)의 0차원 "스칼라"로 작동하도록 [`Base.broadcastable(x::X) = Ref(x)`](@ref man-interfaces-broadcasting) 메서드를 정의하고 싶을 수 있습니다.

## Mutable Composite Types

`mutable struct`로 선언된 복합 유형은 `struct` 대신에 인스턴스를 수정할 수 있습니다:

```jldoctest bartype
julia> mutable struct Bar
           baz
           qux::Float64
       end

julia> bar = Bar("Hello", 1.5);

julia> bar.qux = 2.0
2.0

julia> bar.baz = 1//2
1//2
```

필드와 사용자 간의 추가 인터페이스는 [Instance Properties](@ref man-instance-properties)를 통해 제공될 수 있습니다. 이는 `bar.baz` 표기법을 사용하여 접근하고 수정할 수 있는 것에 대한 더 많은 제어를 부여합니다.

변이를 지원하기 위해 이러한 객체는 일반적으로 힙에 할당되며 안정적인 메모리 주소를 가집니다. 가변 객체는 시간이 지남에 따라 서로 다른 값을 가질 수 있는 작은 컨테이너와 같으며, 따라서 주소로만 신뢰할 수 있게 식별할 수 있습니다. 반면, 불변 유형의 인스턴스는 특정 필드 값과 연결되어 있으며 – 필드 값만으로 객체에 대한 모든 정보를 알 수 있습니다. 유형을 가변으로 만들지 여부를 결정할 때, 동일한 필드 값을 가진 두 인스턴스가 동일하다고 간주될 것인지, 아니면 시간이 지남에 따라 독립적으로 변경될 필요가 있는지를 물어보세요. 동일하다고 간주된다면, 해당 유형은 아마도 불변이어야 합니다.

요약하자면, 불변성을 정의하는 두 가지 필수 속성이 줄리아에서 있습니다:

  * 변경할 수 없는 타입의 값을 수정하는 것은 허용되지 않습니다.

      * 비트 유형에 대해 이는 설정된 값의 비트 패턴이 한 번 설정되면 절대 변경되지 않으며, 그 값이 비트 유형의 정체성이라는 것을 의미합니다.
      * 복합 유형의 경우, 이는 필드의 값의 정체성이 결코 변경되지 않음을 의미합니다. 필드가 비트 유형인 경우, 이는 해당 비트가 결코 변경되지 않음을 의미하며, 배열과 같은 가변 유형의 값을 가진 필드의 경우, 해당 필드는 가변 값의 내용이 수정될 수 있음에도 불구하고 항상 동일한 가변 값을 참조합니다.
  * 불변 타입의 객체는 불변성 덕분에 원래 객체와 복사본을 프로그래밍적으로 구별할 수 없기 때문에 컴파일러에 의해 자유롭게 복사될 수 있습니다.

      * 특히, 이는 정수와 부동 소수점과 같은 충분히 작은 불변 값들이 일반적으로 레지스터(또는 스택 할당)를 통해 함수에 전달된다는 것을 의미합니다.
      * 변경 가능한 값은 반면에 힙에 할당되며, 컴파일러가 이것이 발생하지 않는다는 것을 확실히 알 수 없는 경우를 제외하고는 힙에 할당된 값에 대한 포인터로 함수에 전달됩니다.

일반적으로 변경 가능한 구조체의 하나 이상의 필드가 불변임이 알려진 경우, 아래와 같이 `const`를 사용하여 이러한 필드를 선언할 수 있습니다. 이는 불변 구조체의 일부 최적화를 가능하게 하며, `const`로 표시된 특정 필드에 대한 불변성을 강제하는 데 사용할 수 있습니다.

!!! compat "Julia 1.8"
    `const` 가 변경 가능한 구조체의 필드를 주석 처리하는 데는 최소한 Julia 1.8이 필요합니다.


```jldoctest baztype
julia> mutable struct Baz
           a::Int
           const b::Float64
       end

julia> baz = Baz(1, 1.5);

julia> baz.a = 2
2

julia> baz.b = 2.0
ERROR: setfield!: const field .b of type Baz cannot be changed
[...]
```

## [Declared Types](@id man-declared-types)

이전 섹션에서 논의된 세 가지 유형(추상, 원시, 복합)은 실제로 모두 밀접하게 관련되어 있습니다. 이들은 동일한 주요 속성을 공유합니다:

  * 그들은 명시적으로 선언되어 있습니다.
  * 그들은 이름이 있다.
  * 그들은 명시적으로 수퍼타입을 선언했습니다.
  * 그들은 매개변수를 가질 수 있습니다.

이러한 공유 속성 때문에, 이러한 유형은 내부적으로 동일한 개념인 `DataType`의 인스턴스로 표현됩니다. 이는 이러한 유형 중 어떤 것이든 해당하는 유형입니다:

```jldoctest
julia> typeof(Real)
DataType

julia> typeof(Int)
DataType
```

`DataType`는 추상적이거나 구체적일 수 있습니다. 구체적일 경우, 지정된 크기, 저장 레이아웃 및 (선택적으로) 필드 이름이 있습니다. 따라서 원시 타입은 크기가 0이 아닌 `DataType`이지만 필드 이름이 없습니다. 복합 타입은 필드 이름이 있거나 비어 있는 (크기 0) `DataType`입니다.

시스템의 모든 구체적인 값은 어떤 `DataType`의 인스턴스입니다.

## Type Unions

유형 유니온은 특별한 추상 유형으로, 특별한 [`Union`](@ref) 키워드를 사용하여 인수 유형의 모든 인스턴스를 객체로 포함합니다:

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 :: IntOrString
1

julia> "Hello!" :: IntOrString
"Hello!"

julia> 1.0 :: IntOrString
ERROR: TypeError: in typeassert, expected Union{Int64, AbstractString}, got a value of type Float64
```

많은 언어의 컴파일러는 타입에 대한 추론을 위한 내부 유니온 구조를 가지고 있으며, 줄리아는 이를 프로그래머에게 단순히 노출합니다. 줄리아 컴파일러는 `Union` 타입이 소수의 타입을 포함할 때 효율적인 코드를 생성할 수 있으며 [^1], 각 가능한 타입에 대해 별도의 분기에서 특화된 코드를 생성합니다.

특히 유용한 `Union` 타입의 경우는 `Union{T, Nothing}`입니다. 여기서 `T`는 어떤 타입이든 될 수 있으며, [`Nothing`](@ref)는 유일한 인스턴스가 객체 [`nothing`](@ref)인 단일 타입입니다. 이 패턴은 다른 언어의 [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type) 타입의 줄리아에 해당합니다. 함수 인자나 필드를 `Union{T, Nothing}`으로 선언하면, 이를 타입 `T`의 값으로 설정하거나, 값이 없음을 나타내기 위해 `nothing`으로 설정할 수 있습니다. 자세한 내용은 [this FAQ entry](@ref faq-nothing)를 참조하세요.

## Parametric Types

줄리아의 타입 시스템의 중요한 기능 중 하나는 그것이 매개변수화되어 있다는 것입니다: 타입은 매개변수를 가질 수 있으므로, 타입 선언은 실제로 매개변수 값의 가능한 조합마다 하나씩 새로운 타입의 전체 패밀리를 도입합니다. 데이터 구조와 이를 조작하는 알고리즘을 정확한 타입을 지정하지 않고도 명시할 수 있는 [generic programming](https://en.wikipedia.org/wiki/Generic_programming)의 일부 버전을 지원하는 언어가 많이 있습니다. 예를 들어, ML, Haskell, Ada, Eiffel, C++, Java, C#, F#, Scala 등에서 어떤 형태의 제네릭 프로그래밍이 존재합니다. 이 언어들 중 일부는 진정한 매개변수 다형성을 지원하고 (예: ML, Haskell, Scala), 다른 언어들은 아드혹, 템플릿 기반의 제네릭 프로그래밍 스타일을 지원합니다 (예: C++, Java). 다양한 언어에서 제네릭 프로그래밍과 매개변수 타입의 여러 가지 변형이 존재하기 때문에, 우리는 줄리아의 매개변수 타입을 다른 언어와 비교하려고 시도하지 않을 것이며, 대신 줄리아의 시스템을 독자적으로 설명하는 데 집중할 것입니다. 그러나 줄리아가 동적 타입 언어이며 모든 타입 결정을 컴파일 타임에 내릴 필요가 없기 때문에, 정적 매개변수 타입 시스템에서 발생하는 많은 전통적인 어려움은 상대적으로 쉽게 처리될 수 있다는 점은 주목할 만합니다.

모든 선언된 타입(즉, `DataType` 종류)은 매개변수화될 수 있으며, 각 경우에 동일한 구문을 사용합니다. 우리는 다음과 같은 순서로 논의할 것입니다: 먼저 매개변수화된 복합 타입, 그 다음 매개변수화된 추상 타입, 마지막으로 매개변수화된 원시 타입입니다.

### [Parametric Composite Types](@id man-parametric-composite-types)

타입 매개변수는 타입 이름 바로 뒤에 중괄호로 둘러싸여 도입됩니다:

```jldoctest pointtype
julia> struct Point{T}
           x::T
           y::T
       end
```

이 선언은 두 개의 "좌표"를 타입 `T`로 보유하는 새로운 매개변수 타입 `Point{T}`를 정의합니다. `T`는 무엇일까요? 글쎄요, 그것이 바로 매개변수 타입의 요점입니다: 그것은 실제로 어떤 타입이든 될 수 있습니다(또는 실제로는 어떤 비트 타입의 값이 될 수 있지만, 여기서는 명확히 타입으로 사용됩니다). `Point{Float64}`는 `Point`의 정의에서 `T`를 [`Float64`](@ref)로 대체하여 정의된 타입과 동등한 구체적인 타입입니다. 따라서 이 단일 선언은 실제로 무한한 수의 타입을 선언합니다: `Point{Float64}`, `Point{AbstractString}`, `Point{Int64}` 등. 이들 각각은 이제 사용 가능한 구체적인 타입입니다:

```jldoctest pointtype
julia> Point{Float64}
Point{Float64}

julia> Point{AbstractString}
Point{AbstractString}
```

`Point{Float64}` 유형은 좌표가 64비트 부동 소수점 값인 점을 나타내고, `Point{AbstractString}` 유형은 "좌표"가 문자열 객체인 "점"을 나타냅니다(참조: [Strings](@ref)).

`Point` 자체는 유효한 타입 객체로, 모든 인스턴스 `Point{Float64}`, `Point{AbstractString}` 등과 같은 하위 타입을 포함합니다:

```jldoctest pointtype
julia> Point{Float64} <: Point
true

julia> Point{AbstractString} <: Point
true
```

물론 다른 유형들은 그것의 하위 유형이 아닙니다:

```jldoctest pointtype
julia> Float64 <: Point
false

julia> AbstractString <: Point
false
```

구체적인 `Point` 타입은 서로 다른 `T` 값에 대해 절대 서로의 하위 타입이 아닙니다:

```jldoctest pointtype
julia> Point{Float64} <: Point{Int64}
false

julia> Point{Float64} <: Point{Real}
false
```

!!! warning
    이 마지막 포인트는 *매우* 중요합니다: 비록 `Float64 <: Real`이지만 우리는 **하지 않습니다** `Point{Float64} <: Point{Real}`.


다시 말해, 타입 이론의 용어로, 줄리아의 타입 매개변수는 *불변*이며, [covariant (or even contravariant)](https://en.wikipedia.org/wiki/Covariance_and_contravariance_%28computer_science%29)가 아닙니다. 이는 실용적인 이유 때문입니다: `Point{Float64}`의 모든 인스턴스는 개념적으로 `Point{Real}`의 인스턴스와 비슷할 수 있지만, 두 타입은 메모리에서 서로 다른 표현을 가집니다:

  * `Point{Float64}`의 인스턴스는 64비트 값의 즉각적인 쌍으로 간결하고 효율적으로 표현될 수 있습니다;
  * `Point{Real}`의 인스턴스는 [`Real`](@ref)의 인스턴스 쌍을 보유할 수 있어야 합니다. `Real`의 인스턴스는 임의의 크기와 구조를 가질 수 있으므로, 실제로 `Point{Real}`의 인스턴스는 개별적으로 할당된 `Real` 객체에 대한 포인터 쌍으로 표현되어야 합니다.

`Point{Float64}` 객체를 즉시 값으로 저장할 수 있는 효율성은 배열의 경우에 엄청나게 확대됩니다: `Array{Float64}`는 64비트 부동 소수점 값의 연속 메모리 블록으로 저장될 수 있는 반면, `Array{Real}`은 개별적으로 할당된 [`Real`](@ref) 객체에 대한 포인터 배열이어야 합니다 – 이는 [boxed](https://en.wikipedia.org/wiki/Object_type_%28object-oriented_programming%29#Boxing) 64비트 부동 소수점 값일 수도 있지만, 임의로 크고 복잡한 객체일 수도 있으며, 이는 `Real` 추상 타입의 구현으로 선언됩니다.

`Point{Float64}`는 `Point{Real}`의 하위 유형이 아니므로, 다음 메서드는 `Point{Float64}` 유형의 인수에 적용될 수 없습니다:

```julia
function norm(p::Point{Real})
    sqrt(p.x^2 + p.y^2)
end
```

A correct way to define a method that accepts all arguments of type `Point{T}` where `T` is a subtype of [`Real`](@ref) is:

```julia
function norm(p::Point{<:Real})
    sqrt(p.x^2 + p.y^2)
end
```

(동일하게, `function norm(p::Point{T} where T<:Real)` 또는 `function norm(p::Point{T}) where T<:Real`로 정의할 수 있습니다; [UnionAll Types](@ref)를 참조하십시오.)

추가 예제는 나중에 [Methods](@ref)에서 논의될 것입니다.

`Point` 객체는 어떻게 생성하나요? 복합 유형에 대해 사용자 정의 생성자를 정의하는 것이 가능하며, 이는 [Constructors](@ref man-constructors)에서 자세히 논의될 것입니다. 그러나 특별한 생성자 선언이 없는 경우, 새로운 복합 객체를 생성하는 두 가지 기본 방법이 있습니다. 하나는 유형 매개변수가 명시적으로 주어지는 경우이고, 다른 하나는 객체 생성자에 대한 인수에 의해 암시되는 경우입니다.

`Point{Float64}` 유형은 `T` 대신 [`Float64`](@ref)로 선언된 `Point`와 동등한 구체적 유형이므로, 이에 따라 생성자로 적용할 수 있습니다:

```jldoctest pointtype
julia> p = Point{Float64}(1.0, 2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p)
Point{Float64}
```

기본 생성자의 경우 각 필드에 대해 정확히 하나의 인수가 제공되어야 합니다:

```jldoctest pointtype
julia> Point{Float64}(1.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]

julia> Point{Float64}(1.0, 2.0, 3.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64, ::Float64, ::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]
```

매개변수화된 타입에 대해서는 기본 생성자가 하나만 생성되며, 이를 재정의하는 것은 불가능합니다. 이 생성자는 모든 인수를 받아들이고 이를 필드 타입으로 변환합니다.

많은 경우, 생성하려는 `Point` 객체의 유형을 제공하는 것은 중복적입니다. 생성자 호출에 대한 인수의 유형이 이미 암묵적으로 유형 정보를 제공하기 때문입니다. 그런 이유로, 매개변수 유형 `T`의 암시된 값이 모호하지 않은 경우 `Point` 자체를 생성자로 사용할 수도 있습니다:

```jldoctest pointtype
julia> p1 = Point(1.0,2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p1)
Point{Float64}

julia> p2 = Point(1,2)
Point{Int64}(1, 2)

julia> typeof(p2)
Point{Int64}
```

`Point`의 경우, `T`의 타입은 `Point`에 대한 두 인수가 동일한 타입일 때만 명확하게 암시됩니다. 이 경우가 아닐 경우, 생성자는 [`MethodError`](@ref)로 실패합니다:

```jldoctest pointtype
julia> Point(1,2.5)
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T
   @ Main none:2

Stacktrace:
[...]
```

적절하게 이러한 혼합 사례를 처리하기 위한 생성자 메서드를 정의할 수 있지만, 이는 [Constructors](@ref man-constructors)에서 나중에 논의될 것입니다.

### Parametric Abstract Types

매개변수 추상 타입 선언은 다음과 같은 방식으로 추상 타입의 모음을 선언합니다:

```jldoctest pointytype
julia> abstract type Pointy{T} end
```

이 선언으로 `Pointy{T}`는 `T`의 각 타입 또는 정수 값에 대해 구별되는 추상 타입입니다. 매개변수화된 복합 타입과 마찬가지로, 각 인스턴스는 `Pointy`의 서브타입입니다:

```jldoctest pointytype
julia> Pointy{Int64} <: Pointy
true

julia> Pointy{1} <: Pointy
true
```

매개변수 추상 타입은 매개변수 복합 타입과 마찬가지로 불변입니다:

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{Real}
false

julia> Pointy{Real} <: Pointy{Float64}
false
```

표기법 `Pointy{<:Real}`는 줄리아에서 *공변* 타입의 유사성을 표현하는 데 사용될 수 있으며, `Pointy{>:Int}`는 *반공변* 타입의 유사성을 나타내지만, 기술적으로 이들은 *타입의 집합*을 나타냅니다 (참조: [UnionAll Types](@ref)).

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{<:Real}
true

julia> Pointy{Real} <: Pointy{>:Int}
true
```

일반적인 추상 타입이 구체적인 타입에 대한 유용한 계층 구조를 생성하는 데 사용되는 것처럼, 매개변수 추상 타입도 매개변수 복합 타입에 대해 동일한 목적을 수행합니다. 예를 들어, `Point{T}`를 `Pointy{T}`의 하위 타입으로 다음과 같이 선언할 수 있습니다:

```jldoctest pointytype
julia> struct Point{T} <: Pointy{T}
           x::T
           y::T
       end
```

주어진 선언에 따라, `T`의 각 선택에 대해 `Point{T}`는 `Pointy{T}`의 하위 유형입니다:

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Float64}
true

julia> Point{Real} <: Pointy{Real}
true

julia> Point{AbstractString} <: Pointy{AbstractString}
true
```

이 관계는 또한 불변입니다:

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Real}
false

julia> Point{Float64} <: Pointy{<:Real}
true
```

파라메트릭 추상 타입인 `Pointy`는 어떤 목적을 가지고 있을까요? 만약 우리가 대각선 *x = y* 위에 있는 점을 나타내기 위해 단일 좌표만 필요한 점과 유사한 구현을 만든다면:

```jldoctest pointytype
julia> struct DiagPoint{T} <: Pointy{T}
           x::T
       end
```

이제 `Point{Float64}`와 `DiagPoint{Float64}` 모두 `Pointy{Float64}` 추상화의 구현체이며, 이는 모든 가능한 타입 `T`의 선택에 대해 유사합니다. 이는 모든 `Pointy` 객체가 공유하는 공통 인터페이스에 프로그래밍할 수 있게 해주며, `Point`와 `DiagPoint` 모두에 대해 구현됩니다. 그러나 이는 다음 섹션인 [Methods](@ref)에서 메서드와 디스패치를 소개하기 전까지는 완전히 시연될 수 없습니다.

타입 매개변수가 모든 가능한 타입에 대해 자유롭게 범위가 설정되는 것이 의미가 없을 수 있는 상황이 있습니다. 이러한 상황에서는 `T`의 범위를 다음과 같이 제한할 수 있습니다:

```jldoctest realpointytype
julia> abstract type Pointy{T<:Real} end
```

이러한 선언을 통해 `T` 대신 [`Real`](@ref)의 하위 유형인 모든 유형을 사용하는 것이 허용되지만, `Real`의 하위 유형이 아닌 유형은 사용할 수 없습니다:

```jldoctest realpointytype
julia> Pointy{Float64}
Pointy{Float64}

julia> Pointy{Real}
Pointy{Real}

julia> Pointy{AbstractString}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got Type{AbstractString}

julia> Pointy{1}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got a value of type Int64
```

매개변수화된 복합 유형의 유형 매개변수는 동일한 방식으로 제한할 수 있습니다:

```julia
struct Point{T<:Real} <: Pointy{T}
    x::T
    y::T
end
```

실제 파라메트릭 타입 기계가 어떻게 유용할 수 있는지에 대한 실제 예를 제공하기 위해, 여기 줄리아의 [`Rational`](@ref) 불변 타입의 실제 정의가 있습니다(단순성을 위해 생성자는 생략합니다). 이는 정수의 정확한 비율을 나타냅니다:

```julia
struct Rational{T<:Integer} <: Real
    num::T
    den::T
end
```

정수 값의 비율을 취하는 것은 의미가 있으므로, 매개변수 유형 `T`는 [`Integer`](@ref)의 하위 유형으로 제한됩니다. 정수의 비율은 실수선上的 값을 나타내므로, 모든 [`Rational`](@ref)는 [`Real`](@ref) 추상화의 인스턴스입니다.

### Tuple Types

튜플은 함수의 인수에 대한 추상화입니다 - 함수 자체는 제외하고. 함수의 인수에서 중요한 측면은 그 순서와 유형입니다. 따라서 튜플 유형은 각 매개변수가 하나의 필드 유형인 매개변수화된 불변 유형과 유사합니다. 예를 들어, 2개 요소의 튜플 유형은 다음과 같은 불변 유형과 유사합니다:

```julia
struct Tuple2{A,B}
    a::A
    b::B
end
```

그러나 세 가지 주요 차이점이 있습니다:

  * 튜플 타입은 매개변수를 임의의 개수 가질 수 있습니다.
  * 튜플 타입은 매개변수에서 *공변적*입니다: `Tuple{Int}`는 `Tuple{Any}`의 하위 타입입니다. 따라서 `Tuple{Any}`는 추상 타입으로 간주되며, 튜플 타입은 매개변수가 구체적일 때만 구체적입니다.
  * 튜플은 필드 이름이 없으며, 필드는 인덱스를 통해서만 접근할 수 있습니다.

튜플 값은 괄호와 쉼표로 작성됩니다. 튜플이 구성될 때, 적절한 튜플 유형이 필요에 따라 생성됩니다:

```jldoctest
julia> typeof((1,"foo",2.5))
Tuple{Int64, String, Float64}
```

공분산의 의미를 주목하세요:

```jldoctest
julia> Tuple{Int,AbstractString} <: Tuple{Real,Any}
true

julia> Tuple{Int,AbstractString} <: Tuple{Real,Real}
false

julia> Tuple{Int,AbstractString} <: Tuple{Real,}
false
```

직관적으로, 이는 함수의 인수 유형이 함수의 시그니처의 하위 유형이 되는 것과 관련이 있습니다(시그니처가 일치할 때).

### Vararg Tuple Types

튜플 타입의 마지막 매개변수는 특별한 값 [`Vararg`](@ref)일 수 있으며, 이는 임의의 수의 후행 요소를 나타냅니다:

```jldoctest
julia> mytupletype = Tuple{AbstractString,Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```

또한 `Vararg{T}`는 타입 `T`의 0개 이상의 요소에 해당합니다. Vararg 튜플 타입은 varargs 메서드에서 허용되는 인수를 나타내는 데 사용됩니다(참조: [Varargs Functions](@ref)).

특별한 값 `Vararg{T,N}` (튜플 타입의 마지막 매개변수로 사용될 때)는 정확히 `N` 개의 `T` 타입 요소에 해당합니다. `NTuple{N,T}`는 `Tuple{Vararg{T,N}}`의 편리한 별칭으로, 즉 정확히 `N` 개의 `T` 타입 요소를 포함하는 튜플 타입입니다.

### Named Tuple Types

명명된 튜플은 [`NamedTuple`](@ref) 유형의 인스턴스이며, 두 개의 매개변수를 가집니다: 필드 이름을 제공하는 기호의 튜플과 필드 유형을 제공하는 튜플 유형입니다. 편의를 위해 `NamedTuple` 유형은 [`@NamedTuple`](@ref) 매크로를 사용하여 인쇄되며, 이는 `key::Type` 선언을 통해 이러한 유형을 선언하는 편리한 `struct`-유사 구문을 제공합니다. 생략된 `::Type`은 `::Any`에 해당합니다.

```jldoctest
julia> typeof((a=1,b="hello")) # prints in macro form
@NamedTuple{a::Int64, b::String}

julia> NamedTuple{(:a, :b), Tuple{Int64, String}} # long form of the type
@NamedTuple{a::Int64, b::String}
```

`@NamedTuple` 매크로의 `begin ... end` 형식은 선언을 여러 줄로 나눌 수 있게 해줍니다(구조체 선언과 유사하지만), 그 외에는 동일합니다:

```jldoctest
julia> @NamedTuple begin
           a::Int
           b::String
       end
@NamedTuple{a::Int64, b::String}
```

`NamedTuple` 타입은 생성자로 사용될 수 있으며, 단일 튜플 인수를 허용합니다. 생성된 `NamedTuple` 타입은 두 개의 매개변수가 지정된 구체적인 타입이거나, 필드 이름만 지정하는 타입일 수 있습니다:

```jldoctest
julia> @NamedTuple{a::Float32,b::String}((1, ""))
(a = 1.0f0, b = "")

julia> NamedTuple{(:a, :b)}((1, ""))
(a = 1, b = "")
```

필드 유형이 지정된 경우, 인수가 변환됩니다. 그렇지 않으면 인수의 유형이 직접 사용됩니다.

### Parametric Primitive Types

원시 타입은 매개변수적으로 선언될 수도 있습니다. 예를 들어, 포인터는 원시 타입으로 표현되며, 이는 줄리아에서 다음과 같이 선언됩니다:

```julia
# 32-bit system:
primitive type Ptr{T} 32 end

# 64-bit system:
primitive type Ptr{T} 64 end
```

이 선언의 약간 이상한 특징은 전형적인 매개변수 복합 유형과 비교할 때, 유형 매개변수 `T`가 유형 자체의 정의에 사용되지 않는다는 것입니다. 이는 본질적으로 동일한 구조를 가진 전체 유형 패밀리를 정의하는 추상 태그일 뿐이며, 유형 매개변수에 의해 구분됩니다. 따라서 `Ptr{Float64}`와 `Ptr{Int64}`는 동일한 표현을 가지고 있음에도 불구하고 서로 다른 유형입니다. 물론 모든 특정 포인터 유형은 우산 유형 [`Ptr`](@ref)의 하위 유형입니다:

```jldoctest
julia> Ptr{Float64} <: Ptr
true

julia> Ptr{Int64} <: Ptr
true
```

## UnionAll Types

우리는 `Ptr`와 같은 매개변수형이 모든 인스턴스(`Ptr{Int64}` 등)의 슈퍼타입으로 작용한다고 말했습니다. 이것은 어떻게 작동할까요? `Ptr` 자체는 참조된 데이터의 유형을 알지 못하면 메모리 작업에 사용할 수 없기 때문에 일반 데이터 유형이 될 수 없습니다. 답은 `Ptr`(또는 `Array`와 같은 다른 매개변수형)이 [`UnionAll`](@ref) 유형이라고 불리는 다른 종류의 유형이라는 것입니다. 이러한 유형은 일부 매개변수의 모든 값에 대한 *반복된 합집합*을 표현합니다.

`UnionAll` 타입은 일반적으로 `where` 키워드를 사용하여 작성됩니다. 예를 들어 `Ptr`는 `Ptr{T} where T`로 더 정확하게 작성될 수 있으며, 이는 어떤 값 `T`에 대해 `Ptr{T}` 타입인 모든 값을 의미합니다. 이 맥락에서 매개변수 `T`는 종종 "타입 변수"라고도 불리며, 이는 타입을 범위로 하는 변수와 같습니다. 각 `where`는 단일 타입 변수를 도입하므로, 이러한 표현은 여러 매개변수를 가진 타입의 경우 중첩됩니다. 예를 들어 `Array{T,N} where N where T`와 같습니다.

타입 응용 구문 `A{B,C}`는 `A`가 `UnionAll` 타입이어야 하며, 먼저 `B`를 `A`의 가장 바깥쪽 타입 변수에 대체합니다. 결과는 또 다른 `UnionAll` 타입이 되어야 하며, 그 안에 `C`가 대체됩니다. 따라서 `A{B,C}`는 `A{B}{C}`와 동등합니다. 이것은 `Array{Float64}`와 같이 타입을 부분적으로 인스턴스화할 수 있는 이유를 설명합니다: 첫 번째 매개변수 값은 고정되었지만, 두 번째는 여전히 모든 가능한 값에 대해 범위가 설정됩니다. 명시적인 `where` 구문을 사용하면 매개변수의 하위 집합을 고정할 수 있습니다. 예를 들어, 모든 1차원 배열의 타입은 `Array{T,1} where T`로 작성할 수 있습니다.

타입 변수는 서브타입 관계로 제한될 수 있습니다. `Array{T} where T<:Integer`는 요소 타입이 어떤 종류의 [`Integer`](@ref)인 모든 배열을 나타냅니다. `Array{<:Integer}` 구문은 `Array{T} where T<:Integer`의 편리한 약어입니다. 타입 변수는 하한과 상한을 모두 가질 수 있습니다. `Array{T} where Int<:T<:Number`는 `Int`를 포함할 수 있는 모든 [`Number`](@ref) 배열을 나타냅니다(여기서 `T`는 최소한 `Int`만큼 커야 합니다). `where T>:Int` 구문은 타입 변수의 하한만 지정하는 데에도 사용할 수 있으며, `Array{>:Int}`는 `Array{T} where T>:Int`와 동일합니다.

`where` 표현식은 중첩될 수 있으므로, 타입 변수 경계는 외부 타입 변수를 참조할 수 있습니다. 예를 들어 `Tuple{T,Array{S}} where S<:AbstractArray{T} where T<:Real`는 첫 번째 요소가 어떤 [`Real`](@ref)인 2-튜플을 참조하며, 두 번째 요소는 첫 번째 튜플 요소의 타입을 포함하는 어떤 종류의 배열의 `Array`입니다.

`where` 키워드는 더 복잡한 선언 안에 중첩될 수 있습니다. 예를 들어, 다음 선언에 의해 생성된 두 가지 유형을 고려해 보십시오:

```jldoctest
julia> const T1 = Array{Array{T, 1} where T, 1}
Vector{Vector} (alias for Array{Array{T, 1} where T, 1})

julia> const T2 = Array{Array{T, 1}, 1} where T
Array{Vector{T}, 1} where T
```

타입 `T1`은 1차원 배열의 1차원 배열을 정의합니다. 각 내부 배열은 동일한 유형의 객체로 구성되지만, 이 유형은 내부 배열마다 다를 수 있습니다. 반면에 타입 `T2`는 모든 내부 배열이 동일한 유형을 가져야 하는 1차원 배열의 1차원 배열을 정의합니다. `T2`는 추상 타입이라는 점에 유의하십시오. 예를 들어, `Array{Array{Int,1},1} <: T2`인 반면, `T1`은 구체적인 타입입니다. 결과적으로 `T1`은 인수가 없는 생성자 `a=T1()`로 생성할 수 있지만 `T2`는 생성할 수 없습니다.

이러한 유형의 이름을 지정하는 데 편리한 구문이 있으며, 이는 함수 정의 구문의 축약형과 유사합니다:

```julia
Vector{T} = Array{T, 1}
```

이는 `const Vector = Array{T,1} where T`와 같습니다. `Vector{Float64}`를 작성하는 것은 `Array{Float64,1}`을 작성하는 것과 같습니다. 그리고 우산 타입인 `Vector`는 두 번째 매개변수 – 배열 차원의 수 – 가 1인 모든 `Array` 객체를 인스턴스로 가집니다. 요소 타입이 무엇이든 상관없이 말이죠. 매개변수 타입을 항상 완전하게 지정해야 하는 언어에서는 이것이 그다지 유용하지 않지만, Julia에서는 모든 요소 타입의 일차원 밀집 배열을 포함하는 추상 타입에 대해 단순히 `Vector`라고 작성할 수 있게 해줍니다.

## [Singleton types](@id man-singleton-types)

필드가 없는 불변 복합 유형을 *싱글톤*이라고 합니다. 공식적으로, 만약

1. `T`는 불변 복합 타입(즉, `struct`로 정의됨)입니다.
2. `a isa T && b isa T`는 `a === b`를 의미합니다.

그렇다면 `T`는 단일체 유형입니다.[^2] [`Base.issingletontype`](@ref)는 유형이 단일체 유형인지 확인하는 데 사용할 수 있습니다. [Abstract types](@ref man-abstract-types)는 구조적으로 단일체 유형이 될 수 없습니다.

정의에 따르면, 이러한 유형의 인스턴스는 오직 하나만 존재할 수 있다:

```jldoctest
julia> struct NoFields
       end

julia> NoFields() === NoFields()
true

julia> Base.issingletontype(NoFields)
true
```

[`===`](@ref) 함수는 생성된 `NoFields` 인스턴스들이 실제로 동일하다는 것을 확인합니다.

매개변수화된 타입은 위의 조건이 성립할 때 단일체 타입이 될 수 있습니다. 예를 들어,

```jldoctest
julia> struct NoFieldsParam{T}
       end

julia> Base.issingletontype(NoFieldsParam) # Can't be a singleton type ...
false

julia> NoFieldsParam{Int}() isa NoFieldsParam # ... because it has ...
true

julia> NoFieldsParam{Bool}() isa NoFieldsParam # ... multiple instances.
true

julia> Base.issingletontype(NoFieldsParam{Int}) # Parametrized, it is a singleton.
true

julia> NoFieldsParam{Int}() === NoFieldsParam{Int}()
true
```

## Types of functions

각 함수는 고유한 유형을 가지며, 이는 `Function`의 하위 유형입니다.

```jldoctest foo41
julia> foo41(x) = x + 1
foo41 (generic function with 1 method)

julia> typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)
```

`typeof(foo41)`가 그 자체로 출력되는 방식을 주목하세요. 이는 단순히 출력에 대한 관례일 뿐이며, 이는 다른 값처럼 사용할 수 있는 일급 객체입니다:

```jldoctest foo41
julia> T = typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)

julia> T <: Function
true
```

최상위에서 정의된 함수의 유형은 싱글톤입니다. 필요할 경우, 이를 [`===`](@ref)와 비교할 수 있습니다.

[Closures](@ref man-anonymous-functions) 또한 고유한 유형을 가지며, 일반적으로 `#<숫자>`로 끝나는 이름으로 인쇄됩니다. 서로 다른 위치에 정의된 함수의 이름과 유형은 구별되지만, 세션 간에 동일한 방식으로 인쇄된다고 보장되지는 않습니다.

```jldoctest; filter = r"[0-9\.]+"
julia> typeof(x -> x + 1)
var"#9#10"
```

클로저의 유형은 반드시 싱글톤이 아닙니다.

```jldoctest
julia> addy(y) = x -> x + y
addy (generic function with 1 method)

julia> typeof(addy(1)) === typeof(addy(2))
true

julia> addy(1) === addy(2)
false

julia> Base.issingletontype(typeof(addy(1)))
false
```

## [`Type{T}` type selectors](@id man-typet-type)

각 유형 `T`에 대해, `Type{T}`는 오직 객체 `T`만을 인스턴스로 가지는 추상 매개변수 유형입니다. [Parametric Methods](@ref) 및 [conversions](@ref conversion-and-promotion)에 대해 논의하기 전까지는 이 구조의 유용성을 설명하기 어렵지만, 간단히 말해, 특정 유형에 대해 함수 동작을 *값*으로 전문화할 수 있게 해줍니다. 이는 특정 유형이 인수 중 하나의 유형에 의해 암시되는 것이 아니라 명시적 인수로 주어질 때 동작이 달라지는 메서드(특히 매개변수화된 메서드)를 작성하는 데 유용합니다.

정의가 다소 이해하기 어려우므로 몇 가지 예를 살펴보겠습니다:

```jldoctest
julia> isa(Float64, Type{Float64})
true

julia> isa(Real, Type{Float64})
false

julia> isa(Real, Type{Real})
true

julia> isa(Float64, Type{Real})
false
```

다시 말해, [`isa(A, Type{B})`](@ref)는 `A`와 `B`가 동일한 객체이고 그 객체가 타입일 때만 참입니다.

특히, 매개변수화된 유형이 [invariant](@ref man-parametric-composite-types)이므로, 우리는 다음과 같습니다.

```jldoctest
julia> struct TypeParamExample{T}
           x::T
       end

julia> TypeParamExample isa Type{TypeParamExample}
true

julia> TypeParamExample{Int} isa Type{TypeParamExample}
false

julia> TypeParamExample{Int} isa Type{TypeParamExample{Int}}
true
```

매개변수 없이 `Type`은 모든 타입 객체를 인스턴스로 가지는 단순한 추상 타입입니다:

```jldoctest
julia> isa(Type{Float64}, Type)
true

julia> isa(Float64, Type)
true

julia> isa(Real, Type)
true
```

타입이 아닌 모든 객체는 `Type`의 인스턴스가 아닙니다:

```jldoctest
julia> isa(1, Type)
false

julia> isa("foo", Type)
false
```

While `Type` is part of Julia's type hierarchy like any other abstract parametric type, it is not commonly used outside method signatures except in some special cases. Another important use case for `Type` is sharpening field types which would otherwise be captured less precisely, e.g. as [`DataType`](@ref man-declared-types) in the example below where the default constructor could lead to performance problems in code relying on the precise wrapped type (similarly to [abstract type parameters](@ref man-performance-abstract-container)).

```jldoctest
julia> struct WrapType{T}
       value::T
       end

julia> WrapType(Float64) # default constructor, note DataType
WrapType{DataType}(Float64)

julia> WrapType(::Type{T}) where T = WrapType{Type{T}}(T)
WrapType

julia> WrapType(Float64) # sharpened constructor, note more precise Type{Float64}
WrapType{Type{Float64}}(Float64)
```

## Type Aliases

때때로 이미 표현 가능한 유형에 대해 새 이름을 도입하는 것이 편리합니다. 이는 간단한 할당 문을 사용하여 수행할 수 있습니다. 예를 들어, `UInt`는 시스템의 포인터 크기에 따라 [`UInt32`](@ref) 또는 [`UInt64`](@ref)로 별칭이 지정됩니다:

```julia-repl
# 32-bit system:
julia> UInt
UInt32

# 64-bit system:
julia> UInt
UInt64
```

이것은 `base/boot.jl`의 다음 코드를 통해 수행됩니다:

```julia
if Int === Int64
    const UInt = UInt64
else
    const UInt = UInt32
end
```

물론, 이는 `Int`가 무엇에 대한 별칭인지에 따라 다릅니다 – 하지만 이는 올바른 유형으로 미리 정의되어 있습니다 – [`Int32`](@ref) 또는 [`Int64`](@ref) 중 하나입니다.

(Note that unlike `Int`, `Float` does not exist as a type alias for a specific sized [`AbstractFloat`](@ref). Unlike with integer registers, where the size of `Int` reflects the size of a native pointer on that machine, the floating point register sizes are specified by the IEEE-754 standard.)

타입 별칭은 매개변수화될 수 있습니다:

```jldoctest
julia> const Family{T} = Set{T}
Set

julia> Family{Char} === Set{Char}
true
```

## Operations on Types

줄리아에서 타입은 객체이기 때문에 일반 함수가 이들에 대해 작동할 수 있습니다. 타입을 다루거나 탐색하는 데 특히 유용한 몇 가지 함수가 이미 소개되었습니다. 예를 들어, `<:` 연산자는 왼쪽 피연산자가 오른쪽 피연산자의 하위 타입인지 여부를 나타냅니다.

[`isa`](@ref) 함수는 객체가 주어진 유형인지 테스트하고 true 또는 false를 반환합니다:

```jldoctest
julia> isa(1, Int)
true

julia> isa(1, AbstractFloat)
false
```

[`typeof`](@ref) 함수는 매뉴얼의 예제에서 이미 사용되었으며, 인수의 유형을 반환합니다. 위에서 언급했듯이, 유형은 객체이므로, 그들도 유형을 가지며, 우리는 그들의 유형이 무엇인지 물어볼 수 있습니다:

```jldoctest
julia> typeof(Rational{Int})
DataType

julia> typeof(Union{Real,String})
Union
```

무슨 일이 일어날까요? 우리가 이 과정을 반복한다면? 타입의 타입의 타입은 무엇일까요? 사실, 타입은 모두 복합 값이므로 모두 `DataType`의 타입을 가집니다:

```jldoctest
julia> typeof(DataType)
DataType

julia> typeof(Union)
DataType
```

`DataType`은 그 자체로 하나의 유형입니다.

또 다른 연산은 일부 유형에 적용되는 [`supertype`](@ref)로, 이는 유형의 수퍼타입을 드러냅니다. 선언된 유형(`DataType`)만이 모호하지 않은 수퍼타입을 가집니다:

```jldoctest
julia> supertype(Float64)
AbstractFloat

julia> supertype(Number)
Any

julia> supertype(AbstractString)
Any

julia> supertype(Any)
Any
```

다른 유형 객체(또는 비유형 객체)에 [`supertype`](@ref)를 적용하면 [`MethodError`](@ref)가 발생합니다:

```jldoctest; filter = r"Closest candidates.*"s
julia> supertype(Union{Float64,Int64})
ERROR: MethodError: no method matching supertype(::Type{Union{Float64, Int64}})
The function `supertype` exists, but no method is defined for this combination of argument types.

Closest candidates are:
[...]
```

## [Custom pretty-printing](@id man-custom-pretty-printing)

종종, 유형의 인스턴스가 어떻게 표시되는지를 사용자 정의하고 싶어합니다. 이는 [`show`](@ref) 함수를 오버로딩하여 달성됩니다. 예를 들어, 극형태의 복소수를 나타내는 유형을 정의한다고 가정해 보겠습니다:

```jldoctest polartype
julia> struct Polar{T<:Real} <: Number
           r::T
           Θ::T
       end

julia> Polar(r::Real,Θ::Real) = Polar(promote(r,Θ)...)
Polar
```

여기에서는 다양한 [`Real`](@ref) 유형의 인수를 받을 수 있도록 사용자 정의 생성자 함수를 추가하여 이를 공통 유형으로 승격시킬 수 있습니다(자세한 내용은 [Constructors](@ref man-constructors) 및 [Conversion and Promotion](@ref conversion-and-promotion) 참조). (물론, [`Number`](@ref)처럼 작동하게 하려면 `+`, `*`, `one`, `zero`, 승격 규칙 등과 같은 많은 다른 메서드도 정의해야 합니다.) 기본적으로 이 유형의 인스턴스는 유형 이름과 필드 값에 대한 정보를 포함하여 비교적 간단하게 표시되며, 예를 들어 `Polar{Float64}(3.0,4.0)`와 같습니다.

`3.0 * exp(4.0im)` 대신 표시하려면, 주어진 출력 객체 `io` (파일, 터미널, 버퍼 등을 나타냄; [Networking and Streams](@ref) 참조)에 객체를 인쇄하는 다음 메서드를 정의해야 합니다:

```jldoctest polartype
julia> Base.show(io::IO, z::Polar) = print(io, z.r, " * exp(", z.Θ, "im)")
```

`Polar` 객체의 표시를 보다 세밀하게 제어할 수 있습니다. 특히, 때때로 REPL 및 기타 대화형 환경에서 단일 객체를 표시하는 데 사용되는 자세한 다중 행 인쇄 형식과 [`print`](@ref)에 사용되는 보다 간결한 단일 행 형식을 모두 원할 수 있습니다. 기본적으로 `show(io, z)` 함수가 두 경우 모두 호출되지만, `text/plain` MIME 유형을 두 번째 인수로 사용하는 `show`의 세 인수 형태를 오버로드하여 객체를 표시하기 위한 *다른* 다중 행 형식을 정의할 수 있습니다(예: [Multimedia I/O](@ref Multimedia-I/O)).

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/plain", z::Polar{T}) where{T} =
           print(io, "Polar{$T} complex number:\n   ", z)
```

(여기서 `print(..., z)`는 2-인수 `show(io, z)` 메서드를 호출합니다.) 이로 인해:

```jldoctest polartype
julia> Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> [Polar(3, 4.0), Polar(4.0,5.3)]
2-element Vector{Polar{Float64}}:
 3.0 * exp(4.0im)
 4.0 * exp(5.3im)
```

단일 행 `show(io, z)` 형식이 `Polar` 값의 배열에 여전히 사용되는 곳. 기술적으로, REPL은 실행된 줄의 결과를 표시하기 위해 `display(z)`를 호출하며, 이는 기본적으로 `show(stdout, MIME("text/plain"), z)`로 설정되어 있고, 다시 `show(stdout, z)`로 기본 설정됩니다. 그러나 새로운 [`display`](@ref) 메서드를 정의해서는 안 됩니다. 새로운 멀티미디어 디스플레이 핸들러를 정의하는 경우를 제외하고 (자세한 내용은 [Multimedia I/O](@ref Multimedia-I/O)를 참조하십시오).

또한, `show` 메서드를 다른 MIME 유형에 대해 정의하여 이 환경(예: IJulia)에서 객체의 더 풍부한 표시(HTML, 이미지 등)를 활성화할 수 있습니다. 예를 들어, 우리는 다음과 같이 위첨자와 이탤릭체가 포함된 `Polar` 객체의 형식화된 HTML 표시를 정의할 수 있습니다:

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/html", z::Polar{T}) where {T} =
           println(io, "<code>Polar{$T}</code> complex number: ",
                   z.r, " <i>e</i><sup>", z.Θ, " <i>i</i></sup>")
```

`Polar` 객체는 HTML 표시를 지원하는 환경에서 자동으로 표시되지만, 원할 경우 `show`를 수동으로 호출하여 HTML 출력을 얻을 수 있습니다:

```jldoctest polartype
julia> show(stdout, "text/html", Polar(3.0,4.0))
<code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup>
```

```@raw html
<p>An HTML renderer would display this as: <code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup></p>
```

일반적인 규칙으로, 단일 행 `show` 메서드는 표시된 객체를 생성하기 위한 유효한 Julia 표현식을 출력해야 합니다. 위의 `Polar`에 대한 단일 행 `show` 메서드에 곱셈 연산자(`*`)와 같은 중위 연산자가 포함되어 있을 경우, 다른 객체의 일부로 인쇄될 때 올바르게 구문 분석되지 않을 수 있습니다. 이를 확인하기 위해, 특정 `Polar` 유형의 인스턴스의 제곱을 취하는 표현식 객체(참조: [Program representation](@ref))를 고려해 보십시오:

```jldoctest polartype
julia> a = Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> print(:($a^2))
3.0 * exp(4.0im) ^ 2
```

연산자 `^`가 `*`보다 높은 우선 순위를 가지기 때문에(자세한 내용은 [Operator Precedence and Associativity](@ref) 참조), 이 출력은 `a ^ 2`라는 표현을 정확하게 나타내지 않으며, 이는 `(3.0 * exp(4.0im)) ^ 2`와 같아야 합니다. 이 문제를 해결하기 위해, 출력할 때 표현식 객체에 의해 내부적으로 호출되는 `Base.show_unquoted(io::IO, z::Polar, indent::Int, precedence::Int)`에 대한 사용자 정의 메서드를 만들어야 합니다.

```jldoctest polartype
julia> function Base.show_unquoted(io::IO, z::Polar, ::Int, precedence::Int)
           if Base.operator_precedence(:*) <= precedence
               print(io, "(")
               show(io, z)
               print(io, ")")
           else
               show(io, z)
           end
       end

julia> :($a^2)
:((3.0 * exp(4.0im)) ^ 2)
```

위에서 정의된 메서드는 호출 연산자의 우선 순위가 곱셈의 우선 순위보다 높거나 같을 때 `show` 호출 주위에 괄호를 추가합니다. 이 검사는 괄호 없이 올바르게 구문 분석되는 표현식(`:($a + 2)` 및 `:($a == 2)`와 같은)이 출력할 때 괄호를 생략할 수 있도록 합니다:

```jldoctest polartype
julia> :($a + 2)
:(3.0 * exp(4.0im) + 2)

julia> :($a == 2)
:(3.0 * exp(4.0im) == 2)
```

일부 경우, 컨텍스트에 따라 `show` 메서드의 동작을 조정하는 것이 유용합니다. 이는 [`IOContext`](@ref) 유형을 통해 달성할 수 있으며, 이는 래핑된 IO 스트림과 함께 컨텍스트 속성을 전달할 수 있게 해줍니다. 예를 들어, `:compact` 속성이 `true`로 설정된 경우 `show` 메서드에서 더 짧은 표현을 만들 수 있으며, 속성이 `false`이거나 없으면 긴 표현으로 되돌아갑니다:

```jldoctest polartype
julia> function Base.show(io::IO, z::Polar)
           if get(io, :compact, false)::Bool
               print(io, z.r, "ℯ", z.Θ, "im")
           else
               print(io, z.r, " * exp(", z.Θ, "im)")
           end
       end
```

이 새로운 압축 표현은 전달된 IO 스트림이 `:compact` 속성이 설정된 `IOContext` 객체일 때 사용됩니다. 특히, 이는 여러 열이 있는 배열을 인쇄할 때(수평 공간이 제한된 경우) 해당됩니다:

```jldoctest polartype
julia> show(IOContext(stdout, :compact=>true), Polar(3, 4.0))
3.0ℯ4.0im

julia> [Polar(3, 4.0) Polar(4.0,5.3)]
1×2 Matrix{Polar{Float64}}:
 3.0ℯ4.0im  4.0ℯ5.3im
```

[`IOContext`](@ref) 문서에서 인쇄 조정에 사용할 수 있는 일반 속성 목록을 확인하세요.

## "Value types"

줄리아에서는 `true` 또는 `false`와 같은 *값*에 대해 디스패치를 할 수 없습니다. 그러나 매개변수화된 타입에 대해 디스패치를 할 수 있으며, 줄리아는 "일반 비트" 값(타입, 심볼, 정수, 부동 소수점 숫자, 튜플 등)을 타입 매개변수로 포함하는 것을 허용합니다. 일반적인 예는 `Array{T,N}`에서의 차원 매개변수로, 여기서 `T`는 타입(예: [`Float64`](@ref))이지만 `N`은 단순히 `Int`입니다.

사용자가 매개변수로 값을 받아들이는 사용자 정의 유형을 생성할 수 있으며, 이를 사용하여 사용자 정의 유형의 디스패치를 제어할 수 있습니다. 이 아이디어를 설명하기 위해 매개변수화된 유형 `Val{x}`와 그 생성자 `Val(x) = Val{x}()`를 소개하겠습니다. 이는 더 복잡한 계층 구조가 필요하지 않은 경우 이 기술을 활용하는 일반적인 방법으로 사용됩니다.

[`Val`](@ref)는 다음과 같이 정의됩니다:

```jldoctest valtype
julia> struct Val{x}
       end

julia> Val(x) = Val{x}()
Val
```

`Val`의 구현은 이보다 더 이상 없습니다. Julia의 표준 라이브러리의 일부 함수는 `Val` 인스턴스를 인수로 받아들이며, 이를 사용하여 자신의 함수를 작성할 수도 있습니다. 예를 들어:

```jldoctest valtype
julia> firstlast(::Val{true}) = "First"
firstlast (generic function with 1 method)

julia> firstlast(::Val{false}) = "Last"
firstlast (generic function with 2 methods)

julia> firstlast(Val(true))
"First"

julia> firstlast(Val(false))
"Last"
```

일관성을 위해 Julia에서는 호출 지점에서 항상 `Val` *인스턴스*를 전달해야 하며, *타입*을 사용해서는 안 됩니다. 즉, `foo(Val(:bar))`를 사용하고 `foo(Val{:bar})`를 사용하지 마십시오.

파라메트릭 "값" 유형, 특히 `Val`을 잘못 사용하는 것은 매우 쉽다는 점은 주목할 가치가 있습니다. 불리한 경우에는 코드의 성능이 훨씬 *나빠질* 수 있습니다. 특히 위에서 설명한 것처럼 실제 코드를 작성하고 싶지는 않을 것입니다. `Val`의 적절한(및 부적절한) 사용에 대한 자세한 내용은 [the more extensive discussion in the performance tips](@ref man-performance-value-type)를 읽어보시기 바랍니다.

[^1]: "Small" is defined by the `max_union_splitting` configuration, which currently defaults to 4.

[^2]: A few popular languages have singleton types, including Haskell, Scala and Ruby.
