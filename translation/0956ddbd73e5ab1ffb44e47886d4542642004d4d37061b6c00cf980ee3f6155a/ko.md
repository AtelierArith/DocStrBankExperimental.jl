# Metaprogramming

Lisp의 가장 강력한 유산은 Julia 언어의 메타프로그래밍 지원입니다. Lisp처럼 Julia는 자신의 코드를 언어 자체의 데이터 구조로 표현합니다. 코드가 언어 내에서 생성되고 조작될 수 있는 객체로 표현되기 때문에, 프로그램이 자신의 코드를 변형하고 생성하는 것이 가능합니다. 이는 추가적인 빌드 단계 없이 정교한 코드 생성을 가능하게 하며, [abstract syntax trees](https://en.wikipedia.org/wiki/Abstract_syntax_tree) 수준에서 작동하는 진정한 Lisp 스타일 매크로를 허용합니다. 반면, C와 C++의 전처리기 "매크로" 시스템은 실제 파싱이나 해석이 발생하기 전에 텍스트 조작 및 치환을 수행합니다. Julia의 모든 데이터 유형과 코드는 Julia 데이터 구조로 표현되기 때문에, 프로그램과 그 유형의 내부를 탐색할 수 있는 강력한 [reflection](https://en.wikipedia.org/wiki/Reflection_%28computer_programming%29) 기능이 다른 데이터처럼 제공됩니다.

!!! warning
    메타프로그래밍은 강력한 도구이지만, 코드 이해를 더 어렵게 만들 수 있는 복잡성을 도입합니다. 예를 들어, 범위 규칙을 올바르게 설정하는 것이 놀랍도록 어려울 수 있습니다. 메타프로그래밍은 일반적으로 [higher order functions](@ref man-anonymous-functions) 및 [closures](https://en.wikipedia.org/wiki/Closure_(computer_programming))와 같은 다른 접근 방식이 적용될 수 없을 때만 사용해야 합니다.

    `eval` 및 새로운 매크로 정의는 일반적으로 최후의 수단으로 사용해야 합니다. `Meta.parse`를 사용하거나 임의의 문자열을 Julia 코드로 변환하는 것은 거의 좋은 아이디어가 아닙니다. Julia 코드를 조작할 때는 Julia 구문이 어떻게 파싱되는지의 복잡성을 피하기 위해 `Expr` 데이터 구조를 직접 사용하는 것이 좋습니다.

    메타프로그래밍의 가장 좋은 사용 사례는 종종 런타임 헬퍼 함수에서 대부분의 기능을 구현하며, 생성하는 코드의 양을 최소화하는 것을 목표로 합니다.


## Program representation

모든 줄리아 프로그램은 문자열로 시작합니다:

```jldoctest prog
julia> prog = "1 + 1"
"1 + 1"
```

**다음에는 무엇이 일어날까요?**

다음 단계는 [parse](https://en.wikipedia.org/wiki/Parsing#Computer_languages) 각 문자열을 표현식이라고 하는 객체로 변환하는 것입니다. 이는 줄리아 타입 [`Expr`](@ref)로 표현됩니다:

```jldoctest prog
julia> ex1 = Meta.parse(prog)
:(1 + 1)

julia> typeof(ex1)
Expr
```

`Expr` 객체는 두 부분으로 구성됩니다:

  * a [`Symbol`](@ref) 표현의 종류를 식별합니다. 기호는 [interned string](https://en.wikipedia.org/wiki/String_interning) 식별자입니다 (아래에서 더 논의합니다).

```jldoctest prog
julia> ex1.head
:call
```

  * 표현식 인수는 기호, 다른 표현식 또는 리터럴 값일 수 있습니다:

```jldoctest prog
julia> ex1.args
3-element Vector{Any}:
  :+
 1
 1
```

표현은 [prefix notation](https://en.wikipedia.org/wiki/Polish_notation)에서 직접 구성될 수도 있습니다:

```jldoctest prog
julia> ex2 = Expr(:call, :+, 1, 1)
:(1 + 1)
```

위에서 구성된 두 표현식 - 파싱을 통해서와 직접 구성하여 - 은 동등합니다:

```jldoctest prog
julia> ex1 == ex2
true
```

**여기서 핵심은 Julia 코드가 언어 자체에서 접근할 수 있는 데이터 구조로 내부적으로 표현된다는 것입니다.**

[`dump`](@ref) 함수는 `Expr` 객체의 들여쓰기 및 주석이 달린 표시를 제공합니다:

```jldoctest prog
julia> dump(ex2)
Expr
  head: Symbol call
  args: Array{Any}((3,))
    1: Symbol +
    2: Int64 1
    3: Int64 1
```

`Expr` 객체는 중첩될 수도 있습니다:

```jldoctest ex3
julia> ex3 = Meta.parse("(4 + 4) / 2")
:((4 + 4) / 2)
```

표현식을 보는 또 다른 방법은 `Meta.show_sexpr`를 사용하는 것으로, 이는 주어진 `Expr`의 [S-expression](https://en.wikipedia.org/wiki/S-expression) 형식을 표시합니다. 이는 Lisp 사용자에게 매우 친숙하게 보일 수 있습니다. 다음은 중첩된 `Expr`에서의 표시를 설명하는 예입니다:

```jldoctest ex3
julia> Meta.show_sexpr(ex3)
(:call, :/, (:call, :+, 4, 4), 2)
```

### Symbols

`:` 문자는 Julia에서 두 가지 구문적 용도로 사용됩니다. 첫 번째 형태는 유효한 식별자에서 표현식의 하나의 구성 요소로 사용되는 [`Symbol`](@ref)를 생성합니다. 이는 [interned string](https://en.wikipedia.org/wiki/String_interning)입니다.

```jldoctest
julia> s = :foo
:foo

julia> typeof(s)
Symbol
```

[`Symbol`](@ref) 생성자는 임의의 개수의 인수를 받아들이고, 이들의 문자열 표현을 함께 연결하여 새로운 심볼을 생성합니다:

```jldoctest
julia> :foo === Symbol("foo")
true

julia> Symbol("1foo") # `:1foo` would not work, as `1foo` is not a valid identifier
Symbol("1foo")

julia> Symbol("func",10)
:func10

julia> Symbol(:var,'_',"sym")
:var_sym
```

표현식의 맥락에서 기호는 변수에 대한 접근을 나타내는 데 사용됩니다. 표현식이 평가될 때, 기호는 해당 기호에 바인딩된 값을 적절한 [scope](@ref scope-of-variables)로 대체됩니다.

때때로 `:`에 대한 인수 주위에 추가 괄호가 필요하여 구문 분석의 모호성을 피할 수 있습니다:

```jldoctest
julia> :(:)
:(:)

julia> :(::)
:(::)
```

## Expressions and evaluation

### Quoting

`:` 문자의 두 번째 구문적 목적은 명시적인 [`Expr`](@ref) 생성자를 사용하지 않고 표현식 객체를 만드는 것입니다. 이것은 *인용*이라고 합니다. `:` 문자 다음에 단일 줄의 Julia 코드 주위에 쌍의 괄호가 오면, 포함된 코드를 기반으로 하는 `Expr` 객체가 생성됩니다. 다음은 산술 표현식을 인용하는 데 사용되는 짧은 형식의 예입니다:

```jldoctest
julia> ex = :(a+b*c+1)
:(a + b * c + 1)

julia> typeof(ex)
Expr
```

(이 표현의 구조를 보려면 `ex.head`와 `ex.args`를 시도하거나 위와 같이 [`dump`](@ref) 또는 [`Meta.@dump`](@ref)를 사용하세요)

동일한 표현식은 [`Meta.parse`](@ref) 또는 직접 `Expr` 형식을 사용하여 구성할 수 있습니다:

```jldoctest
julia>      :(a + b*c + 1)       ==
       Meta.parse("a + b*c + 1") ==
       Expr(:call, :+, :a, Expr(:call, :*, :b, :c), 1)
true
```

파서가 제공하는 표현식은 일반적으로 기호, 다른 표현식 및 리터럴 값만을 인수로 가지지만, Julia 코드로 구성된 표현식은 리터럴 형태 없이 임의의 런타임 값을 인수로 가질 수 있습니다. 이 특정 예에서 `+`와 `a`는 기호이고, `*(b,c)`는 하위 표현식이며, `1`은 리터럴 64비트 부호 있는 정수입니다.

여러 표현을 위한 두 번째 구문 형식이 있습니다: `quote ... end`로 둘러싸인 코드 블록입니다.

```jldoctest
julia> ex = quote
           x = 1
           y = 2
           x + y
       end
quote
    #= none:2 =#
    x = 1
    #= none:3 =#
    y = 2
    #= none:4 =#
    x + y
end

julia> typeof(ex)
Expr
```

### [Interpolation](@id man-expression-interpolation)

[`Expr`](@ref) 객체를 값 인수로 직접 생성하는 것은 강력하지만, `Expr` 생성자는 "일반" Julia 구문에 비해 번거로울 수 있습니다. 대안으로, Julia는 리터럴이나 표현식을 인용된 표현식에 *보간*하는 것을 허용합니다. 보간은 접두사 `$`로 표시됩니다.

이 예제에서는 변수 `a`의 값이 보간됩니다:

```jldoctest interp1
julia> a = 1;

julia> ex = :($a + b)
:(1 + b)
```

인용되지 않은 표현식에 대한 보간은 지원되지 않으며 컴파일 시간 오류를 발생시킵니다:

```jldoctest interp1
julia> $a + b
ERROR: syntax: "$" expression outside quote
```

이 예제에서 튜플 `(1,2,3)`은 조건 테스트에 대한 표현식으로 보간됩니다:

```jldoctest interp1
julia> ex = :(a in $:((1,2,3)) )
:(a in (1, 2, 3))
```

`$`를 표현 보간에 사용하는 것은 의도적으로 [string interpolation](@ref string-interpolation) 및 [command interpolation](@ref command-interpolation)을 연상시킵니다. 표현 보간은 복잡한 줄리아 표현을 편리하고 가독성 있게 프로그래밍적으로 구성할 수 있게 해줍니다.

### Splatting interpolation

`$` 보간 구문은 둘러싸는 표현식에 단일 표현식만 삽입할 수 있음을 유의하세요. 때때로, 표현식의 배열이 필요하고 이 모든 표현식이 둘러싸는 표현식의 인수가 되어야 할 때가 있습니다. 이는 `$(xs...)` 구문을 사용하여 수행할 수 있습니다. 예를 들어, 다음 코드는 인수의 수가 프로그래밍적으로 결정되는 함수 호출을 생성합니다:

```jldoctest interp1
julia> args = [:x, :y, :z];

julia> :(f(1, $(args...)))
:(f(1, x, y, z))
```

### Nested quote

자연스럽게도, 인용 표현이 다른 인용 표현을 포함하는 것이 가능합니다. 이러한 경우에 보간이 어떻게 작동하는지 이해하는 것은 다소 까다로울 수 있습니다. 이 예를 고려해 보세요:

```jldoctest interp1
julia> x = :(1 + 2);

julia> e = quote quote $x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :x))
end))
end
```

결과에 `$x`가 포함되어 있다는 것은 `x`가 아직 평가되지 않았음을 의미합니다. 다시 말해, `$` 표현식은 내부 인용 표현식에 "속해" 있으며, 따라서 그 인수는 내부 인용 표현식이:

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    1 + 2
end
```

그러나 외부 `quote` 표현식은 내부 인용에서 `$` 안의 값을 보간할 수 있습니다. 이는 여러 개의 `$`로 수행됩니다:

```jldoctest interp1
julia> e = quote quote $$x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :(1 + 2)))
end))
end
```

`(1 + 2)`가 이제 기호 `x` 대신 결과에 나타나는 것을 주목하세요. 이 표현식을 평가하면 보간된 `3`이 나옵니다:

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    3
end
```

이 행동 뒤에 있는 직관은 `x`가 각 `$`마다 한 번 평가된다는 것입니다: 하나의 `$`는 `eval(:x)`와 유사하게 작동하여 `x`의 값을 제공하고, 두 개의 `$`는 `eval(eval(:x))`와 동등한 작업을 수행합니다.

### [QuoteNode](@id man-quote-node)

AST에서 `quote` 형태의 일반적인 표현은 [`Expr`](@ref)이며, 헤드는 `:quote`입니다:

```jldoctest interp1
julia> dump(Meta.parse(":(1+2)"))
Expr
  head: Symbol quote
  args: Array{Any}((1,))
    1: Expr
      head: Symbol call
      args: Array{Any}((3,))
        1: Symbol +
        2: Int64 1
        3: Int64 2
```

우리가 보았듯이, 이러한 표현식은 `$`를 사용하여 보간을 지원합니다. 그러나 어떤 상황에서는 보간을 수행하지 않고 코드를 *인용*해야 할 필요가 있습니다. 이러한 종류의 인용은 아직 구문이 없지만 내부적으로 `QuoteNode` 유형의 객체로 표현됩니다:

```jldoctest interp1
julia> eval(Meta.quot(Expr(:$, :(1+2))))
3

julia> eval(QuoteNode(Expr(:$, :(1+2))))
:($(Expr(:$, :(1 + 2))))
```

파서는 기호와 같은 간단한 인용 항목에 대해 `QuoteNode`를 생성합니다:

```jldoctest interp1
julia> dump(Meta.parse(":x"))
QuoteNode
  value: Symbol x
```

`QuoteNode`는 특정 고급 메타프로그래밍 작업에도 사용할 수 있습니다.

### Evaluating expressions

주어진 표현식 객체를 사용하여 Julia가 전역 범위에서 이를 평가(실행)하도록 할 수 있습니다: [`eval`](@ref)

```jldoctest interp1
julia> ex1 = :(1 + 2)
:(1 + 2)

julia> eval(ex1)
3

julia> ex = :(a + b)
:(a + b)

julia> eval(ex)
ERROR: UndefVarError: `b` not defined in `Main`
[...]

julia> a = 1; b = 2;

julia> eval(ex)
3
```

모든 [module](@ref modules)는 고유한 [`eval`](@ref) 함수를 가지고 있으며, 이 함수는 전역 범위에서 표현식을 평가합니다. `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566`에 전달된 표현식은 값을 반환하는 것에 국한되지 않으며, 포함된 모듈의 환경 상태를 변경하는 부작용을 가질 수도 있습니다:

```jldoctest
julia> ex = :(x = 1)
:(x = 1)

julia> x
ERROR: UndefVarError: `x` not defined in `Main`

julia> eval(ex)
1

julia> x
1
```

여기서 표현식 객체의 평가로 인해 전역 변수 `x`에 값이 할당됩니다.

표현식은 단순히 `Expr` 객체로, 프로그래밍 방식으로 생성한 후 평가할 수 있으므로, 임의의 코드를 동적으로 생성한 다음 [`eval`](@ref)를 사용하여 실행할 수 있습니다. 다음은 간단한 예입니다:

```julia-repl
julia> a = 1;

julia> ex = Expr(:call, :+, a, :b)
:(1 + b)

julia> a = 0; b = 2;

julia> eval(ex)
3
```

`a`의 값은 `ex` 표현식을 구성하는 데 사용되며, 이는 값 1과 변수 `b`에 `+` 함수를 적용합니다. `a`와 `b`가 사용되는 방식의 중요한 차이를 주목하세요:

  * 식 구성 시 *변수* `a`의 값은 식에서 즉시 값으로 사용됩니다. 따라서 식이 평가될 때 `a`의 값은 더 이상 중요하지 않습니다: 식의 값은 이미 `1`이며, `a`의 값이 무엇이든 상관없습니다.
  * 반면에, *기호* `:b`는 표현식 구성에서 사용되므로, 그 시점에서 변수 `b`의 값은 무관합니다 – `:b`는 단지 기호일 뿐이며 변수 `b`는 정의될 필요조차 없습니다. 그러나 표현식 평가 시점에서는 기호 `:b`의 값이 변수 `b`의 값을 조회하여 해결됩니다.

### Functions on `Expr`essions

As hinted above, one extremely useful feature of Julia is the capability to generate and manipulate Julia code within Julia itself. We have already seen one example of a function returning [`Expr`](@ref) objects: the [`Meta.parse`](@ref) function, which takes a string of Julia code and returns the corresponding `Expr`. A function can also take one or more `Expr` objects as arguments, and return another `Expr`. Here is a simple, motivating example:

```jldoctest
julia> function math_expr(op, op1, op2)
           expr = Expr(:call, op, op1, op2)
           return expr
       end
math_expr (generic function with 1 method)

julia>  ex = math_expr(:+, 1, Expr(:call, :*, 4, 5))
:(1 + 4 * 5)

julia> eval(ex)
21
```

다른 예로, 여기 숫자 인수를 두 배로 만드는 함수가 있지만, 표현식은 그대로 두는 함수가 있습니다:

```jldoctest
julia> function make_expr2(op, opr1, opr2)
           opr1f, opr2f = map(x -> isa(x, Number) ? 2*x : x, (opr1, opr2))
           retexpr = Expr(:call, op, opr1f, opr2f)
           return retexpr
       end
make_expr2 (generic function with 1 method)

julia> make_expr2(:+, 1, 2)
:(2 + 4)

julia> ex = make_expr2(:+, 1, Expr(:call, :*, 5, 8))
:(2 + 5 * 8)

julia> eval(ex)
42
```

## [Macros](@id man-macros)

매크로는 프로그램의 최종 본문에 생성된 코드를 포함하는 메커니즘을 제공합니다. 매크로는 인수의 튜플을 반환된 *표현식*에 매핑하며, 결과 표현식은 런타임 [`eval`](@ref) 호출을 요구하지 않고 직접 컴파일됩니다. 매크로 인수에는 표현식, 리터럴 값 및 기호가 포함될 수 있습니다.

### Basics

여기 매우 간단한 매크로가 있습니다:

```jldoctest sayhello
julia> macro sayhello()
           return :( println("Hello, world!") )
       end
@sayhello (macro with 1 method)
```

매크로는 줄리아의 문법에서 전용 문자를 가지고 있습니다: `@` (앳 기호) 다음에 `macro NAME ... end` 블록에서 선언된 고유한 이름이 옵니다. 이 예제에서 컴파일러는 모든 `@sayhello` 인스턴스를 다음으로 대체할 것입니다:

```julia
:( println("Hello, world!") )
```

`@sayhello`가 REPL에 입력되면, 표현식이 즉시 실행되므로 평가 결과만 볼 수 있습니다:

```jldoctest sayhello
julia> @sayhello()
Hello, world!
```

조금 더 복잡한 매크로를 고려해 보겠습니다:

```jldoctest sayhello2
julia> macro sayhello(name)
           return :( println("Hello, ", $name) )
       end
@sayhello (macro with 1 method)
```

이 매크로는 하나의 인수인 `name`을 받습니다. `@sayhello`가 발견되면, 인용된 표현식이 *확장*되어 인수의 값을 최종 표현식에 삽입합니다:

```jldoctest sayhello2
julia> @sayhello("human")
Hello, human
```

우리는 인용된 반환 표현식을 함수 [`macroexpand`](@ref)를 사용하여 볼 수 있습니다 (**중요 참고:** 이는 매크로 디버깅에 매우 유용한 도구입니다):

```julia-repl sayhello2
julia> ex = macroexpand(Main, :(@sayhello("human")) )
:(Main.println("Hello, ", "human"))

julia> typeof(ex)
Expr
```

우리는 `"human"` 리터럴이 표현식에 삽입된 것을 볼 수 있습니다.

또한 [`@macroexpand`](@ref)라는 매크로가 존재하는데, 이는 `macroexpand` 함수보다 조금 더 편리할 수 있습니다:

```jldoctest sayhello2
julia> @macroexpand @sayhello "human"
:(println("Hello, ", "human"))
```

### Hold up: why macros?

우리는 이전 섹션에서 `f(::Expr...) -> Expr`라는 함수를 이미 보았습니다. 사실, [`macroexpand`](@ref)도 그런 함수입니다. 그렇다면 매크로는 왜 존재할까요?

매크로는 코드가 파싱될 때 실행되기 때문에 필요합니다. 따라서 매크로는 프로그래머가 전체 프로그램이 실행되기 *전에* 맞춤형 코드 조각을 생성하고 포함할 수 있게 해줍니다. 차이를 설명하기 위해 다음 예를 고려해 보십시오:

```julia-repl whymacros
julia> macro twostep(arg)
           println("I execute at parse time. The argument is: ", arg)
           return :(println("I execute at runtime. The argument is: ", $arg))
       end
@twostep (macro with 1 method)

julia> ex = macroexpand(Main, :(@twostep :(1, 2, 3)) );
I execute at parse time. The argument is: :((1, 2, 3))
```

[`println`](@ref)를 호출할 때 [`macroexpand`](@ref)가 호출됩니다. 결과 표현식에는 *오직* 두 번째 `println`만 포함됩니다:

```julia-repl whymacros
julia> typeof(ex)
Expr

julia> ex
:(println("I execute at runtime. The argument is: ", $(Expr(:copyast, :($(QuoteNode(:((1, 2, 3)))))))))

julia> eval(ex)
I execute at runtime. The argument is: (1, 2, 3)
```

### Macro invocation

매크로는 다음과 같은 일반 구문으로 호출됩니다:

```julia
@name expr1 expr2 ...
@name(expr1, expr2, ...)
```

매크로 이름 앞에 있는 구별되는 `@`와 첫 번째 형식에서 인수 표현식 사이의 쉼표가 없는 점, 그리고 두 번째 형식에서 `@name` 뒤에 공백이 없는 점에 유의하세요. 두 스타일은 혼합해서 사용해서는 안 됩니다. 예를 들어, 다음 구문은 위의 예와 다릅니다. 이는 튜플 `(expr1, expr2, ...)`을 매크로에 하나의 인수로 전달합니다:

```julia
@name (expr1, expr2, ...)
```

매크로를 배열 리터럴(또는 이해) 위에서 호출하는 대안적인 방법은 괄호를 사용하지 않고 둘을 나란히 배치하는 것입니다. 이 경우 배열은 매크로에 제공되는 유일한 표현식이 됩니다. 다음 구문은 동등하지만 `@name [a b] * v`와는 다릅니다:

```julia
@name[a b] * v
@name([a b]) * v
```

매크로는 인수를 표현식, 리터럴 또는 기호로 받는다는 점을 강조하는 것이 중요합니다. 매크로 인수를 탐색하는 한 가지 방법은 매크로 본문 내에서 [`show`](@ref) 함수를 호출하는 것입니다:

```jldoctest
julia> macro showarg(x)
           show(x)
           # ... remainder of macro, returning an expression
       end
@showarg (macro with 1 method)

julia> @showarg(a)
:a

julia> @showarg(1+1)
:(1 + 1)

julia> @showarg(println("Yo!"))
:(println("Yo!"))

julia> @showarg(1)        # Numeric literal
1

julia> @showarg("Yo!")    # String literal
"Yo!"

julia> @showarg("Yo! $("hello")")    # String with interpolation is an Expr rather than a String
:("Yo! $("hello")")
```

주어진 인수 목록 외에도, 모든 매크로는 `__source__` 및 `__module__`이라는 추가 인수가 전달됩니다.

인수 `__source__`는 매크로 호출에서 `@` 기호의 파서 위치에 대한 정보를 `LineNumberNode` 객체 형태로 제공합니다. 이를 통해 매크로는 더 나은 오류 진단 정보를 포함할 수 있으며, 일반적으로 로깅, 문자열 파서 매크로 및 문서에서 사용됩니다. 예를 들어, [`@__LINE__`](@ref), [`@__FILE__`](@ref), 및 [`@__DIR__`](@ref) 매크로를 구현하는 데 사용됩니다.

위치 정보는 `__source__.line` 및 `__source__.file`을 참조하여 접근할 수 있습니다:

```jldoctest
julia> macro __LOCATION__(); return QuoteNode(__source__); end
@__LOCATION__ (macro with 1 method)

julia> dump(
            @__LOCATION__(
       ))
LineNumberNode
  line: Int64 2
  file: Symbol none
```

인수 `__module__`는 매크로 호출의 확장 컨텍스트에 대한 정보를 `Module` 객체 형태로 제공합니다. 이를 통해 매크로는 기존 바인딩과 같은 컨텍스트 정보를 조회하거나 현재 모듈에서 자기 반사를 수행하는 런타임 함수 호출에 추가 인수로 값을 삽입할 수 있습니다.

### Building an advanced macro

여기 줄리아의 [`@assert`](@ref) 매크로에 대한 간단한 정의가 있습니다:

```jldoctest building
julia> macro assert(ex)
           return :( $ex ? nothing : throw(AssertionError($(string(ex)))) )
       end
@assert (macro with 1 method)
```

이 매크로는 다음과 같이 사용할 수 있습니다:

```jldoctest building
julia> @assert 1 == 1.0

julia> @assert 1 == 0
ERROR: AssertionError: 1 == 0
```

매크로 호출은 구문 분석 시점에 반환된 결과로 확장됩니다. 이는 다음과 같이 작성하는 것과 같습니다:

```julia
1 == 1.0 ? nothing : throw(AssertionError("1 == 1.0"))
1 == 0 ? nothing : throw(AssertionError("1 == 0"))
```

즉, 첫 번째 호출에서 표현식 `:(1 == 1.0)`이 테스트 조건 슬롯에 삽입되고, `string(:(1 == 1.0))`의 값이 단언 메시지 슬롯에 삽입됩니다. 이렇게 구성된 전체 표현식은 `@assert` 매크로 호출이 발생하는 구문 트리에 배치됩니다. 그런 다음 실행 시간에 테스트 표현식이 true로 평가되면 [`nothing`](@ref)가 반환되고, 테스트가 false인 경우에는 false인 단언 표현식을 나타내는 오류가 발생합니다. 조건의 *값*만 사용 가능하므로 이를 함수로 작성하는 것은 불가능하며, 오류 메시지에서 이를 계산한 표현식을 표시하는 것은 불가능하다는 점에 유의하십시오.

`@assert`의 실제 정의는 Julia Base에서 더 복잡합니다. 사용자가 실패한 표현식을 단순히 출력하는 대신, 선택적으로 자신의 오류 메시지를 지정할 수 있도록 허용합니다. 가변 인수를 가진 함수와 마찬가지로([Varargs Functions](@ref)), 이는 마지막 인수 뒤에 생략 기호(...)를 사용하여 지정됩니다:

```jldoctest assert2
julia> macro assert(ex, msgs...)
           msg_body = isempty(msgs) ? ex : msgs[1]
           msg = string(msg_body)
           return :($ex ? nothing : throw(AssertionError($msg)))
       end
@assert (macro with 1 method)
```

이제 `@assert`는 받는 인수의 수에 따라 두 가지 작동 모드를 가지고 있습니다! 인수가 하나만 있으면 `msgs`에 캡처된 표현식의 튜플은 비어 있으며, 위의 더 간단한 정의와 동일하게 작동합니다. 그러나 이제 사용자가 두 번째 인수를 지정하면, 실패하는 표현식 대신 메시지 본문에 인수가 출력됩니다. 적절하게 명명된 [`@macroexpand`](@ref) 매크로를 사용하여 매크로 확장의 결과를 검사할 수 있습니다:

```julia-repl assert2
julia> @macroexpand @assert a == b
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a == b"))
    end)

julia> @macroexpand @assert a==b "a should equal b!"
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a should equal b!"))
    end)
```

또 다른 경우가 있습니다. 실제 `@assert` 매크로가 처리하는 경우인데, "a는 b와 같아야 한다"는 메시지를 출력하는 것 외에도 그들의 값을 출력하고 싶다면 어떻게 해야 할까요? 누군가는 사용자 정의 메시지에서 문자열 보간을 사용하려고 할 수 있습니다. 예를 들어, `@assert a==b "a ($a) should equal b ($b)!"`와 같이 말이죠. 하지만 위의 매크로와 함께 사용하면 예상대로 작동하지 않을 것입니다. 그 이유를 알 수 있나요? [string interpolation](@ref string-interpolation)에서 보았듯이, 보간된 문자열은 [`string`](@ref)에 대한 호출로 재작성됩니다. 비교해 보세요:

```jldoctest
julia> typeof(:("a should equal b"))
String

julia> typeof(:("a ($a) should equal b ($b)!"))
Expr

julia> dump(:("a ($a) should equal b ($b)!"))
Expr
  head: Symbol string
  args: Array{Any}((5,))
    1: String "a ("
    2: Symbol a
    3: String ") should equal b ("
    4: Symbol b
    5: String ")!"
```

이제 `msg_body`에서 단순 문자열 대신 평가해야 할 전체 표현식을 수신하게 됩니다. 이는 [`string`](@ref) 호출의 인수로 반환된 표현식에 직접 삽입할 수 있습니다. 전체 구현은 [`error.jl`](https://github.com/JuliaLang/julia/blob/master/base/error.jl)를 참조하세요.

`@assert` 매크로는 매크로 본문 내에서 표현식을 조작하는 것을 단순화하기 위해 인용된 표현식에 스플라이싱을 효과적으로 활용합니다.

### Hygiene

더 복잡한 매크로에서 발생하는 문제는 [hygiene](https://en.wikipedia.org/wiki/Hygienic_macro)입니다. 간단히 말해, 매크로는 반환된 표현식에서 도입한 변수가 확장되는 주변 코드의 기존 변수와 우연히 충돌하지 않도록 해야 합니다. 반대로, 매크로에 인수로 전달되는 표현식은 종종 주변 코드의 맥락에서 평가될 것으로 *예상*되며, 기존 변수와 상호작용하고 수정합니다. 또 다른 우려는 매크로가 정의된 모듈과 다른 모듈에서 호출될 수 있다는 사실에서 발생합니다. 이 경우 모든 전역 변수가 올바른 모듈로 해결되도록 해야 합니다. Julia는 반환된 표현식만 고려하면 되기 때문에 텍스트 매크로 확장을 사용하는 언어(C와 같은)에 비해 이미 큰 장점을 가지고 있습니다. 다른 모든 변수(위의 `@assert`에서의 `msg`와 같은)는 [normal scoping block behavior](@ref scope-of-variables)를 따릅니다.

이 문제를 설명하기 위해, 표현식을 인수로 받아 시간을 기록하고, 표현식을 평가하고, 다시 시간을 기록한 후, 이전 시간과 이후 시간의 차이를 출력하며, 마지막으로 표현식의 값을 최종 값으로 갖는 `@time` 매크로를 작성하는 것을 고려해 보겠습니다. 매크로는 다음과 같이 보일 수 있습니다:

```julia
macro time(ex)
    return quote
        local t0 = time_ns()
        local val = $ex
        local t1 = time_ns()
        println("elapsed time: ", (t1-t0)/1e9, " seconds")
        val
    end
end
```

여기서 우리는 `t0`, `t1`, 및 `val`이 개인 임시 변수이기를 원하며, `time_ns`는 사용자가 가질 수 있는 어떤 `time_ns` 변수도 아닌 Julia Base의 [`time_ns`](@ref) 함수에 참조되기를 원합니다. (이것은 `println`에도 동일하게 적용됩니다.) 사용자의 표현식 `ex`에 `t0`라는 변수에 대한 할당이 포함되거나 자체 `time_ns` 변수를 정의하는 경우 발생할 수 있는 문제를 상상해 보십시오. 우리는 오류가 발생하거나 신비롭게도 잘못된 동작을 경험할 수 있습니다.

줄리아의 매크로 확장기는 다음과 같은 방식으로 이러한 문제를 해결합니다. 먼저, 매크로 결과 내의 변수는 로컬 또는 글로벌로 분류됩니다. 변수가 로컬로 간주되려면 할당되었고(글로벌로 선언되지 않았으며), 로컬로 선언되었거나 함수 인수 이름으로 사용되어야 합니다. 그렇지 않으면 글로벌로 간주됩니다. 로컬 변수는 고유하게 이름이 변경되며([`gensym`](@ref) 함수를 사용하여 새로운 기호를 생성함), 글로벌 변수는 매크로 정의 환경 내에서 해결됩니다. 따라서 위의 두 가지 문제 모두 처리됩니다. 매크로의 로컬 변수는 사용자 변수와 충돌하지 않으며, `time_ns`와 `println`은 줄리아 기본 정의를 참조합니다.

하나의 문제는 여전히 남아 있습니다. 다음 매크로의 사용을 고려해 보십시오:

```julia
module MyModule
import Base.@time

time_ns() = ... # compute something

@time time_ns()
end
```

여기 사용자 표현식 `ex`는 `time_ns`에 대한 호출이지만 매크로가 사용하는 동일한 `time_ns` 함수가 아닙니다. 이는 분명히 `MyModule.time_ns`를 참조합니다. 따라서 `ex`의 코드가 매크로 호출 환경에서 해결되도록 해야 합니다. 이는 표현식을 [`esc`](@ref)로 "이스케이프"하여 수행됩니다:

```julia
macro time(ex)
    ...
    local val = $(esc(ex))
    ...
end
```

이러한 방식으로 감싸진 표현식은 매크로 확장기에 의해 변경되지 않고 출력에 그대로 붙여넣어집니다. 따라서 매크로 호출 환경에서 해결됩니다.

이 탈출 메커니즘은 필요할 때 위생을 "위반"하는 데 사용될 수 있으며, 사용자 변수를 도입하거나 조작하는 데 사용됩니다. 예를 들어, 다음 매크로는 호출 환경에서 `x`를 0으로 설정합니다:

```jldoctest
julia> macro zerox()
           return esc(:(x = 0))
       end
@zerox (macro with 1 method)

julia> function foo()
           x = 1
           @zerox
           return x # is zero
       end
foo (generic function with 1 method)

julia> foo()
0
```

이러한 변수 조작은 신중하게 사용해야 하지만, 때때로 매우 유용합니다.

위생 규칙을 올바르게 설정하는 것은 상당한 도전이 될 수 있습니다. 매크로를 사용하기 전에 함수 클로저가 충분할지 고려해 볼 수 있습니다. 또 다른 유용한 전략은 가능한 한 많은 작업을 런타임으로 연기하는 것입니다. 예를 들어, 많은 매크로는 단순히 인수를 `QuoteNode` 또는 다른 유사한 [`Expr`](@ref)로 감쌉니다. 이러한 예로는 단순히 `schedule(Task(() -> $body))`를 반환하는 `@task body`와 단순히 `eval(QuoteNode(expr))`를 반환하는 `@eval expr`이 있습니다.

위의 `@time` 예제를 다음과 같이 다시 작성할 수 있습니다:

```julia
macro time(expr)
    return :(timeit(() -> $(esc(expr))))
end
function timeit(f)
    t0 = time_ns()
    val = f()
    t1 = time_ns()
    println("elapsed time: ", (t1-t0)/1e9, " seconds")
    return val
end
```

그러나 우리는 좋은 이유로 이것을 하지 않습니다: `expr`을 새로운 스코프 블록(익명 함수)으로 감싸는 것은 표현식의 의미(그 안의 변수의 스코프)를 약간 변경하기 때문입니다. 우리는 `@time`이 감싸진 코드에 최소한의 영향을 미치면서 사용 가능하기를 원합니다.

### Macros and dispatch

매크로는 줄리아 함수와 마찬가지로 일반적입니다. 이는 다중 디스패치를 통해 여러 메서드 정의를 가질 수 있음을 의미합니다:

```jldoctest macromethods
julia> macro m end
@m (macro with 0 methods)

julia> macro m(args...)
           println("$(length(args)) arguments")
       end
@m (macro with 1 method)

julia> macro m(x,y)
           println("Two arguments")
       end
@m (macro with 2 methods)

julia> @m "asd"
1 arguments

julia> @m 1 2
Two arguments
```

그러나 매크로 디스패치가 매크로에 전달되는 AST의 유형을 기반으로 한다는 점을 염두에 두어야 하며, AST가 런타임에 평가되는 유형이 아니라는 점을 기억해야 합니다.

```jldoctest macromethods
julia> macro m(::Int)
           println("An Integer")
       end
@m (macro with 3 methods)

julia> @m 2
An Integer

julia> x = 2
2

julia> @m x
1 arguments
```

## Code Generation

중복된 보일러플레이트 코드가 상당량 필요할 때, 중복을 피하기 위해 이를 프로그래밍적으로 생성하는 것이 일반적입니다. 대부분의 언어에서는 이를 위해 추가 빌드 단계와 중복 코드를 생성할 별도의 프로그램이 필요합니다. Julia에서는 표현식 보간과 [`eval`](@ref)를 통해 이러한 코드 생성을 프로그램 실행의 정상적인 과정에서 수행할 수 있습니다. 예를 들어, 다음과 같은 사용자 정의 유형을 고려해 보십시오.

```jldoctest mynumber-codegen
struct MyNumber
    x::Float64
end
# output

```

우리가 여러 가지 메서드를 추가하고자 하는 것입니다. 다음 루프에서 프로그래밍 방식으로 이를 수행할 수 있습니다:

```jldoctest mynumber-codegen
for op = (:sin, :cos, :tan, :log, :exp)
    eval(quote
        Base.$op(a::MyNumber) = MyNumber($op(a.x))
    end)
end
# output

```

이제 우리는 우리의 사용자 정의 타입과 함께 이러한 함수를 사용할 수 있습니다:

```jldoctest mynumber-codegen
julia> x = MyNumber(π)
MyNumber(3.141592653589793)

julia> sin(x)
MyNumber(1.2246467991473532e-16)

julia> cos(x)
MyNumber(-1.0)
```

이러한 방식으로, Julia는 자체적으로 [preprocessor](https://en.wikipedia.org/wiki/Preprocessor) 역할을 하며, 언어 내부에서 코드 생성을 허용합니다. 위 코드는 `:` 접두사 인용 형식을 사용하여 약간 더 간결하게 작성될 수 있습니다:

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    eval(:(Base.$op(a::MyNumber) = MyNumber($op(a.x))))
end
```

이러한 종류의 언어 내 코드 생성은 `eval(quote(...))` 패턴을 사용하여 일반적이어서, Julia는 이 패턴을 간략화하는 매크로를 제공합니다:

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    @eval Base.$op(a::MyNumber) = MyNumber($op(a.x))
end
```

[`@eval`](@ref) 매크로는 이 호출을 위의 더 긴 버전과 정확히 동등하게 재작성합니다. 생성된 코드의 더 긴 블록의 경우, `4d61726b646f776e2e436f64652822222c2022406576616c2229_40726566`에 제공된 표현식 인수는 블록일 수 있습니다:

```julia
@eval begin
    # multiple lines
end
```

## [Non-Standard String Literals](@id meta-non-standard-string-literals)

[Strings](@ref non-standard-string-literals)에서 기억하듯이, 식별자로 접두사가 붙은 문자열 리터럴은 비표준 문자열 리터럴이라고 하며, 접두사가 없는 문자열 리터럴과는 다른 의미를 가질 수 있습니다. 예를 들어:

  * `r"^\s*(?:#|$)"`는 문자열 대신 [regular expression object](@ref man-regex-literals)를 생성합니다.
  * `b"DATA\xff\u2200"`는 `[68,65,84,65,255,226,136,128]`에 대한 [byte array literal](@ref man-byte-array-literals)입니다.

아마 놀랍게도, 이러한 동작은 Julia 파서나 컴파일러에 하드코딩되어 있지 않습니다. 대신, 이는 누구나 사용할 수 있는 일반 메커니즘에 의해 제공되는 사용자 정의 동작입니다: 접두사가 있는 문자열 리터럴은 특별히 이름이 지정된 매크로에 대한 호출로 파싱됩니다. 예를 들어, 정규 표현식 매크로는 다음과 같습니다:

```julia
macro r_str(p)
    Regex(p)
end
```

그게 전부입니다. 이 매크로는 문자열 리터럴 `r"^\s*(?:#|$)"`의 리터럴 내용을 `@r_str` 매크로에 전달해야 하며, 그 확장의 결과가 문자열 리터럴이 발생하는 구문 트리에 배치되어야 한다고 말합니다. 다시 말해, 표현식 `r"^\s*(?:#|$)"`는 다음 객체를 구문 트리에 직접 배치하는 것과 동일합니다:

```julia
Regex("^\\s*(?:#|\$)")
```

문자열 리터럴 형식이 짧고 훨씬 더 편리할 뿐만 아니라, 효율성 면에서도 더 우수합니다. 정규 표현식이 컴파일되고 `Regex` 객체가 실제로 *코드가 컴파일될 때* 생성되기 때문에, 컴파일은 코드가 실행될 때마다가 아니라 한 번만 발생합니다. 정규 표현식이 루프에서 발생하는 경우를 고려해 보십시오:

```julia
for line = lines
    m = match(r"^\s*(?:#|$)", line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

정규 표현식 `r"^\s*(?:#|$)"`가 컴파일되어 구문 트리에 삽입되기 때문에, 이 코드를 파싱할 때 표현식은 루프가 실행될 때마다가 아니라 한 번만 컴파일됩니다. 매크로 없이 이를 달성하기 위해서는 이 루프를 다음과 같이 작성해야 합니다:

```julia
re = Regex("^\\s*(?:#|\$)")
for line = lines
    m = match(re, line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

또한, 컴파일러가 정규 표현식 객체가 모든 루프에서 상수임을 결정할 수 없다면, 특정 최적화가 불가능할 수 있으며, 이로 인해 위의 더 편리한 리터럴 형식보다 여전히 비효율적일 수 있습니다. 물론, 비리터럴 형식이 더 편리한 상황도 여전히 존재합니다. 정규 표현식에 변수를 삽입해야 하는 경우, 더 장황한 접근 방식을 취해야 합니다. 정규 표현식 패턴 자체가 동적이고 각 루프 반복마다 변경될 가능성이 있는 경우, 각 반복마다 새로운 정규 표현식 객체를 생성해야 합니다. 그러나 대다수의 사용 사례에서 정규 표현식은 런타임 데이터에 기반하여 생성되지 않습니다. 이러한 대다수의 경우, 정규 표현식을 컴파일 타임 값으로 작성할 수 있는 능력은 매우 귀중합니다.

사용자 정의 문자열 리터럴의 메커니즘은 깊고 강력합니다. 줄리아의 비표준 리터럴이 이를 사용하여 구현될 뿐만 아니라, 명령 리터럴 구문 (``` `echo "Hello, $person"` ```) 또한 다음과 같은 무해해 보이는 매크로를 사용하여 구현됩니다:

```julia
macro cmd(str)
    :(cmd_gen($(shell_parse(str)[1])))
end
```

물론, 이 매크로 정의에서 사용되는 함수들에는 많은 복잡성이 숨겨져 있지만, 그들은 단순히 함수일 뿐이며, 전적으로 줄리아로 작성되었습니다. 그들의 소스를 읽고 그들이 정확히 무엇을 하는지 확인할 수 있습니다. 그들이 하는 모든 일은 프로그램의 구문 트리에 삽입될 표현식 객체를 구성하는 것입니다.

문자열 리터럴과 마찬가지로, 명령 리터럴은 식별자로 접두사를 붙여 비표준 명령 리터럴이라고 하는 것을 형성할 수 있습니다. 이러한 명령 리터럴은 특별히 이름이 지정된 매크로에 대한 호출로 구문 분석됩니다. 예를 들어, 구문 ```custom`literal` ```은 `@custom_cmd "literal"`로 구문 분석됩니다. Julia 자체에는 비표준 명령 리터럴이 포함되어 있지 않지만, 패키지는 이 구문을 사용할 수 있습니다. 다른 구문과 `_str` 접미사 대신 `_cmd` 접미사를 제외하면, 비표준 명령 리터럴은 비표준 문자열 리터럴과 정확히 동일하게 동작합니다.

두 모듈이 동일한 이름의 비표준 문자열 또는 명령 리터럴을 제공하는 경우, 문자열 또는 명령 리터럴을 모듈 이름으로 한정할 수 있습니다. 예를 들어, `Foo`와 `Bar`가 비표준 문자열 리터럴 `@x_str`을 제공하는 경우, `Foo.x"literal"` 또는 `Bar.x"literal"`과 같이 작성하여 두 가지를 구분할 수 있습니다.

매크로를 정의하는 또 다른 방법은 다음과 같습니다:

```julia
macro foo_str(str, flag)
    # do stuff
end
```

이 매크로는 다음 구문으로 호출할 수 있습니다:

```julia
foo"str"flag
```

위에서 언급한 구문에서 플래그의 유형은 문자열 리터럴 뒤에 오는 내용을 포함하는 `String`입니다.

## Generated functions

매우 특별한 매크로는 [`@generated`](@ref)로, 이 매크로를 사용하면 이른바 *생성된 함수*를 정의할 수 있습니다. 이러한 함수는 인수의 유형에 따라 전문화된 코드를 생성할 수 있는 능력을 가지고 있으며, 다중 분배로 달성할 수 있는 것보다 더 유연하게 또는 더 적은 코드로 이를 수행할 수 있습니다. 매크로는 구문 분석 시점에서 표현식과 함께 작동하며 입력의 유형에 접근할 수 없지만, 생성된 함수는 인수의 유형이 알려진 시점에 확장되지만 함수는 아직 컴파일되지 않은 상태입니다.

대신 계산이나 작업을 수행하는 대신, 생성된 함수 선언은 인용된 표현식을 반환하며, 이는 인수의 유형에 해당하는 메서드의 본체를 형성합니다. 생성된 함수가 호출되면, 반환된 표현식이 컴파일되고 실행됩니다. 이를 효율적으로 만들기 위해 결과는 일반적으로 캐시됩니다. 또한 이를 추론 가능하게 만들기 위해 언어의 제한된 하위 집합만 사용할 수 있습니다. 따라서 생성된 함수는 허용되는 구성 요소에 대한 더 큰 제약을 감수하면서 작업을 실행 시간에서 컴파일 시간으로 이동하는 유연한 방법을 제공합니다.

생성 함수 정의 시, 일반 함수와의 주요 차이점은 다섯 가지가 있습니다:

1. 함수 선언에 `@generated` 매크로를 주석으로 추가합니다. 이렇게 하면 AST에 일부 정보가 추가되어 컴파일러가 이것이 생성된 함수임을 알 수 있습니다.
2. 생성된 함수의 본문에서는 인수의 *타입*만 접근할 수 있으며, 값에는 접근할 수 없습니다.
3. 대신 어떤 것을 계산하거나 행동을 수행하는 대신, 당신이 원하는 것을 수행하는 *인용된 표현*을 반환합니다.
4. 생성된 함수는 생성된 함수의 정의 *이전*에 정의된 함수만 호출할 수 있습니다. (이를 따르지 않으면 미래 세계 연대의 함수에 대한 `MethodErrors`가 발생할 수 있습니다.)
5. 생성된 함수는 비상수 전역 상태(예: IO, 잠금, 비지역 사전 또는 [`hasmethod`](@ref) 사용)를 *변경*하거나 *관찰*해서는 안 됩니다. 이는 전역 상수만 읽을 수 있으며, 부작용이 없어야 함을 의미합니다. 다시 말해, 함수는 완전히 순수해야 합니다. 구현 제한으로 인해 현재 클로저나 생성기를 정의할 수 없습니다.

가장 쉽게 예를 들어 설명할 수 있습니다. 생성된 함수 `foo`를 다음과 같이 선언할 수 있습니다.

```jldoctest generated
julia> @generated function foo(x)
           Core.println(x)
           return :(x * x)
       end
foo (generic function with 1 method)
```

본문은 `x * x`의 값이 아니라 인용된 표현인 `:(x * x)`를 반환한다는 점에 유의하십시오.

호출자의 관점에서 볼 때, 이것은 일반 함수와 동일합니다. 사실, 일반 함수인지 생성된 함수인지 알 필요가 없습니다. `foo`가 어떻게 동작하는지 살펴보겠습니다:

```jldoctest generated
julia> x = foo(2); # note: output is from println() statement in the body
Int64

julia> x           # now we print x
4

julia> y = foo("bar");
String

julia> y
"barbar"
```

그래서 생성된 함수의 본문에서 `x`는 전달된 인수의 *유형*이며, 생성된 함수가 반환하는 값은 정의에서 반환한 인용된 표현식을 평가한 결과로, 이제는 `x`의 *값*을 사용합니다.

`foo`를 이미 사용한 타입으로 다시 평가하면 어떻게 될까요?

```jldoctest generated
julia> foo(4)
16
```

[`Int64`](@ref)의 출력이 없음을 주의하세요. 생성된 함수의 본문이 특정 인수 유형 집합에 대해 여기서 단 한 번만 실행되었고, 결과가 캐시되었음을 알 수 있습니다. 그 후, 이 예제에서는 첫 번째 호출에서 생성된 함수가 반환한 표현식이 메서드 본문으로 재사용되었습니다. 그러나 실제 캐싱 동작은 구현 정의 성능 최적화이므로 이 동작에 너무 의존하는 것은 무효입니다.

생성된 함수가 생성되는 횟수는 *한 번만* 발생할 수도 있지만, *더 자주* 발생할 수도 있고, 전혀 발생하지 않는 것처럼 보일 수도 있습니다. 결과적으로, 부작용이 있는 생성된 함수를 *절대* 작성해서는 안 됩니다 - 부작용이 언제, 얼마나 자주 발생하는지는 정의되지 않았습니다. (이것은 매크로에도 해당됩니다 - 매크로와 마찬가지로, 생성된 함수에서 [`eval`](@ref)를 사용하는 것은 잘못된 방식으로 작업하고 있다는 신호입니다.) 그러나 매크로와 달리, 런타임 시스템은 `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566`에 대한 호출을 올바르게 처리할 수 없으므로, 이는 금지됩니다.

`@generated` 함수가 메서드 재정의와 어떻게 상호작용하는지를 보는 것도 중요합니다. 올바른 `@generated` 함수는 어떤 가변 상태도 관찰하지 않거나 전역 상태의 변화를 일으키지 않아야 한다는 원칙에 따라, 다음과 같은 동작을 확인할 수 있습니다. 생성된 함수는 생성된 함수 자체의 *정의* 이전에 정의되지 않은 어떤 메서드도 호출할 수 *없습니다*.

처음에 `f(x)`는 하나의 정의를 가지고 있습니다.

```jldoctest redefinition
julia> f(x) = "original definition";
```

`f(x)`를 사용하는 다른 연산을 정의하세요:

```jldoctest redefinition
julia> g(x) = f(x);

julia> @generated gen1(x) = f(x);

julia> @generated gen2(x) = :(f(x));
```

이제 `f(x)`에 대한 새로운 정의를 추가합니다:

```jldoctest redefinition
julia> f(x::Int) = "definition for Int";

julia> f(x::Type{Int}) = "definition for Type{Int}";
```

그리고 이러한 결과들이 어떻게 다른지 비교하십시오:

```jldoctest redefinition
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> gen1(1)
"original definition"

julia> gen2(1)
"definition for Int"
```

생성된 함수의 각 메서드는 정의된 함수에 대한 고유한 관점을 가지고 있습니다:

```jldoctest redefinition
julia> @generated gen1(x::Real) = f(x);

julia> gen1(1)
"definition for Type{Int}"
```

위에서 생성된 함수 `foo`는 일반 함수 `foo(x) = x * x`가 할 수 없는 일을 하지 않았습니다(첫 번째 호출 시 타입을 출력하고 더 높은 오버헤드를 발생시키는 것을 제외하고). 그러나 생성된 함수의 강점은 전달된 타입에 따라 서로 다른 인용된 표현식을 계산할 수 있는 능력에 있습니다:

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generic function with 1 method)

julia> bar(4)
16

julia> bar("baz")
"baz"
```

(물론 이 인위적인 예제는 다중 디스패치를 사용하여 더 쉽게 구현될 수 있습니다...)

이것을 남용하면 런타임 시스템이 손상되고 정의되지 않은 동작을 초래할 수 있습니다:

```jldoctest
julia> @generated function baz(x)
           if rand() < .9
               return :(x^2)
           else
               return :("boo!")
           end
       end
baz (generic function with 1 method)
```

생성된 함수의 본체가 비결정적이기 때문에, 그 동작과 *모든 후속 코드의 동작*은 정의되지 않습니다.

*이 예제를 복사하지 마세요!*

이 예제들이 생성된 함수가 어떻게 작동하는지를 정의 측면과 호출 측면에서 설명하는 데 도움이 되기를 바랍니다. 그러나 *이들을 복사하지 마세요*, 그 이유는 다음과 같습니다:

  * `foo` 함수는 부작용이 있으며( `Core.println` 호출), 이러한 부작용이 발생하는 정확한 시점, 빈도 또는 횟수는 정의되지 않습니다.
  * `bar` 함수는 다중 분배로 더 잘 해결되는 문제를 해결합니다. `bar(x) = x`와 `bar(x::Integer) = x ^ 2`를 정의하면 같은 작업을 수행하지만, 더 간단하고 빠릅니다.
  * `baz` 함수는 병리적입니다.

생성된 함수에서 시도해서는 안 되는 작업의 집합은 무한하며, 현재 런타임 시스템은 유효하지 않은 작업의 하위 집합만 감지할 수 있습니다. 알림 없이 런타임 시스템을 단순히 손상시키는 다른 많은 작업이 있으며, 일반적으로 나쁜 정의와 명백하게 연결되지 않은 미묘한 방식으로 발생합니다. 함수 생성기는 추론 중에 실행되므로 해당 코드의 모든 제한 사항을 준수해야 합니다.

시도해서는 안 되는 몇 가지 작업은 다음과 같습니다:

1. 네이티브 포인터의 캐싱.
2. `Core.Compiler`의 내용이나 메서드와 상호작용하는 방법.
3. 변경 가능한 상태 관찰하기.

      * 생성된 함수에 대한 추론은 *언제든지* 실행될 수 있으며, 이는 코드가 이 상태를 관찰하거나 변경하려고 시도하는 동안에도 가능합니다.
4. 잠금을 사용하는 것: 호출하는 C 코드가 내부적으로 잠금을 사용할 수 있습니다(예: 대부분의 구현이 내부적으로 잠금을 요구하더라도 `malloc`을 호출하는 것은 문제가 되지 않습니다). 그러나 Julia 코드를 실행하는 동안 잠금을 보유하거나 획득하려고 하지 마십시오.
5. 생성된 함수의 본문 이후에 정의된 모든 함수를 호출합니다. 이 조건은 점진적으로 로드된 미리 컴파일된 모듈에 대해 완화되어 모듈 내의 모든 함수를 호출할 수 있도록 허용됩니다.

좋습니다. 이제 생성된 함수가 어떻게 작동하는지 더 잘 이해했으니, 이를 사용하여 좀 더 고급(및 유효한) 기능을 구축해 봅시다...

### An advanced example

줄리아의 기본 라이브러리에는 n차원 배열에 대한 선형 인덱스를 계산하기 위한 내부 `sub2ind` 함수가 있습니다. 이는 n개의 다중 선형 인덱스 집합을 기반으로 하며, 즉 `A[x,y,z,...]` 대신 `A[i]`를 사용하여 배열 `A`에 인덱싱할 수 있는 인덱스 `i`를 계산하는 것입니다. 가능한 구현 중 하나는 다음과 같습니다:

```jldoctest sub2ind
julia> function sub2ind_loop(dims::NTuple{N}, I::Integer...) where N
           ind = I[N] - 1
           for i = N-1:-1:1
               ind = I[i]-1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> sub2ind_loop((3, 5), 1, 2)
4
```

재귀를 사용하여 같은 작업을 수행할 수 있습니다:

```jldoctest
julia> sub2ind_rec(dims::Tuple{}) = 1;

julia> sub2ind_rec(dims::Tuple{}, i1::Integer, I::Integer...) =
           i1 == 1 ? sub2ind_rec(dims, I...) : throw(BoundsError());

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer) = i1;

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer, I::Integer...) =
           i1 + dims[1] * (sub2ind_rec(Base.tail(dims), I...) - 1);

julia> sub2ind_rec((3, 5), 1, 2)
4
```

이 두 구현은 서로 다르지만 본질적으로 동일한 작업을 수행합니다: 배열의 차원에 대한 런타임 루프를 통해 각 차원에서 오프셋을 수집하여 최종 인덱스를 생성합니다.

그러나 루프에 필요한 모든 정보는 인수의 타입 정보에 내장되어 있습니다. 이는 컴파일러가 반복을 컴파일 시간으로 이동하고 런타임 루프를 완전히 제거할 수 있게 해줍니다. 우리는 생성된 함수를 활용하여 유사한 효과를 얻을 수 있습니다. 컴파일러 용어로, 우리는 생성된 함수를 사용하여 루프를 수동으로 펼칩니다. 본문은 거의 동일해지지만, 선형 인덱스를 계산하는 대신 인덱스를 계산하는 *식*을 구성합니다:

```jldoctest sub2ind_gen
julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

**이 코드는 무엇을 생성할까요?**

몸체를 다른 (일반) 함수로 추출하는 것이 쉬운 방법입니다:

```jldoctest sub2ind_gen2
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           length(I) == N || return :(error("partial indexing is unsupported"))
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           return sub2ind_gen_impl(dims, I...)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

이제 `sub2ind_gen_impl`을 실행하고 그것이 반환하는 표현식을 살펴볼 수 있습니다:

```jldoctest sub2ind_gen2
julia> sub2ind_gen_impl(Tuple{Int,Int}, Int, Int)
:(((I[1] - 1) + dims[1] * (I[2] - 1)) + 1)
```

그래서 여기서 사용될 메서드 본체는 전혀 루프를 포함하지 않습니다 - 단지 두 튜플에 인덱싱하고, 곱셈과 덧셈/뺄셈을 수행합니다. 모든 루핑은 컴파일 시간에 수행되며, 실행 중에는 루핑을 완전히 피합니다. 따라서 우리는 *타입당 한 번*만 루프를 수행하며, 이 경우 `N`당 한 번 수행합니다 (함수가 한 번 이상 생성되는 엣지 케이스를 제외하고 - 위의 면책 조항을 참조하세요).

### Optionally-generated functions

생성된 함수는 실행 시간에 높은 효율성을 달성할 수 있지만, 컴파일 시간 비용이 발생합니다: 구체적인 인수 유형의 모든 조합에 대해 새로운 함수 본체가 생성되어야 합니다. 일반적으로 Julia는 모든 인수에 대해 작동하는 "일반" 버전의 함수를 컴파일할 수 있지만, 생성된 함수의 경우 이는 불가능합니다. 이는 생성된 함수를 많이 사용하는 프로그램이 정적으로 컴파일되는 것이 불가능할 수 있음을 의미합니다.

이 문제를 해결하기 위해, 언어는 생성된 함수의 일반적인 비생성 대체 구현을 작성하는 구문을 제공합니다. 위의 `sub2ind` 예제에 적용하면 다음과 같이 보일 것입니다:

```jldoctest sub2ind_gen_opt
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> function sub2ind_gen_fallback(dims::NTuple{N}, I) where N
           ind = I[N] - 1
           for i = (N - 1):-1:1
               ind = I[i] - 1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           length(I) == N || error("partial indexing is unsupported")
           if @generated
               return sub2ind_gen_impl(dims, I...)
           else
               return sub2ind_gen_fallback(dims, I)
           end
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

내부적으로 이 코드는 함수의 두 가지 구현을 생성합니다: `if @generated`의 첫 번째 블록이 사용되는 생성된 구현과 `else` 블록이 사용되는 일반 구현입니다. `if @generated` 블록의 `then` 부분 안에서는 코드가 다른 생성된 함수와 동일한 의미를 가집니다: 인수 이름은 타입을 참조하고, 코드는 표현식을 반환해야 합니다. 여러 개의 `if @generated` 블록이 발생할 수 있으며, 이 경우 생성된 구현은 모든 `then` 블록을 사용하고 대체 구현은 모든 `else` 블록을 사용합니다.

함수의 맨 위에 오류 검사를 추가했음을 주목하세요. 이 코드는 두 버전 모두에 공통적이며, 두 버전 모두에서 런타임 코드입니다(생성된 버전에서 표현식으로 인용되고 반환됩니다). 이는 로컬 변수의 값과 타입이 코드 생성 시점에 사용 가능하지 않음을 의미합니다 – 코드 생성 코드는 인수의 타입만 볼 수 있습니다.

이 정의 스타일에서 코드 생성 기능은 본질적으로 선택적 최적화입니다. 컴파일러는 편리할 경우 이를 사용하지만, 그렇지 않으면 일반 구현을 선택할 수 있습니다. 이 스타일은 컴파일러가 더 많은 결정을 내리고 프로그램을 더 다양한 방식으로 컴파일할 수 있게 해주기 때문에 선호됩니다. 또한 일반 코드는 코드 생성 코드보다 더 읽기 쉽습니다. 그러나 어떤 구현이 사용되는지는 컴파일러 구현 세부 사항에 따라 다르므로 두 구현이 동일하게 동작하는 것이 필수적입니다.
