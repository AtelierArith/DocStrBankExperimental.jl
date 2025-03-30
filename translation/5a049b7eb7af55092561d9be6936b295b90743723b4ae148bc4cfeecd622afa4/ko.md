# Julia Functions

이 문서는 함수, 메서드 정의 및 메서드 테이블이 작동하는 방식을 설명합니다.

## Method Tables

모든 함수는 줄리아에서 제네릭 함수입니다. 제네릭 함수는 개념적으로 단일 함수이지만, 여러 정의 또는 메소드로 구성됩니다. 제네릭 함수의 메소드는 메소드 테이블에 저장됩니다. 메소드 테이블(타입 `MethodTable`)은 `TypeName`과 연결되어 있습니다. `TypeName`은 매개변수화된 타입의 집합을 설명합니다. 예를 들어 `Complex{Float32}`와 `Complex{Float64}`는 동일한 `Complex` 타입 이름 객체를 공유합니다.

모든 객체는 호출 가능성이 있으며, 이는 모든 객체가 타입을 가지고 있고, 그 타입은 `TypeName`을 가지고 있기 때문입니다.

## [Function calls](@id Function-calls)

주어진 호출 `f(x, y)`에 대해 다음 단계가 수행됩니다: 첫째, 사용할 메서드 테이블에 `typeof(f).name.mt`로 접근합니다. 둘째, 인수 튜플 타입이 형성됩니다, `Tuple{typeof(f), typeof(x), typeof(y)}`. 함수 자체의 타입이 첫 번째 요소라는 점에 유의하세요. 이는 타입이 매개변수를 가질 수 있기 때문에 디스패치에 참여해야 합니다. 이 튜플 타입은 메서드 테이블에서 조회됩니다.

이 디스패치 프로세스는 `jl_apply_generic`에 의해 수행되며, 두 개의 인수를 받습니다: 값 `f`, `x`, `y`의 배열에 대한 포인터와 값의 수(이 경우 3)입니다.

시스템 전반에 걸쳐 함수와 인수 목록을 처리하는 두 가지 종류의 API가 있습니다: 함수와 인수를 별도로 받는 API와 단일 인수 구조를 받는 API입니다. 첫 번째 종류의 API에서는 "인수" 부분이 *함수*에 대한 정보를 포함하지 않으며, 이는 별도로 전달됩니다. 두 번째 종류의 API에서는 함수가 인수 구조의 첫 번째 요소입니다.

예를 들어, 호출을 수행하는 다음 함수는 `args` 포인터만을 받아들이므로, args 배열의 첫 번째 요소는 호출할 함수가 됩니다:

```c
jl_value_t *jl_apply(jl_value_t **args, uint32_t nargs)
```

이 동일한 기능에 대한 진입점은 함수를 별도로 수용하므로 `args` 배열에는 함수가 포함되지 않습니다:

```c
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs);
```

## Adding methods

주어진 위의 디스패치 프로세스에 따르면, 새로운 메서드를 추가하는 데 필요한 것은 (1) 튜플 타입과 (2) 메서드 본체에 대한 코드입니다. `jl_method_def`는 이 작업을 구현합니다. `jl_method_table_for`는 첫 번째 인수의 타입이 될 수 있는 것에서 관련 메서드 테이블을 추출하기 위해 호출됩니다. 이는 디스패치 중의 해당 절차보다 훨씬 복잡합니다. 왜냐하면 인수 튜플 타입이 추상적일 수 있기 때문입니다. 예를 들어, 우리는 다음과 같이 정의할 수 있습니다:

```julia
(::Union{Foo{Int},Foo{Int8}})(x) = 0
```

모든 가능한 매칭 방법이 동일한 메서드 테이블에 속하기 때문에 작동합니다.

## Creating generic functions

모든 객체가 호출 가능하므로 일반 함수를 생성하는 데 특별한 것이 필요하지 않습니다. 따라서 `jl_new_generic_function`은 단순히 `Function`의 새로운 단일 인스턴스(0 크기) 하위 유형을 생성하고 그 인스턴스를 반환합니다. 함수는 디버그 정보와 객체를 출력할 때 사용되는 기억하기 쉬운 "표시 이름"을 가질 수 있습니다. 예를 들어 `Base.sin`의 이름은 `sin`입니다. 관례적으로 생성된 *유형*의 이름은 함수 이름과 동일하며, `#`가 앞에 붙습니다. 따라서 `typeof(sin)`은 `Base.#sin`입니다.

## Closures

클로저는 캡처된 변수에 해당하는 필드 이름을 가진 호출 가능한 객체입니다. 예를 들어, 다음 코드는:

```julia
function adder(x)
    return y->x+y
end
```

대략적으로 다음과 같이 낮아집니다:

```julia
struct ##1{T}
    x::T
end

(_::##1)(y) = _.x + y

function adder(x)
    return ##1(x)
end
```

## Constructors

생성자 호출은 단순히 타입에 대한 호출입니다. `Type`의 메서드 테이블에는 모든 생성자 정의가 포함되어 있습니다. 현재 `Type`, `UnionAll`, `Union`, 및 `DataType`의 모든 하위 타입은 특별한 arrangement를 통해 메서드 테이블을 공유하고 있습니다.

## Builtins

`Core` 모듈에 정의된 "builtin" 함수는 다음과 같습니다:

```@eval
function lines(words)
    io = IOBuffer()
    n = 0
    for w in words
        if n+length(w) > 80
            print(io, '\n', w)
            n = length(w)
        elseif n == 0
            print(io, w);
            n += length(w)
        else
            print(io, ' ', w);
            n += length(w)+1
        end
    end
    String(take!(io))
end
import Markdown
[string(n) for n in names(Core;all=true)
    if getfield(Core,n) isa Core.Builtin && nameof(getfield(Core,n)) === n] |>
    lines |>
    s ->  "```\n$s\n```" |>
    Markdown.parse
```

이들은 모두 `Builtin`의 하위 유형인 단일 객체로, `Function`의 하위 유형입니다. 이들의 목적은 "jlcall" 호출 규약을 사용하는 런타임의 진입점을 노출하는 것입니다:

```c
jl_value_t *(jl_value_t*, jl_value_t**, uint32_t)
```

내장 함수의 메서드 테이블은 비어 있습니다. 대신, 그들은 올바른 함수에 포인터를 가리키는 단일 캐치올 메서드 캐시 항목(`Tuple{Vararg{Any}}`)을 가지고 있습니다. 이것은 일종의 해킹이지만 꽤 잘 작동합니다.

## Keyword arguments

키워드 인수는 kwcall 함수에 메서드를 추가하여 작동합니다. 이 함수는 일반적으로 "키워드 인수 정렬기" 또는 "키워드 정렬기"이며, 그 후 익명으로 정의된 함수의 내부 본체를 호출합니다. kwsorter 함수의 모든 정의는 일반 메서드 테이블의 일부 정의와 동일한 인수를 가지지만, 앞에 `NamedTuple` 인수가 추가되어 전달된 키워드 인수의 이름과 값을 제공합니다. kwsorter의 작업은 이름에 따라 키워드 인수를 표준 위치로 이동하고, 필요한 기본값 표현식을 평가하고 대체하는 것입니다. 결과는 일반적인 위치 인수 목록이며, 이는 또 다른 컴파일러 생성 함수에 전달됩니다.

키워드 인수 메서드 정의가 어떻게 낮춰지는지를 살펴보는 것이 이 과정을 이해하는 가장 쉬운 방법입니다. 코드는:

```julia
function circle(center, radius; color = black, fill::Bool = true, options...)
    # draw
end
```

실제로 *세 개*의 메서드 정의를 생성합니다. 첫 번째는 모든 인수(키워드 인수를 포함하여)를 위치 인수로 받아들이고, 메서드 본문의 코드를 포함하는 함수입니다. 자동 생성된 이름을 가지고 있습니다:

```julia
function #circle#1(color, fill::Bool, options, circle, center, radius)
    # draw
end
```

두 번째 방법은 키워드 인수가 전달되지 않는 경우를 처리하는 원래 `circle` 함수에 대한 일반적인 정의입니다:

```julia
function circle(center, radius)
    #circle#1(black, true, pairs(NamedTuple()), circle, center, radius)
end
```

이것은 기본값을 전달하면서 첫 번째 메서드로 간단히 디스패치합니다. `pairs`는 나머지 인수의 명명된 튜플에 적용되어 키-값 쌍 반복을 제공합니다. 메서드가 나머지 키워드 인수를 수용하지 않으면 이 인수는 존재하지 않습니다.

마지막으로 kwsorter 정의가 있습니다:

```
function (::Core.kwftype(typeof(circle)))(kws, circle, center, radius)
    if haskey(kws, :color)
        color = kws.color
    else
        color = black
    end
    # etc.

    # put remaining kwargs in `options`
    options = structdiff(kws, NamedTuple{(:color, :fill)})

    # if the method doesn't accept rest keywords, throw an error
    # unless `options` is empty

    #circle#1(color, fill, pairs(options), circle, center, radius)
end
```

함수 `Core.kwftype(t)`는 필드 `t.name.mt.kwsorter`를 생성하고(아직 생성되지 않은 경우), 해당 함수의 유형을 반환합니다.

이 디자인은 키워드 인수를 사용하지 않는 호출 사이트가 특별한 처리가 필요 없다는 특징이 있습니다. 모든 것이 마치 언어의 일부가 아닌 것처럼 작동합니다. 키워드 인수를 사용하는 호출 사이트는 호출된 함수의 kwsorter로 직접 전달됩니다. 예를 들어, 다음과 같은 호출:

```julia
circle((0, 0), 1.0, color = red; other...)
```

낮춰진다:

```julia
kwcall(merge((color = red,), other), circle, (0, 0), 1.0)
```

`kwcall` (또한 `Core`에서도) kwcall 서명 및 디스패치를 나타냅니다. 키워드 스플래팅 작업( `other...`로 작성됨)은 명명된 튜플 `merge` 함수를 호출합니다. 이 함수는 `other`의 각 *요소*를 추가로 언팩하며, 각 요소가 두 개의 값(기호와 값)을 포함할 것으로 예상합니다. 자연스럽게, 모든 스플래팅된 인수가 명명된 튜플인 경우 더 효율적인 구현이 가능합니다. 원래의 `circle` 함수가 클로저를 처리하기 위해 전달된다는 점에 유의하세요.

## [Compiler efficiency issues](@id compiler-efficiency-issues)

모든 함수에 대해 새로운 유형을 생성하는 것은 Julia의 "기본적으로 모든 인수에 대해 특수화" 설계와 결합될 때 컴파일러 자원 사용에 심각한 결과를 초래할 수 있습니다. 실제로 이 설계의 초기 구현은 훨씬 더 긴 빌드 및 테스트 시간, 더 높은 메모리 사용량, 그리고 기준보다 거의 2배 큰 시스템 이미지를 겪었습니다. 단순한 구현에서는 문제가 심각하여 시스템이 거의 사용 불가능해질 정도입니다. 이 설계를 실용적으로 만들기 위해 몇 가지 중요한 최적화가 필요했습니다.

첫 번째 문제는 함수 값 인수의 다양한 값에 대한 기능의 과도한 특수화입니다. 많은 함수는 단순히 인수를 다른 곳, 예를 들어 다른 함수나 저장 위치로 "전달"합니다. 이러한 함수는 전달될 수 있는 모든 클로저에 대해 특수화될 필요가 없습니다. 다행히도 이 경우는 함수가 인수 중 하나를 *호출*하는지 여부를 고려함으로써 쉽게 구별할 수 있습니다(즉, 인수가 어딘가에서 "헤드 위치"에 나타납니다). 성능이 중요한 고차 함수인 `map`은 확실히 인수 함수를 호출하므로 여전히 예상대로 특수화됩니다. 이 최적화는 프론트 엔드에서 `analyze-variables` 패스를 수행하는 동안 호출된 인수를 기록함으로써 구현됩니다. `cache_method`가 `Any` 또는 `Function`으로 선언된 슬롯에 전달된 `Function` 유형 계층의 인수를 발견하면, `@nospecialize` 주석이 적용된 것처럼 동작합니다. 이 휴리스틱은 실제로 매우 효과적인 것으로 보입니다.

다음 문제는 메서드 캐시 해시 테이블의 구조와 관련이 있습니다. 경험적 연구에 따르면 동적으로 디스패치된 호출의 대다수는 하나 또는 두 개의 인수를 포함합니다. 차례로, 이러한 경우의 많은 부분은 첫 번째 인수만 고려함으로써 해결될 수 있습니다. (참고: 단일 디스패치의 지지자들은 이것에 전혀 놀라지 않을 것입니다. 그러나 이 주장은 "다중 디스패치는 실제로 최적화하기 쉽다"는 의미이며, 따라서 우리는 이를 사용해야 하고, *단일 디스패치를 사용해야 한다*는 의미가 아닙니다!) 따라서 메서드 캐시는 첫 번째 인수의 유형을 기본 키로 사용합니다. 그러나 이는 함수 호출의 튜플 유형의 *두 번째* 요소에 해당합니다(첫 번째 요소는 함수 자체의 유형입니다). 일반적으로 헤드 위치에서의 유형 변동은 매우 낮습니다. 실제로 대부분의 함수는 매개변수가 없는 단일 유형에 속합니다. 그러나 생성자의 경우는 다릅니다. 여기서는 단일 메서드 테이블이 모든 유형에 대한 생성자를 보유합니다. 따라서 `Type` 메서드 테이블은 두 번째 대신 *첫 번째* 튜플 유형 요소를 사용하도록 특별히 처리됩니다.

프론트 엔드는 모든 클로저에 대한 타입 선언을 생성합니다. 처음에는 일반 타입 선언을 생성하는 방식으로 구현되었습니다. 그러나 이로 인해 매우 많은 수의 생성자가 생성되었고, 이들 모두는 사소한 것들이었습니다(모든 인수를 [`new`](@ref)에 단순히 전달하는 것). 메서드가 부분적으로 정렬되기 때문에 이러한 모든 메서드를 삽입하는 것은 O(n²)이며, 이들 중 너무 많은 수가 있어 유지하기 어렵습니다. 이는 기본 생성자 생성을 우회하고 `new`를 직접 사용하여 클로저 인스턴스를 생성하는 `struct_type` 표현식을 생성함으로써 최적화되었습니다. 가장 예쁜 방법은 아니지만, 해야 할 일을 하는 것입니다.

다음 문제는 각 테스트 케이스에 대해 0-인자 클로저를 생성하는 `@test` 매크로였습니다. 이는 실제로 필요하지 않으며, 각 테스트 케이스는 단순히 한 번 실행되기 때문입니다. 따라서 `@test`는 테스트 결과(참, 거짓 또는 예외 발생)를 기록하고 이를 테스트 스위트 핸들러에 호출하는 try-catch 블록으로 확장되도록 수정되었습니다.
