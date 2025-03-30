# [Functions](@id man-functions)

줄리아에서 함수는 인수 값의 튜플을 반환 값에 매핑하는 객체입니다. 줄리아 함수는 프로그램의 전역 상태에 의해 영향을 받고 영향을 줄 수 있기 때문에 순수한 수학적 함수가 아닙니다. 줄리아에서 함수를 정의하는 기본 구문은 다음과 같습니다:

```jldoctest
julia> function f(x, y)
           x + y
       end
f (generic function with 1 method)
```

이 함수는 두 개의 인수 `x`와 `y`를 받아들이고, 마지막으로 평가된 표현식의 값을 반환합니다. 이 값은 `x + y`입니다.

줄리아에서 함수를 정의하는 두 번째, 더 간결한 문법이 있습니다. 위에서 보여준 전통적인 함수 선언 문법은 다음의 간결한 "할당 형식"과 동일합니다:

```jldoctest fofxy
julia> f(x, y) = x + y
f (generic function with 1 method)
```

과제 양식에서 함수의 본문은 단일 표현식이어야 하지만, 복합 표현식일 수 있습니다 (참조: [Compound Expressions](@ref man-compound-expressions)). 짧고 간단한 함수 정의는 줄리아에서 일반적입니다. 따라서 짧은 함수 구문은 매우 관용적이며, 타이핑과 시각적 소음을 모두 상당히 줄여줍니다.

함수는 전통적인 괄호 구문을 사용하여 호출됩니다:

```jldoctest fofxy
julia> f(2, 3)
5
```

괄호 없이, 표현식 `f`는 함수 객체를 참조하며, 다른 값처럼 전달될 수 있습니다:

```jldoctest fofxy
julia> g = f;

julia> g(2, 3)
5
```

변수와 마찬가지로, 유니코드는 함수 이름에도 사용할 수 있습니다:

```jldoctest
julia> ∑(x, y) = x + y
∑ (generic function with 1 method)

julia> ∑(2, 3)
5
```

## [Argument Passing Behavior](@id man-argument-passing)

줄리아 함수 인수는 "공유에 의한 전달"이라고 불리는 규칙을 따르며, 이는 값이 함수에 전달될 때 복사되지 않음을 의미합니다. 함수 인수 자체는 새로운 변수 *바인딩* (값을 참조할 수 있는 새로운 "이름")으로 작용하며, 이는 [assignments](@ref man-assignment-expressions) `argument_name = argument_value`와 유사하여, 이들이 참조하는 객체는 전달된 값과 동일합니다. 함수 내에서 변경된 가변 값(예: `Array`)에 대한 수정은 호출자에게도 보이게 됩니다. (이는 스킴, 대부분의 리스프, 파이썬, 루비, 펄 등 다른 동적 언어에서도 발견되는 동일한 동작입니다.)

예를 들어, 함수에서

```julia
function f(x, y)
    x[1] = 42    # mutates x
    y = 7 + y    # new binding for y, no mutation
    return y
end
```

`x[1] = 42` 문장은 객체 `x`를 *변경*하며, 따라서 이 변경 사항은 호출자가 이 인수로 전달한 배열에서 *보이게* 됩니다. 반면에, 할당문 `y = 7 + y`는 *바인딩* ("이름") `y`를 새로운 값 `7 + y`를 가리키도록 변경하며, 이는 `y`가 참조하는 *원래* 객체를 변경하지 않으므로 호출자가 전달한 해당 인수를 *변경하지* 않습니다. 이는 `f(x, y)`를 호출하면 확인할 수 있습니다:

```julia-repl
julia> a = [4, 5, 6]
3-element Vector{Int64}:
 4
 5
 6

julia> b = 3
3

julia> f(a, b) # returns 7 + b == 10
10

julia> a  # a[1] is changed to 42 by f
3-element Vector{Int64}:
 42
  5
  6

julia> b  # not changed
3
```

일반적인 관례로서 Julia에서는 (구문적 요구 사항은 아님) 이러한 함수는 [typically be named `f!(x, y)`](@ref man-punctuation) 대신 `f(x, y)`로 작성됩니다. 이는 호출 지점에서 인수 중 적어도 하나(종종 첫 번째)가 변경되고 있음을 시각적으로 상기시켜줍니다.

!!! warning "Shared memory between arguments"
    변경하는 함수의 동작은 변경된 인수가 다른 인수와 메모리를 공유할 때 예상치 못한 결과를 초래할 수 있으며, 이를 별칭(aliasing)이라고 합니다(예: 하나가 다른 것의 뷰일 때). 함수의 문서 문자열이 별칭이 예상되는 결과를 생성한다고 명시적으로 언급하지 않는 한, 그러한 입력에 대해 올바른 동작을 보장하는 것은 호출자의 책임입니다.


## Argument-type declarations

함수 인수의 유형을 `::TypeName`을 인수 이름에 추가하여 선언할 수 있습니다. 이는 Julia의 [Type Declarations](@ref)에 대해 일반적입니다. 예를 들어, 다음 함수는 [Fibonacci numbers](https://en.wikipedia.org/wiki/Fibonacci_number)를 재귀적으로 계산합니다:

```
fib(n::Integer) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)
```

`::Integer` 사양은 `n`이 [abstract](@ref man-abstract-types) `Integer` 유형의 하위 유형일 때만 호출 가능함을 의미합니다.

인수 유형 선언은 **일반적으로 성능에 영향을 미치지 않습니다**: 선언된 인수 유형이 무엇이든(있다면) 관계없이, Julia는 호출자가 전달한 실제 인수 유형에 대해 함수의 특수화된 버전을 컴파일합니다. 예를 들어, `fib(1)`을 호출하면 `Int` 인수에 대해 특별히 최적화된 `fib`의 특수화된 버전이 컴파일되며, 이후 `fib(7)` 또는 `fib(15)`가 호출될 때 재사용됩니다. (인수 유형 선언이 추가적인 컴파일러 특수화를 유발할 수 있는 드문 예외가 있습니다; 참조: [Be aware of when Julia avoids specializing](@ref).) Julia에서 인수 유형을 선언하는 가장 일반적인 이유는 대신:

  * **디스패치:** [Methods](@ref)에서 설명한 바와 같이, 서로 다른 인수 유형에 대해 함수의 서로 다른 버전("메서드")을 가질 수 있으며, 이 경우 인수 유형이 어떤 인수에 대해 어떤 구현이 호출되는지를 결정하는 데 사용됩니다. 예를 들어, `fib(x::Number) = ...`와 같이 모든 `Number` 유형에 대해 작동하는 완전히 다른 알고리즘을 구현할 수 있으며, 이를 통해 비정수 값으로 확장할 수 있습니다 [Binet's formula](https://en.wikipedia.org/wiki/Fibonacci_number#Binet%27s_formula).
  * **정확성:** 타입 선언은 함수가 특정 인수 타입에 대해서만 올바른 결과를 반환하는 경우 유용할 수 있습니다. 예를 들어, 인수 타입을 생략하고 `fib(n) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)`라고 작성하면, `fib(1.5)`는 조용히 비논리적인 답인 `1.0`을 반환하게 됩니다.
  * **명확성:** 타입 선언은 예상되는 인수에 대한 문서의 한 형태로 사용될 수 있습니다.

그러나 **인수 유형을 지나치게 제한하는 것은 일반적인 실수**로, 이는 함수의 적용 가능성을 불필요하게 제한하고 예상하지 못한 상황에서 재사용되는 것을 방지할 수 있습니다. 예를 들어, 위의 `fib(n::Integer)` 함수는 `Int` 인수(기계 정수)와 `BigInt` 임의 정밀도 정수 모두에 대해 동일하게 잘 작동합니다(자세한 내용은 [BigFloats and BigInts](@ref BigFloats-and-BigInts) 참조). 이는 피보나치 수가 기하급수적으로 빠르게 증가하고 `Int`와 같은 고정 정밀도 유형을 빠르게 오버플로우하기 때문에 특히 유용합니다(자세한 내용은 [Overflow behavior](@ref) 참조). 그러나 만약 우리가 함수를 `fib(n::Int)`로 선언했다면, 아무 이유 없이 `BigInt`에 대한 적용이 방지되었을 것입니다. 일반적으로 인수에 대해 가장 일반적인 적용 가능한 추상 유형을 사용해야 하며, **의심스러울 때는 인수 유형을 생략하세요**. 나중에 필요해지면 항상 인수 유형 사양을 추가할 수 있으며, 이를 생략한다고 해서 성능이나 기능이 희생되지 않습니다.

## The `return` Keyword

함수가 반환하는 값은 평가된 마지막 표현식의 값이며, 기본적으로 이는 함수 정의 본문의 마지막 표현식입니다. 이전 섹션의 예제 함수 `f`에서 이는 표현식 `x + y`의 값입니다. 다른 많은 언어와 마찬가지로 `return` 키워드는 함수가 즉시 반환하도록 하며, 반환되는 값의 표현식을 제공합니다:

```julia
function g(x, y)
    return x * y
    x + y
end
```

함수 정의는 대화형 세션에 입력할 수 있으므로 이러한 정의를 쉽게 비교할 수 있습니다:

```jldoctest
julia> f(x, y) = x + y
f (generic function with 1 method)

julia> function g(x, y)
           return x * y
           x + y
       end
g (generic function with 1 method)

julia> f(2, 3)
5

julia> g(2, 3)
6
```

물론, `g`와 같은 순수한 선형 함수 본문에서는 `return`의 사용이 무의미합니다. 왜냐하면 `x + y`라는 표현이 결코 평가되지 않기 때문입니다. 우리는 단순히 `x * y`를 함수의 마지막 표현으로 만들고 `return`을 생략할 수 있습니다. 그러나 다른 제어 흐름과 함께 사용할 때 `return`은 실제로 유용합니다. 여기, 예를 들어, 길이가 `x`와 `y`인 직각 삼각형의 빗변 길이를 계산하는 함수가 있습니다. 오버플로우를 피합니다:

```jldoctest
julia> function hypot(x, y)
           x = abs(x)
           y = abs(y)
           if x > y
               r = y/x
               return x*sqrt(1 + r*r)
           end
           if y == 0
               return zero(x)
           end
           r = x/y
           return y*sqrt(1 + r*r)
       end
hypot (generic function with 1 method)

julia> hypot(3, 4)
5.0
```

이 함수에서 반환할 수 있는 세 가지 가능한 반환 지점이 있으며, 이는 `x`와 `y`의 값에 따라 세 가지 다른 표현식의 값을 반환합니다. 마지막 줄의 `return`은 마지막 표현식이므로 생략할 수 있습니다.

### [Return type](@id man-functions-return-type)

함수 선언에서 `::` 연산자를 사용하여 반환 유형을 지정할 수 있습니다. 이는 반환 값을 지정된 유형으로 변환합니다.

```jldoctest
julia> function g(x, y)::Int8
           return x * y
       end;

julia> typeof(g(1, 2))
Int8
```

이 함수는 `x`와 `y`의 타입에 관계없이 항상 `Int8`을 반환합니다. 반환 타입에 대한 자세한 내용은 [Type Declarations](@ref)를 참조하세요.

반환 타입 선언은 **드물게 사용**됩니다. 일반적으로, Julia의 컴파일러가 반환 타입을 자동으로 추론할 수 있는 "타입 안정성" 함수 작성을 권장합니다. 자세한 내용은 [Performance Tips](@ref man-performance-tips) 장을 참조하세요.

### Returning nothing

값을 반환할 필요가 없는 함수(단지 부작용을 위해 사용되는 함수)의 경우, Julia의 관례는 값 [`nothing`](@ref)를 반환하는 것입니다:

```julia
function printx(x)
    println("x = $x")
    return nothing
end
```

이것은 `nothing`이 줄리아 키워드가 아니라 `Nothing` 유형의 단일 객체일 뿐이라는 의미에서 *관습*입니다. 또한, 위의 `printx` 함수 예제가 인위적이라는 것을 알 수 있습니다. 왜냐하면 `println`은 이미 `nothing`을 반환하므로 `return` 줄이 중복되기 때문입니다.

`return nothing` 표현에 대한 두 가지 가능한 축약형이 있습니다. 한편으로는 `return` 키워드가 암묵적으로 `nothing`을 반환하므로 혼자 사용할 수 있습니다. 다른 한편으로는 함수가 암묵적으로 마지막으로 평가된 표현식을 반환하므로, `nothing`이 마지막 표현식일 때 혼자 사용할 수 있습니다. `return nothing` 표현을 `return`이나 `nothing` 단독으로 사용하는 것보다 선호하는 것은 코딩 스타일의 문제입니다.

## Operators Are Functions

줄리아에서 대부분의 연산자는 특별한 구문을 지원하는 함수일 뿐입니다. (예외는 `&&` 및 `||`와 같은 특별한 평가 의미론을 가진 연산자입니다. 이러한 연산자는 [Short-Circuit Evaluation](@ref)이 연산자의 평가 전에 피연산자가 평가되지 않아야 하므로 함수가 될 수 없습니다.) 따라서 다른 함수와 마찬가지로 괄호로 묶인 인수 목록을 사용하여 적용할 수도 있습니다:

```jldoctest
julia> 1 + 2 + 3
6

julia> +(1, 2, 3)
6
```

중위 표기는 함수 적용 형식과 정확히 동등합니다. 사실, 전자는 내부적으로 함수 호출을 생성하기 위해 구문 분석됩니다. 이는 또한 [`+`](@ref) 및 [`*`](@ref)와 같은 연산자를 다른 함수 값과 마찬가지로 할당하고 전달할 수 있음을 의미합니다.

```jldoctest
julia> f = +;

julia> f(1, 2, 3)
6
```

`f`라는 이름 아래에서, 이 함수는 중위 표기법을 지원하지 않습니다.

## Operators With Special Names

몇 가지 특별한 표현은 비직관적인 이름을 가진 함수 호출에 해당합니다. 이러한 표현은:

| Expression            | Calls                                    |
|:--------------------- |:---------------------------------------- |
| `[A B C ...]`         | [`hcat`](@ref)                           |
| `[A; B; C; ...]`      | [`vcat`](@ref)                           |
| `[A B; C D; ...]`     | [`hvcat`](@ref)                          |
| `[A; B;; C; D;; ...]` | [`hvncat`](@ref)                         |
| `A'`                  | [`adjoint`](@ref)                        |
| `A[i]`                | [`getindex`](@ref)                       |
| `A[i] = x`            | [`setindex!`](@ref)                      |
| `A.n`                 | [`getproperty`](@ref Base.getproperty)   |
| `A.n = x`             | [`setproperty!`](@ref Base.setproperty!) |

`[A; B;; C; D;; ...]`와 유사한 표현이지만 두 개 이상의 연속된 `;`가 있는 경우도 `hvncat` 호출에 해당합니다.

## [Anonymous Functions](@id man-anonymous-functions)

줄리아의 함수는 [first-class objects](https://en.wikipedia.org/wiki/First-class_citizen): 변수에 할당할 수 있으며, 할당된 변수에서 표준 함수 호출 구문을 사용하여 호출할 수 있습니다. 함수는 인수로 사용될 수 있으며, 값으로 반환될 수 있습니다. 또한 이름 없이 익명으로 생성할 수 있으며, 다음 두 가지 구문 중 하나를 사용할 수 있습니다:

```jldoctest
julia> x -> x^2 + 2x - 1
#1 (generic function with 1 method)

julia> function (x)
           x^2 + 2x - 1
       end
#3 (generic function with 1 method)
```

각 문장은 하나의 인수 `x`를 받아들이고 해당 값에서 다항식 `x^2 + 2x - 1`의 값을 반환하는 함수를 생성합니다. 결과는 일반적인 함수이지만, 연속 번호를 기반으로 한 컴파일러 생성 이름을 가지고 있습니다.

익명 함수의 주요 용도는 다른 함수를 인수로 받는 함수에 전달하는 것입니다. 고전적인 예는 [`map`](@ref)로, 이는 배열의 각 값에 함수를 적용하고 결과 값을 포함하는 새로운 배열을 반환합니다:

```jldoctest
julia> map(round, [1.2, 3.5, 1.7])
3-element Vector{Float64}:
 1.0
 4.0
 2.0
```

이것은 [`map`](@ref)의 첫 번째 인수로 전달할 수 있는 이름이 있는 함수가 이미 존재하는 경우 괜찮습니다. 그러나 종종 즉시 사용할 수 있는 이름이 있는 함수가 존재하지 않습니다. 이러한 상황에서는 익명 함수 구성을 사용하여 이름 없이 단일 사용 함수 객체를 쉽게 생성할 수 있습니다:

```jldoctest
julia> map(x -> x^2 + 2x - 1, [1, 3, -1])
3-element Vector{Int64}:
  2
 14
 -2
```

익명 함수는 여러 인수를 받아 `(x,y,z)->2x+y-z` 구문을 사용하여 작성할 수 있습니다.

익명 함수에 대한 인수 유형 선언은 이름이 있는 함수와 동일하게 작동합니다. 예를 들어 `x::Integer->2x`. 익명 함수의 반환 유형은 지정할 수 없습니다.

인수가 없는 익명 함수는 `()->2+2`와 같이 작성할 수 있습니다. 인수가 없는 함수의 개념은 이상하게 보일 수 있지만, 결과를 미리 계산할 수 없거나 계산해서는 안 되는 경우에 유용합니다. 예를 들어, Julia에는 현재 시간을 초 단위로 반환하는 인수가 없는 [`time`](@ref) 함수가 있으며, 따라서 `seconds = ()->round(Int, time())`는 이 시간을 가장 가까운 정수로 반올림하여 변수 `seconds`에 할당하는 익명 함수입니다. 이 익명 함수가 `seconds()`로 호출될 때마다 현재 시간이 계산되어 반환됩니다.

## Tuples

줄리아에는 함수 인수 및 반환 값과 밀접하게 관련된 *튜플*이라는 내장 데이터 구조가 있습니다. 튜플은 고정 길이의 컨테이너로, 어떤 값이든 담을 수 있지만 수정할 수는 없습니다(즉, *불변*입니다). 튜플은 쉼표와 괄호로 구성되며, 인덱싱을 통해 접근할 수 있습니다:

```jldoctest
julia> (1, 1+1)
(1, 2)

julia> (1,)
(1,)

julia> x = (0.0, "hello", 6*7)
(0.0, "hello", 42)

julia> x[2]
"hello"
```

길이 1의 튜플은 쉼표와 함께 작성해야 합니다, `(1,)`, 왜냐하면 `(1)`은 단순히 괄호로 묶인 값이기 때문입니다. `()`는 빈 (길이 0) 튜플을 나타냅니다.

## Named Tuples

튜플의 구성 요소는 선택적으로 이름을 지정할 수 있으며, 이 경우 *명명된 튜플*이 생성됩니다:

```jldoctest
julia> x = (a=2, b=1+2)
(a = 2, b = 3)

julia> x[1]
2

julia> x.a
2
```

명명된 튜플의 필드는 점 표기법(`x.a`)을 사용하여 이름으로 접근할 수 있으며, 일반 인덱싱 표기법(`x[1]` 또는 `x[:a]`)도 사용할 수 있습니다.

## [Destructuring Assignment and Multiple Return Values](@id destructuring-assignment)

할당의 왼쪽에는 괄호로 감싸일 수 있는 쉼표로 구분된 변수 목록이 올 수 있습니다: 오른쪽의 값은 각 변수를 차례로 반복하여 할당함으로써 *구조 분해*됩니다:

```jldoctest
julia> (a, b, c) = 1:3
1:3

julia> b
2
```

오른쪽의 값은 반복자여야 하며(참조: [Iteration interface](@ref man-interface-iteration)), 왼쪽의 변수 수만큼은 최소한 길어야 합니다(반복자의 초과 요소는 무시됩니다).

이것은 튜플이나 다른 반복 가능한 값을 반환하여 함수에서 여러 값을 반환하는 데 사용할 수 있습니다. 예를 들어, 다음 함수는 두 개의 값을 반환합니다:

```jldoctest foofunc
julia> function foo(a, b)
           a+b, a*b
       end
foo (generic function with 1 method)
```

대화형 세션에서 반환 값을 어디에도 할당하지 않고 호출하면 반환된 튜플을 볼 수 있습니다:

```jldoctest foofunc
julia> foo(2, 3)
(5, 6)
```

구조 분해 할당은 각 값을 변수로 추출합니다:

```jldoctest foofunc
julia> x, y = foo(2, 3)
(5, 6)

julia> x
5

julia> y
6
```

또 다른 일반적인 용도는 변수를 교환하는 것입니다:

```jldoctest foofunc
julia> y, x = x, y
(5, 6)

julia> x
6

julia> y
5
```

필요한 요소의 하위 집합만 필요한 경우, 일반적인 관례는 무시된 요소를 오직 밑줄 `_`로만 구성된 변수에 할당하는 것입니다 (이는 다른 경우에는 유효하지 않은 변수 이름입니다, [Allowed Variable Names](@ref man-allowed-variable-names) 참조):

```jldoctest
julia> _, _, _, d = 1:10
1:10

julia> d
4
```

다른 유효한 왼쪽 표현식은 할당 목록의 요소로 사용될 수 있으며, 이는 [`setindex!`](@ref) 또는 [`setproperty!`](@ref)를 호출하거나 반복자의 개별 요소를 재귀적으로 구조 분해할 수 있습니다:

```jldoctest
julia> X = zeros(3);

julia> X[1], (a, b) = (1, (2, 3))
(1, (2, 3))

julia> X
3-element Vector{Float64}:
 1.0
 0.0
 0.0

julia> a
2

julia> b
3
```

!!! compat "Julia 1.6"
    `...` 할당이 필요합니다 Julia 1.6


할당 목록의 마지막 기호가 `...`로 접미사로 붙어 있으면 (*슬러핑*이라고 함), 오른쪽 반복자의 나머지 요소로 구성된 컬렉션 또는 지연 반복자가 할당됩니다:

```jldoctest
julia> a, b... = "hello"
"hello"

julia> a
'h': ASCII/Unicode U+0068 (category Ll: Letter, lowercase)

julia> b
"ello"

julia> a, b... = Iterators.map(abs2, 1:4)
Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4)

julia> a
1

julia> b
Base.Iterators.Rest{Base.Generator{UnitRange{Int64}, typeof(abs2)}, Int64}(Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4), 1)
```

[`Base.rest`](@ref)에 대한 세부정보는 특정 반복자에 대한 정확한 처리 및 사용자 지정을 참조하십시오.

!!! compat "Julia 1.9"
    `...` 할당의 비최종 위치는 Julia 1.9를 요구합니다.


과제에서 슬러핑은 다른 어떤 위치에서도 발생할 수 있습니다. 그러나 컬렉션의 끝을 슬러핑하는 것과는 달리, 이것은 항상 열망적일 것입니다.

```jldoctest
julia> a, b..., c = 1:5
1:5

julia> a
1

julia> b
3-element Vector{Int64}:
 2
 3
 4

julia> c
5

julia> front..., tail = "Hi!"
"Hi!"

julia> front
"Hi"

julia> tail
'!': ASCII/Unicode U+0021 (category Po: Punctuation, other)
```

이것은 함수 [`Base.split_rest`](@ref)의 관점에서 구현됩니다.

가변 인수 함수 정의의 경우, 슬러핑은 여전히 마지막 위치에서만 허용된다는 점에 유의하세요. 그러나 [single argument destructuring](@ref man-argument-destructuring)에는 적용되지 않으며, 이는 메서드 디스패치에 영향을 미치지 않습니다:

```jldoctest
julia> f(x..., y) = x
ERROR: syntax: invalid "..." on non-final argument
Stacktrace:
[...]

julia> f((x..., y)) = x
f (generic function with 1 method)

julia> f((1, 2, 3))
(1, 2)
```

## Property destructuring

반복에 기반한 구조 분해 대신, 할당의 오른쪽도 속성 이름을 사용하여 구조 분해할 수 있습니다. 이는 NamedTuples의 구문을 따르며, `getproperty`를 사용하여 왼쪽의 각 변수에 할당의 오른쪽에서 동일한 이름을 가진 속성을 할당함으로써 작동합니다:

```jldoctest
julia> (; b, a) = (a=1, b=2, c=3)
(a = 1, b = 2, c = 3)

julia> a
1

julia> b
2
```

## [Argument destructuring](@id man-argument-destructuring)

함수 인수 내에서도 구조 분해 할당 기능을 사용할 수 있습니다. 함수 인수 이름이 기호 대신 튜플(예: `(x, y)`)로 작성되면, `(x, y) = argument`라는 할당이 자동으로 삽입됩니다:

```julia-repl
julia> minmax(x, y) = (y < x) ? (y, x) : (x, y)

julia> gap((min, max)) = max - min

julia> gap(minmax(10, 2))
8
```

`gap`의 정의에서 추가적인 괄호 세트를 주목하세요. 그것이 없으면 `gap`은 두 개의 인수를 가지는 함수가 되어 이 예제가 작동하지 않을 것입니다.

유사하게, 속성 구조 분해는 함수 인수에도 사용할 수 있습니다:

```julia-repl
julia> foo((; x, y)) = x + y
foo (generic function with 1 method)

julia> foo((x=1, y=2))
3

julia> struct A
           x
           y
       end

julia> foo(A(3, 4))
7
```

익명 함수의 경우, 단일 인수를 구조 분해 할당하려면 추가적인 쉼표가 필요합니다:

```
julia> map(((x, y),) -> x + y, [(1, 2), (3, 4)])
2-element Array{Int64,1}:
 3
 7
```

## Varargs Functions

임의의 수의 인수를 받을 수 있는 함수를 작성하는 것은 종종 편리합니다. 이러한 함수는 전통적으로 "varargs" 함수로 알려져 있으며, 이는 "가변 인수"의 약자입니다. 마지막 위치 인수 뒤에 생략 부호(...)를 추가하여 varargs 함수를 정의할 수 있습니다:

```jldoctest barfunc
julia> bar(a, b, x...) = (a, b, x)
bar (generic function with 1 method)
```

변수 `a`와 `b`는 일반적으로 첫 번째 두 인수 값에 바인딩되고, 변수 `x`는 `bar`에 첫 번째 두 인수 이후에 전달된 0개 이상의 값의 반복 가능한 컬렉션에 바인딩됩니다:

```jldoctest barfunc
julia> bar(1, 2)
(1, 2, ())

julia> bar(1, 2, 3)
(1, 2, (3,))

julia> bar(1, 2, 3, 4)
(1, 2, (3, 4))

julia> bar(1, 2, 3, 4, 5, 6)
(1, 2, (3, 4, 5, 6))
```

모든 경우에서 `x`는 `bar`에 전달된 후행 값들의 튜플에 바인딩됩니다.

변수 인수로 전달되는 값의 수를 제한하는 것이 가능합니다. 이는 나중에 [Parametrically-constrained Varargs methods](@ref)에서 논의될 것입니다.

반대로, 반복 가능한 컬렉션에 포함된 값을 개별 인수로 함수 호출에 "펼치는" 것이 종종 유용합니다. 이를 위해서도 `...`를 사용하지만, 함수 호출에서 사용합니다:

```jldoctest barfunc
julia> x = (3, 4)
(3, 4)

julia> bar(1, 2, x...)
(1, 2, (3, 4))
```

이 경우 값의 튜플이 가변 인수가 가는 정확한 위치에 varargs 호출로 분할됩니다. 그러나 반드시 그럴 필요는 없습니다:

```jldoctest barfunc
julia> x = (2, 3, 4)
(2, 3, 4)

julia> bar(1, x...)
(1, 2, (3, 4))

julia> x = (1, 2, 3, 4)
(1, 2, 3, 4)

julia> bar(x...)
(1, 2, (3, 4))
```

또한, 함수 호출에 스플랫된 iterable 객체는 튜플일 필요가 없습니다:

```jldoctest barfunc
julia> x = [3, 4]
2-element Vector{Int64}:
 3
 4

julia> bar(1, 2, x...)
(1, 2, (3, 4))

julia> x = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> bar(x...)
(1, 2, (3, 4))
```

또한, 인수가 스플랫된 함수는 가변 인자 함수일 필요는 없습니다(비록 종종 그렇긴 하지만):

```jldoctest
julia> baz(a, b) = a + b;

julia> args = [1, 2]
2-element Vector{Int64}:
 1
 2

julia> baz(args...)
3

julia> args = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> baz(args...)
ERROR: MethodError: no method matching baz(::Int64, ::Int64, ::Int64)
The function `baz` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  baz(::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

보시다시피, 스플랫된 컨테이너에 잘못된 수의 요소가 있으면 함수 호출이 실패합니다. 이는 너무 많은 인수가 명시적으로 주어졌을 때와 마찬가지입니다.

## Optional Arguments

함수 인수에 대해 합리적인 기본값을 제공하는 것이 종종 가능합니다. 이렇게 하면 사용자가 매 호출마다 모든 인수를 전달할 필요가 없습니다. 예를 들어, `Dates` 모듈의 [`Date(y, [m, d])`](@ref) 함수는 주어진 연도 `y`, 월 `m` 및 일 `d`에 대한 `Date` 유형을 생성합니다. 그러나 `m` 및 `d` 인수는 선택 사항이며 기본값은 `1`입니다. 이 동작은 간결하게 다음과 같이 표현할 수 있습니다:

```jldoctest date_default_args
julia> using Dates

julia> function date(y::Int64, m::Int64=1, d::Int64=1)
           err = Dates.validargs(Date, y, m, d)
           err === nothing || throw(err)
           return Date(Dates.UTD(Dates.totaldays(y, m, d)))
       end
date (generic function with 3 methods)
```

관찰해보면, 이 정의는 `Date` 함수의 다른 메서드를 호출하는데, 이 메서드는 `UTInstant{Day}` 타입의 하나의 인수를 받습니다.

이 정의에 따라, 함수는 하나, 두 개 또는 세 개의 인수로 호출될 수 있으며, 인수가 하나 또는 두 개만 지정될 경우 `1`이 자동으로 전달됩니다:

```jldoctest date_default_args
julia> date(2000, 12, 12)
2000-12-12

julia> date(2000, 12)
2000-12-01

julia> date(2000)
2000-01-01
```

선택적 인수는 실제로 서로 다른 수의 인수를 가진 여러 메서드 정의를 작성하기 위한 편리한 구문입니다 (참조: [Note on Optional and keyword Arguments](@ref)). 이는 `date` 함수 예제를 통해 `methods` 함수를 호출하여 확인할 수 있습니다:

```julia-repl
julia> methods(date)
# 3 methods for generic function "date":
[1] date(y::Int64) in Main at REPL[1]:1
[2] date(y::Int64, m::Int64) in Main at REPL[1]:1
[3] date(y::Int64, m::Int64, d::Int64) in Main at REPL[1]:1
```

## Keyword Arguments

일부 함수는 많은 수의 인수를 필요로 하거나 많은 수의 동작을 가질 수 있습니다. 이러한 함수를 호출하는 방법을 기억하는 것은 어려울 수 있습니다. 키워드 인수는 인수를 위치가 아닌 이름으로 식별할 수 있게 하여 이러한 복잡한 인터페이스를 더 쉽게 사용하고 확장할 수 있도록 도와줍니다.

예를 들어, 선을 그리는 `plot` 함수가 있다고 가정해 보겠습니다. 이 함수는 선 스타일, 너비, 색상 등을 제어하기 위한 많은 옵션을 가질 수 있습니다. 만약 키워드 인수를 허용한다면, 가능한 호출은 `plot(x, y, width=2)`와 같이 보일 수 있으며, 여기서 우리는 선 너비만 지정하기로 선택했습니다. 이는 두 가지 목적을 수행합니다. 호출이 더 읽기 쉬워지며, 인수의 의미를 레이블로 붙일 수 있습니다. 또한 많은 수의 인수 중에서 임의의 하위 집합을 어떤 순서로든 전달할 수 있게 됩니다.

키워드 인수가 있는 함수는 서명에서 세미콜론을 사용하여 정의됩니다:

```julia
function plot(x, y; style="solid", width=1, color="black")
    ###
end
```

함수가 호출될 때 세미콜론은 선택 사항입니다: `plot(x, y, width=2)` 또는 `plot(x, y; width=2)`를 호출할 수 있지만, 전자의 스타일이 더 일반적입니다. 명시적인 세미콜론은 아래에 설명된 대로 varargs 또는 계산된 키워드를 전달할 때만 필요합니다.

키워드 인수의 기본값은 필요할 때만 평가됩니다(해당 키워드 인수가 전달되지 않았을 때) 및 왼쪽에서 오른쪽으로 순서대로 평가됩니다. 따라서 기본 표현식은 이전 키워드 인수를 참조할 수 있습니다.

키워드 인수의 유형은 다음과 같이 명시적으로 만들 수 있습니다:

```julia
function f(; x::Int=1)
    ###
end
```

키워드 인수는 가변 인수 함수에서도 사용할 수 있습니다:

```julia
function plot(x...; style="solid")
    ###
end
```

추가 키워드 인자는 `...`를 사용하여 수집할 수 있습니다. 이는 가변 인자 함수에서와 같습니다:

```julia
function f(x; y=0, kwargs...)
    ###
end
```

`f` 내부에서 `kwargs`는 명명된 튜플에 대한 불변 키-값 반복자입니다. 명명된 튜플(및 `Symbol` 키를 가진 사전, 첫 번째 값이 기호인 두 값 컬렉션을 생성하는 기타 반복자)은 호출 시 세미콜론을 사용하여 키워드 인수로 전달될 수 있습니다. 예: `f(x, z=1; kwargs...)`.

키워드 인수가 메서드 정의에서 기본값을 할당받지 않으면 *필수*입니다: 호출자가 값을 할당하지 않으면 [`UndefKeywordError`](@ref) 예외가 발생합니다:

```julia
function f(x; y)
    ###
end
f(3, y=5) # ok, y is assigned
f(3)      # throws UndefKeywordError(:y)
```

세미콜론 뒤에 `key => value` 표현식을 전달할 수도 있습니다. 예를 들어, `plot(x, y; :width => 2)`는 `plot(x, y, width=2)`와 동일합니다. 이는 키워드 이름이 런타임에 계산되는 상황에서 유용합니다.

세미콜론 뒤에 빈 식별자 또는 점 표현식이 나타나면, 키워드 인수 이름은 식별자 또는 필드 이름에 의해 암시됩니다. 예를 들어 `plot(x, y; width)`는 `plot(x, y; width=width)`와 같고, `plot(x, y; options.width)`는 `plot(x, y; width=options.width)`와 같습니다.

키워드 인수의 특성 덕분에 동일한 인수를 여러 번 지정할 수 있습니다. 예를 들어, `plot(x, y; options..., width=2)` 호출에서 `options` 구조체에도 `width`에 대한 값이 포함될 수 있습니다. 이 경우 가장 오른쪽에 있는 항목이 우선권을 가지며, 이 예제에서는 `width`가 확실히 값 `2`를 갖습니다. 그러나 동일한 키워드 인수를 여러 번 명시적으로 지정하는 것은 허용되지 않으며, 예를 들어 `plot(x, y, width=2, width=3)`와 같은 경우 구문 오류가 발생합니다.

## Evaluation Scope of Default Values

선택적 및 키워드 인수의 기본 표현식이 평가될 때, 오직 *이전* 인수만 범위에 있습니다. 예를 들어, 다음과 같은 정의가 주어졌을 때:

```julia
function f(x, a=b, b=1)
    ###
end
```

`a=b`에서 `b`는 이후의 인수 `b`가 아닌 외부 범위의 `b`를 참조합니다.

## Do-Block Syntax for Function Arguments

함수를 다른 함수의 인수로 전달하는 것은 강력한 기법이지만, 그 문법은 항상 편리하지 않습니다. 함수 인수가 여러 줄을 요구할 때 이러한 호출은 특히 작성하기 불편합니다. 예를 들어, 여러 경우가 있는 함수에서 [`map`](@ref)를 호출하는 것을 고려해 보십시오:

```julia
map(x->begin
           if x < 0 && iseven(x)
               return 0
           elseif x == 0
               return 1
           else
               return x
           end
       end,
    [A, B, C])
```

Julia는 이 코드를 더 명확하게 다시 작성하기 위해 예약어 `do`를 제공합니다:

```julia
map([A, B, C]) do x
    if x < 0 && iseven(x)
        return 0
    elseif x == 0
        return 1
    else
        return x
    end
end
```

`do x` 구문은 인수 `x`를 가진 익명 함수를 생성하고, 이 익명 함수를 "외부" 함수의 첫 번째 인수로 전달합니다 - 이 예제에서는 [`map`](@ref)입니다. 마찬가지로, `do a,b`는 두 개의 인수를 가진 익명 함수를 생성합니다. `do (a,b)`는 튜플을 분해할 인수로 가지는 하나의 인수를 가진 익명 함수를 생성합니다. 일반적인 `do`는 그 뒤에 오는 것이 `() -> ...` 형태의 익명 함수임을 선언합니다.

이러한 인수가 초기화되는 방식은 "외부" 함수에 따라 다릅니다. 여기서 [`map`](@ref)는 순차적으로 `x`를 `A`, `B`, `C`로 설정하고, 각 값에 대해 익명 함수를 호출합니다. 이는 `map(func, [A, B, C])` 구문에서 발생하는 것과 같습니다.

이 구문은 함수 사용을 더 쉽게 하여 언어를 효과적으로 확장할 수 있게 해줍니다. 호출이 일반 코드 블록처럼 보이기 때문입니다. [`map`](@ref)와는 매우 다른 여러 가지 가능한 용도가 있으며, 시스템 상태 관리와 같은 용도가 있습니다. 예를 들어, 열린 파일이 결국 닫히도록 보장하는 코드를 실행하는 [`open`](@ref)의 버전이 있습니다:

```julia
open("outfile", "w") do io
    write(io, data)
end
```

이는 다음 정의에 의해 달성됩니다:

```julia
function open(f::Function, args...)
    io = open(args...)
    try
        f(io)
    finally
        close(io)
    end
end
```

여기서 [`open`](@ref)는 파일을 쓰기 위해 열고, 그 다음에 `do ... end` 블록에서 정의한 익명 함수에 결과 출력 스트림을 전달합니다. 함수가 종료되면 `4d61726b646f776e2e436f64652822222c20226f70656e2229_40726566`는 함수가 정상적으로 종료되었든 예외가 발생했든 관계없이 스트림이 제대로 닫히도록 보장합니다. (`try/finally` 구조는 [Control Flow](@ref)에서 설명될 것입니다.)

`do` 블록 구문을 사용하면 사용자 함수의 인수가 어떻게 초기화되는지 알기 위해 문서나 구현을 확인하는 데 도움이 됩니다.

`do` 블록은 다른 내부 함수와 마찬가지로 자신의 외부 범위에서 변수를 "캡처"할 수 있습니다. 예를 들어, `open...do`의 위 예제에서 변수 `data`는 외부 범위에서 캡처됩니다. 캡처된 변수는 [performance tips](@ref man-performance-captured)에서 논의된 것처럼 성능 문제를 일으킬 수 있습니다.

## Function composition and piping

줄리아에서 함수는 조합하거나 파이핑(체이닝)하여 함께 사용할 수 있습니다.

함수 합성은 함수를 함께 결합하고 결과로 얻은 합성을 인수에 적용하는 것입니다. 함수 합성 연산자(`∘`)를 사용하여 함수를 합성하므로, `(f ∘ g)(args...; kw...)`는 `f(g(args...; kw...))`와 동일합니다.

REPL 및 적절히 구성된 편집기에서 조합 연산자를 입력하려면 `\circ<tab>`를 사용하세요.

예를 들어, `sqrt`와 `+` 함수를 다음과 같이 조합할 수 있습니다:

```jldoctest
julia> (sqrt ∘ +)(3, 6)
3.0
```

이것은 먼저 숫자를 더한 다음 결과의 제곱근을 찾습니다.

다음 예제는 세 개의 함수를 조합하고 결과를 문자열 배열에 매핑합니다:

```jldoctest
julia> map(first ∘ reverse ∘ uppercase, split("you can compose functions like this"))
6-element Vector{Char}:
 'U': ASCII/Unicode U+0055 (category Lu: Letter, uppercase)
 'N': ASCII/Unicode U+004E (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
```

함수 체이닝(때때로 "파이핑" 또는 "파이프 사용"이라고 불림)은 데이터를 후속 함수로 전송하기 위해 함수를 이전 함수의 출력에 적용하는 것입니다:

```jldoctest
julia> 1:10 |> sum |> sqrt
7.416198487095663
```

여기서 `sum`에 의해 생성된 총합이 `sqrt` 함수에 전달됩니다. 동등한 조합은 다음과 같습니다:

```jldoctest
julia> (sqrt ∘ sum)(1:10)
7.416198487095663
```

파이프 연산자는 브로드캐스팅과 함께 `.|>`로 사용할 수 있으며, 이는 체이닝/파이핑과 점 벡터화 구문(아래에 설명됨)의 유용한 조합을 제공합니다.

```jldoctest
julia> ["a", "list", "of", "strings"] .|> [uppercase, reverse, titlecase, length]
4-element Vector{Any}:
  "A"
  "tsil"
  "Of"
 7
```

익명 함수와 파이프를 결합할 때, 후속 파이프가 익명 함수의 본문의 일부로 해석되지 않도록 하려면 괄호를 사용해야 합니다. 비교:

```jldoctest
julia> 1:3 .|> (x -> x^2) |> sum |> sqrt
3.7416573867739413

julia> 1:3 .|> x -> x^2 |> sum |> sqrt
3-element Vector{Float64}:
 1.0
 2.0
 3.0
```

## [Dot Syntax for Vectorizing Functions](@id man-vectorized)

기술 컴퓨팅 언어에서는 주어진 함수 `f(x)`를 배열 `A`의 각 요소에 적용하여 새로운 배열을 생성하는 "벡터화된" 버전의 함수가 일반적입니다. 이러한 구문은 데이터 처리에 편리하지만, 다른 언어에서는 성능을 위해 벡터화가 종종 필요합니다. 루프가 느리면, 함수의 "벡터화된" 버전은 저수준 언어로 작성된 빠른 라이브러리 코드를 호출할 수 있습니다. Julia에서는 성능을 위해 벡터화된 함수가 *필수*는 아니며, 실제로 자신의 루프를 작성하는 것이 종종 유익합니다(참조: [Performance Tips](@ref man-performance-tips)), 하지만 여전히 편리할 수 있습니다. 따라서 *모든* Julia 함수 `f`는 구문 `f.(A)`를 사용하여 모든 배열(또는 다른 컬렉션)에 요소별로 적용될 수 있습니다. 예를 들어, `sin`은 다음과 같이 벡터 `A`의 모든 요소에 적용될 수 있습니다:

```jldoctest
julia> A = [1.0, 2.0, 3.0]
3-element Vector{Float64}:
 1.0
 2.0
 3.0

julia> sin.(A)
3-element Vector{Float64}:
 0.8414709848078965
 0.9092974268256817
 0.1411200080598672
```

물론, `f`의 전문화된 "벡터" 메서드를 작성하면 점을 생략할 수 있습니다. 예를 들어 `f(A::AbstractArray) = map(f, A)`와 같이 작성하면 `f.(A)`와 동일하게 효율적입니다. `f.(A)` 구문이 가지는 장점은 어떤 함수가 벡터화 가능한지를 라이브러리 작성자가 미리 결정할 필요가 없다는 점입니다.

더 일반적으로, `f.(args...)`는 실제로 `broadcast(f, args...)`와 동등하며, 이는 서로 다른 형태의 여러 배열이나 배열과 스칼라의 혼합에 대해 작업할 수 있게 해줍니다 (자세한 내용은 [Broadcasting](@ref) 참조). 예를 들어, `f(x, y) = 3x + 4y`가 있다면, `f.(pi, A)`는 `A`의 각 `a`에 대해 `f(pi, a)`를 포함하는 새로운 배열을 반환하고, `f.(vector1, vector2)`는 각 인덱스 `i`에 대해 `f(vector1[i], vector2[i])`를 포함하는 새로운 벡터를 반환합니다 (벡터의 길이가 다르면 예외가 발생합니다).

```jldoctest
julia> f(x, y) = 3x + 4y;

julia> A = [1.0, 2.0, 3.0];

julia> B = [4.0, 5.0, 6.0];

julia> f.(pi, A)
3-element Vector{Float64}:
 13.42477796076938
 17.42477796076938
 21.42477796076938

julia> f.(A, B)
3-element Vector{Float64}:
 19.0
 26.0
 33.0
```

키워드 인자는 브로드캐스트되지 않고, 각 함수 호출에 단순히 전달됩니다. 예를 들어, `round.(x, digits=3)`는 `broadcast(x -> round(x, digits=3), x)`와 동일합니다.

게다가, *중첩된* `f.(args...)` 호출은 *융합*되어 단일 `broadcast` 루프로 처리됩니다. 예를 들어, `sin.(cos.(X))`는 `broadcast(x -> sin(cos(x)), X)`와 동등하며, 이는 `[sin(cos(x)) for x in X]`와 유사합니다: `X`에 대해 단일 루프만 존재하며, 결과를 위해 단일 배열이 할당됩니다. [대조적으로, 일반적인 "벡터화된" 언어에서 `sin(cos(X))`는 먼저 `tmp=cos(X)`를 위해 임시 배열 하나를 할당한 다음, 별도의 루프에서 `sin(tmp)`를 계산하여 두 번째 배열을 할당합니다.] 이 루프 융합은 발생할 수도 있고 발생하지 않을 수도 있는 컴파일러 최적화가 아니라, 중첩된 `f.(args...)` 호출이 발견될 때마다 *구문적 보장*입니다. 기술적으로, 융합은 "비점" 함수 호출이 발견되는 즉시 중단됩니다; 예를 들어, `sin.(sort(cos.(X)))`에서는 개입하는 `sort` 함수 때문에 `sin`과 `cos` 루프를 병합할 수 없습니다.

마지막으로, 최대 효율성은 일반적으로 벡터화된 연산의 출력 배열이 *미리 할당*될 때 달성됩니다. 이렇게 하면 반복 호출 시 결과를 위해 새로운 배열을 계속 할당하지 않게 됩니다 (참조: [Pre-allocating outputs](@ref)). 이를 위한 편리한 구문은 `X .= ...`이며, 이는 `broadcast!(identity, X, ...)`와 동등하지만, 위에서 언급한 것처럼 `broadcast!` 루프가 모든 중첩된 "점" 호출과 융합됩니다. 예를 들어, `X .= sin.(Y)`는 `broadcast!(sin, X, Y)`와 동등하며, `X`를 `sin.(Y)`로 제자리에서 덮어씁니다. 왼쪽 항이 배열 인덱싱 표현식인 경우, 예를 들어 `X[begin+1:end] .= sin.(Y)`라면, 이는 `view`에 대한 `broadcast!`로 변환됩니다. 예를 들어, `broadcast!(sin, view(X, firstindex(X)+1:lastindex(X)), Y)`와 같이 왼쪽 항이 제자리에서 업데이트됩니다.

여러 작업 및 함수 호출에 점을 추가하는 것이 번거롭고 읽기 어려운 코드를 초래할 수 있으므로, 표현식에서 *모든* 함수 호출, 작업 및 할당을 "점이 있는" 버전으로 변환하기 위해 매크로 [`@.`](@ref @__dot__)가 제공됩니다.

```jldoctest
julia> Y = [1.0, 2.0, 3.0, 4.0];

julia> X = similar(Y); # pre-allocate output array

julia> @. X = sin(cos(Y)) # equivalent to X .= sin.(cos.(Y))
4-element Vector{Float64}:
  0.5143952585235492
 -0.4042391538522658
 -0.8360218615377305
 -0.6080830096407656
```

이진(또는 단항) 연산자 `.+`는 동일한 메커니즘으로 처리됩니다: 이들은 `broadcast` 호출과 동등하며 다른 중첩된 "점" 호출과 융합됩니다. `X .+= Y` 등은 `X .= X .+ Y`와 동등하며, 융합된 제자리 할당 결과를 생성합니다; 또한 [dot operators](@ref man-dot-operators)도 참조하십시오.

[`|>`](@ref)를 사용하여 함수 체이닝과 점 연산을 결합할 수도 있습니다. 다음 예를 참조하세요:

```jldoctest
julia> 1:5 .|> [x->x^2, inv, x->2*x, -, isodd]
5-element Vector{Real}:
    1
    0.5
    6
   -4
 true
```

모든 함수는 결과의 각 요소에 대해 항상 호출됩니다. 따라서 `X .+ σ .* randn.()`는 배열 `X`의 각 요소에 독립적이고 동일하게 샘플링된 랜덤 값의 마스크를 추가하지만, `X .+ σ .* randn()`은 각 요소에 *같은* 랜덤 샘플을 추가합니다. 브로드캐스트 반복의 하나 이상의 축을 따라 융합된 계산이 상수인 경우, 중간 값을 할당하여 계산 수를 줄이는 공간-시간 절충을 활용할 수 있습니다. 자세한 내용은 [performance tips](@ref man-performance-unfuse)를 참조하세요.

## Further Reading

여기서 언급해야 할 것은 이것이 함수 정의에 대한 완전한 그림이 아니라는 점입니다. Julia는 정교한 타입 시스템을 가지고 있으며 인수 타입에 대한 다중 디스패치를 허용합니다. 여기서 제공된 예제는 인수에 대한 타입 주석이 없으므로 모든 타입의 인수에 적용될 수 있습니다. 타입 시스템은 [Types](@ref man-types)에서 설명되어 있으며, 런타임 인수 타입에 대한 다중 디스패치에 의해 선택된 메서드로 함수를 정의하는 것은 [Methods](@ref)에서 설명되어 있습니다.
