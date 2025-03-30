# [Documentation](@id man-documentation)

## Accessing Documentation

문서는 REPL에서 또는 [IJulia](https://github.com/JuliaLang/IJulia.jl)에서 접근할 수 있으며, `?` 다음에 함수나 매크로의 이름을 입력하고 `Enter`를 누르면 됩니다. 예를 들어,

```julia
?cos
?@time
?r""
```

관련 함수, 매크로 또는 문자열 매크로에 대한 문서를 보여줍니다. 대부분의 Julia 환경에서는 문서에 직접 접근할 수 있는 방법을 제공합니다:

  * [VS Code](https://www.julia-vscode.org/)는 함수 이름 위에 마우스를 올리면 문서를 보여줍니다. 또한 사이드바의 Julia 패널을 사용하여 문서를 검색할 수 있습니다.
  * [Pluto](https://github.com/fonsp/Pluto.jl)에서 오른쪽 하단의 "Live Docs" 패널을 엽니다.
  * [Juno](https://junolab.org)에서 `Ctrl-J, Ctrl-D`를 사용하면 커서 아래의 객체에 대한 문서가 표시됩니다.

`Docs.hasdoc(module, name)::Bool`은 이름에 문서 문자열이 있는지 여부를 알려줍니다. `Docs.undocumented_names(module; all)`은 모듈에서 문서화되지 않은 이름을 반환합니다.

## Writing Documentation

줄리아는 패키지 개발자와 사용자가 내장된 문서화 시스템을 통해 함수, 타입 및 기타 객체를 쉽게 문서화할 수 있도록 합니다.

기본 구문은 간단합니다: 객체(함수, 매크로, 타입 또는 인스턴스) 바로 앞에 나타나는 모든 문자열은 그것을 문서화하는 것으로 해석됩니다(이를 *docstrings*라고 합니다). docstring과 문서화된 객체 사이에 빈 줄이나 주석이 들어갈 수 없다는 점에 유의하세요. 다음은 기본 예입니다:

```julia
"Tell whether there are too foo items in the array."
foo(xs::Array) = ...
```

문서는 [Markdown](https://en.wikipedia.org/wiki/Markdown)로 해석되므로, 들여쓰기와 코드 펜스를 사용하여 코드 예제를 텍스트와 구분할 수 있습니다. 기술적으로, 어떤 객체든 메타데이터로 다른 객체와 연결될 수 있습니다; Markdown은 기본값이지만, 다른 문자열 매크로를 구성하고 이를 `@doc` 매크로에 전달할 수도 있습니다.

!!! note
    `Markdown` 표준 라이브러리에 Markdown 지원이 구현되어 있으며, 지원되는 구문 목록은 [documentation](@ref markdown_stdlib)를 참조하십시오.


여기 더 복잡한 예제가 있습니다. 여전히 Markdown을 사용하고 있습니다:

````julia
"""
    bar(x[, y])

Compute the Bar index between `x` and `y`.

If `y` is unspecified, compute the Bar index between all pairs of columns of `x`.

# Examples
```julia-repl
julia> bar([1, 2], [1, 2])
1
```
"""
function bar(x, y) ...
````

위의 예와 같이 문서를 작성할 때 몇 가지 간단한 규칙을 따르는 것을 권장합니다:

1. 항상 문서의 맨 위에 함수의 서명을 표시하고, 네 개의 공백으로 들여쓰기를 하여 Julia 코드로 출력되도록 합니다.

    이것은 Julia 코드에 있는 서명과 동일할 수 있습니다(예: `mean(x::AbstractArray)`), 또는 단순화된 형태일 수 있습니다. 선택적 인자는 가능한 경우 기본값과 함께 표현되어야 합니다(즉, `f(x, y=1)`). 기본값이 없는 선택적 인자는 괄호 안에 넣어야 합니다(즉, `f(x[, y])` 및 `f(x[, y[, z]])`). 대안 솔루션은 여러 줄을 사용하는 것입니다: 하나는 선택적 인자가 없는 것이고, 다른 것들은 선택적 인자가 있는 것입니다. 이 솔루션은 주어진 함수의 여러 관련 메서드를 문서화하는 데에도 사용할 수 있습니다. 함수가 많은 키워드 인자를 허용할 때는 서명에 `<keyword arguments>` 자리 표시자만 포함하고(즉, `f(x; <keyword arguments>)`), `# Arguments` 섹션 아래에 전체 목록을 제공해야 합니다(아래 4번 항목 참조).
2. 기능이 수행하는 작업이나 객체가 나타내는 내용을 설명하는 한 줄의 문장을 간단한 서명 블록 뒤에 포함합니다. 필요하다면, 빈 줄 뒤에 두 번째 단락에서 더 많은 세부 정보를 제공합니다.

    한 줄 문장은 함수 문서화 시 3인칭 대신 명령형("이것을 하세요", "그것을 반환하세요")을 사용해야 합니다. 문장은 마침표로 끝나야 합니다. 함수의 의미를 쉽게 요약할 수 없는 경우, 별도의 조합 가능한 부분으로 나누는 것이 유익할 수 있습니다(하지만 이는 모든 경우에 대한 절대적인 요구 사항으로 간주되어서는 안 됩니다).
3. 자기 반복을 피하세요.

    함수 이름이 시그니처에 의해 제공되므로, 문서를 "함수 `bar`..."로 시작할 필요가 없습니다: 바로 요점으로 들어가십시오. 마찬가지로, 시그니처가 인수의 유형을 지정하는 경우, 설명에서 이를 언급하는 것은 중복됩니다.
4. 필요할 때만 인수 목록을 제공하십시오.

    간단한 함수의 경우, 함수의 목적에 대한 설명에서 인수의 역할을 직접 언급하는 것이 종종 더 명확합니다. 인수 목록은 이미 다른 곳에서 제공된 정보를 반복할 뿐입니다. 그러나 인수가 많은 복잡한 함수(특히 키워드 인수)의 경우 인수 목록을 제공하는 것이 좋은 아이디어일 수 있습니다. 이 경우, 함수에 대한 일반 설명 후에 `# Arguments` 헤더 아래에 삽입하고, 각 인수에 대해 하나의 `-` 글머리를 사용합니다. 목록에는 인수의 유형과 기본값(있는 경우)을 언급해야 합니다:

    ```julia
    """
    ...
    # Arguments
    - `n::Integer`: the number of elements to compute.
    - `dim::Integer=1`: the dimensions along which to perform the computation.
    ...
    """
    ```
5. 관련 함수에 대한 힌트를 제공하십시오.

    때때로 관련 기능의 함수가 있습니다. 발견 가능성을 높이기 위해 `See also` 단락에 이러한 함수의 짧은 목록을 제공해 주십시오.

    ```
    See also [`bar!`](@ref), [`baz`](@ref), [`baaz`](@ref).
    ```
6. Include any code examples in an `# Examples` section.

    Examples should, whenever possible, be written as *doctests*. A *doctest* is a fenced code block (see [Code blocks](@ref)) starting with ````` ```jldoctest````` and contains any number of `julia>` prompts together with inputs and expected outputs that mimic the Julia REPL.

    !!! note
        Doctests는 [`Documenter.jl`](https://github.com/JuliaDocs/Documenter.jl)에 의해 활성화됩니다. 더 자세한 문서는 Documenter's [manual](https://juliadocs.github.io/Documenter.jl/)를 참조하세요.


    예를 들어, 다음 문서 문자열에서 변수 `a`가 정의되고, 이후에 Julia REPL에서 출력된 예상 결과가 나타납니다:

    ````julia
    """
    Some nice documentation here.

    # Examples
    ```jldoctest
    julia> a = [1 2; 3 4]
    2×2 Array{Int64,2}:
     1  2
     3  4
    ```
    """
    ````

    !!! warning
        `rand` 및 기타 RNG 관련 함수를 doctest에서 호출하는 것은 피해야 합니다. 이는 서로 다른 Julia 세션에서 일관된 출력을 생성하지 않기 때문입니다. 무작위 숫자 생성과 관련된 기능을 보여주고 싶다면, 한 가지 옵션은 자신의 RNG 객체를 명시적으로 구성하고 시드(seed)를 설정하는 것입니다(자세한 내용은 [`Random`](@ref Random-Numbers)를 참조하세요) 그리고 이를 doctest 중인 함수에 전달하는 것입니다.

        운영 체제의 단어 크기 ([`Int32`](@ref) 또는 [`Int64`](@ref))와 경로 구분자 차이 (`/` 또는 `\`)는 일부 doctest의 재현성에도 영향을 미칠 것입니다.

        공백이 당신의 doctest에서 중요하다는 점에 유의하세요! 예를 들어 배열의 예쁘게 출력된 결과를 잘못 정렬하면 doctest가 실패합니다.


    그런 다음 `make -C doc doctest=true`를 실행하여 Julia 매뉴얼 및 API 문서의 모든 doctest를 실행할 수 있으며, 이를 통해 예제가 작동하는지 확인할 수 있습니다.

    출력 결과가 잘렸음을 나타내기 위해, 확인을 중지해야 하는 줄에 `[...]`를 작성할 수 있습니다. 이는 doctest가 예외가 발생했음을 보여줄 때, 줄의 줄리아 코드에 대한 비영구적인 참조가 포함된 스택 추적을 숨기는 데 유용합니다. 예를 들어:

    ````julia
    ```jldoctest
    julia> div(1, 0)
    ERROR: DivideError: integer division error
    [...]
    ```
    ````

    예제는 생성된 문서에서 올바르게 강조 표시되도록 ````` ```julia`````로 시작하는 코드 블록 내에 작성해야 합니다.

    !!! tip
        가능한 경우 예제는 **자체 포함**되고 **실행 가능**해야 하므로 독자가 종속성을 포함하지 않고도 시도해 볼 수 있어야 합니다.
7. 코드와 수식을 식별하기 위해 백틱을 사용하세요.

    줄리아 식별자와 코드 발췌는 항상 백틱 ``` ` ``` 사이에 나타나야 하며, 하이라이팅을 가능하게 합니다. LaTeX 구문으로 된 방정식은 이중 백틱 ``` `` ``` 사이에 삽입할 수 있습니다. LaTeX 이스케이프 시퀀스 대신 유니코드 문자를 사용해야 합니다. 즉, ``` ``α = 1`` ``` 대신에 ``` ``\\alpha = 1`` ```을 사용하지 않아야 합니다.
8. Place the starting and ending `"""` characters on lines by themselves.

    그렇다면, 작성하세요:

    ```julia
    """
    ...

    ...
    """
    f(x, y) = ...
    ```

    대신:

    ```julia
    """...

    ..."""
    f(x, y) = ...
    ```

    이것은 docstring이 시작하고 끝나는 위치를 더 명확하게 합니다.
9. 주변 코드에서 사용된 줄 길이 제한을 존중하세요.

    Docstring은 코드와 동일한 도구를 사용하여 편집됩니다. 따라서 동일한 규칙이 적용되어야 합니다. 한 줄의 길이는 최대 92자 이내로 하는 것이 좋습니다.
10. Provide information allowing custom types to implement the function in an `# Implementation` section. These implementation details are intended for developers rather than users, explaining e.g. which functions should be overridden and which functions automatically use appropriate fallbacks. Such details are best kept separate from the main description of the function's behavior.
11. 긴 문서 문자열의 경우, `# Extended help` 헤더로 문서를 나누는 것을 고려하세요. 일반적인 도움말 모드는 헤더 위의 자료만 표시합니다. 표현식의 시작 부분에 '?'를 추가하면 전체 도움말에 접근할 수 있습니다(즉, "?foo" 대신 "??foo"를 사용하세요).

## Functions & Methods

줄리아의 함수는 여러 구현, 즉 메서드를 가질 수 있습니다. 일반적인 함수는 단일 목적을 갖는 것이 좋은 관행이지만, 필요하다면 줄리아는 메서드를 개별적으로 문서화할 수 있도록 허용합니다. 일반적으로 가장 일반적인 메서드만 문서화해야 하며, 심지어 함수 자체(즉, `function bar end`로 생성된 메서드가 없는 객체)도 문서화할 수 있습니다. 특정 메서드는 더 일반적인 메서드와 동작이 다를 경우에만 문서화해야 합니다. 어떤 경우든, 다른 곳에서 제공된 정보를 반복해서는 안 됩니다. 예를 들어:

```julia
"""
    *(x, y, z...)

Multiplication operator. `x * y * z *...` calls this function with multiple
arguments, i.e. `*(x, y, z...)`.
"""
function *(x, y, z...)
    # ... [implementation sold separately] ...
end

"""
    *(x::AbstractString, y::AbstractString, z::AbstractString...)

When applied to strings, concatenates them.
"""
function *(x::AbstractString, y::AbstractString, z::AbstractString...)
    # ... [insert secret sauce here] ...
end

help?> *
search: * .*

  *(x, y, z...)

  Multiplication operator. x * y * z *... calls this function with multiple
  arguments, i.e. *(x,y,z...).

  *(x::AbstractString, y::AbstractString, z::AbstractString...)

  When applied to strings, concatenates them.
```

일반 함수에 대한 문서를 검색할 때, 각 메서드의 메타데이터는 `catdoc` 함수로 연결되며, 이는 물론 사용자 정의 유형에 대해 재정의할 수 있습니다.

## Advanced Usage

`@doc` 매크로는 첫 번째 인수를 두 번째 인수와 연결하여 `META`라는 모듈별 사전에서 사용합니다.

문서 작성을 쉽게 하기 위해, 파서는 매크로 이름 `@doc`를 특별하게 처리합니다: `@doc`에 대한 호출이 하나의 인수를 가지지만, 단일 줄 바꿈 후에 다른 표현식이 나타나면, 그 추가 표현식이 매크로에 대한 인수로 추가됩니다. 따라서 다음 구문은 `@doc`에 대한 2-인수 호출로 파싱됩니다:

```julia
@doc raw"""
...
"""
f(x) = x
```

이것은 `raw""` 문자열 매크로와 같은 일반 문자열 리터럴 이외의 표현식을 문서 문자열로 사용할 수 있게 해줍니다.

문서 검색에 사용될 때, `@doc` 매크로(또는 동일하게 `doc` 함수)는 주어진 객체와 관련된 메타데이터를 찾기 위해 모든 `META` 사전을 검색하고 이를 반환합니다. 반환된 객체(예: 일부 Markdown 콘텐츠)는 기본적으로 지능적으로 자신을 표시합니다. 이 설계는 프로그램 방식으로 문서 시스템을 쉽게 사용할 수 있게 해줍니다. 예를 들어, 함수의 서로 다른 버전 간에 문서를 재사용하는 방법입니다:

```julia
@doc "..." foo!
@doc (@doc foo!) foo
```

또는 줄리아의 메타프로그래밍 기능과 함께 사용하기 위해:

```julia
for (f, op) in ((:add, :+), (:subtract, :-), (:multiply, :*), (:divide, :/))
    @eval begin
        $f(a, b) = $op(a, b)
    end
end
@doc "`add(a, b)` adds `a` and `b` together" add
@doc "`subtract(a, b)` subtracts `b` from `a`" subtract
```

비최상위 블록에서의 문서화, 예를 들어 `begin`, `if`, `for`, `let`, 및 내부 생성자와 같은 경우, `@doc`를 통해 문서 시스템에 추가되어야 합니다. 예를 들어:

```julia
if condition()
    @doc "..."
    f(x) = x
end
```

`f(x)`에 대한 문서는 `condition()`이 `true`일 때 추가됩니다. 블록의 끝에서 `f(x)`가 범위를 벗어나더라도 그 문서는 남아 있음을 유의하세요.

메타프로그래밍을 사용하여 문서 작성에 도움을 줄 수 있습니다. docstring 내에서 문자열 보간을 사용할 때는 `$($name)`과 같이 추가 `$`를 사용해야 합니다:

```julia
for func in (:day, :dayofmonth)
    name = string(func)
    @eval begin
        @doc """
            $($name)(dt::TimeType) -> Int64

        The day of month of a `Date` or `DateTime` as an `Int64`.
        """ $func(dt::Dates.TimeType)
    end
end
```

### Dynamic documentation

때때로 특정 유형의 인스턴스에 대한 적절한 문서는 해당 인스턴스의 필드 값에 따라 달라지며, 단순히 유형 자체에만 의존하지 않습니다. 이러한 경우, 사용자 정의 유형에 대해 `Docs.getdoc`에 메서드를 추가하여 인스턴스별로 문서를 반환할 수 있습니다. 예를 들어,

```julia
struct MyType
    value::Int
end

Docs.getdoc(t::MyType) = "Documentation for MyType with value $(t.value)"

x = MyType(1)
y = MyType(2)
```

`?x`는 "값이 1인 MyType에 대한 문서"를 표시하고 `?y`는 "값이 2인 MyType에 대한 문서"를 표시합니다.

## Syntax Guide

이 가이드는 문서를 제공할 수 있는 모든 Julia 구문 구성 요소에 문서를 첨부하는 방법에 대한 포괄적인 개요를 제공합니다.

다음 예제에서 `"..."`는 임의의 문서 문자열을 설명하는 데 사용됩니다.

### `$` and `\` characters

`$` 및 `\` 문자는 docstring에서도 여전히 문자열 보간 또는 이스케이프 시퀀스의 시작으로 해석됩니다. `raw""` 문자열 매크로와 `@doc` 매크로를 함께 사용하면 이스케이프할 필요가 없습니다. 이는 docstring에 보간이 포함된 LaTeX 또는 Julia 소스 코드 예제가 포함될 때 유용합니다:

````julia
@doc raw"""
```math
\LaTeX
```
"""
function f end
````

### Functions and Methods

```julia
"..."
function f end

"..."
f
```

함수 `f`에 docstring `"..."`을 추가합니다. 첫 번째 버전이 선호되는 구문이지만, 두 가지 모두 동등합니다.

```julia
"..."
f(x) = x

"..."
function f(x)
    return x
end

"..."
f(x)
```

`f(::Any)` 메서드에 docstring `"..."`을 추가합니다.

```julia
"..."
f(x, y = 1) = x + y
```

두 개의 `Method`인 `f(::Any)`와 `f(::Any, ::Any)`에 docstring `"..."`을 추가합니다.

### Macros

```julia
"..."
macro m(x) end
```

`@m(::Any)` 매크로 정의에 docstring `"..."`을 추가합니다.

```julia
"..."
:(@m1)

"..."
macro m2 end
```

`@m1` 및 `@m2`라는 매크로에 docstring `"..."`을 추가합니다.

### Types

```
"..."
abstract type T1 end

"..."
mutable struct T2
    ...
end

"..."
struct T3
    ...
end
```

타입 `T1`, `T2`, 및 `T3`에 문서 문자열 `"..."`을 추가합니다.

```
"..."
T1

"..."
T2

"..."
T3
```

타입 `T1`, `T2`, 및 `T3`에 문서 문자열 `"..."`을 추가합니다. 이전 버전이 선호되는 구문이지만 두 가지 모두 동등합니다.

```julia
"..."
struct T
    "x"
    x
    "y"
    y

    @doc "Inner constructor"
    function T()
        new(...)
    end
end
```

타입 `T`에 문서 문자열 `"..."`을 추가하고, 필드 `T.x`에 `"x"`를, 필드 `T.y`에 `"y"`를, 내부 생성자 `T()`에 `"Inner constructor"`를 추가합니다. `mutable struct` 타입에도 적용 가능합니다.

### Modules

```julia
"..."
module M end

module M

"..."
M

end
```

`Module` `M`에 docstring `"..."`을 추가합니다. `Module` 위에 docstring을 추가하는 것이 선호되는 구문이지만, 두 방법은 동일합니다.

```julia
"..."
baremodule M
# ...
end

baremodule M

import Base: @doc

"..."
f(x) = x

end
```

`baremodule`에 대한 문서를 작성할 때 표현 위에 docstring을 배치하면 `@doc`이 모듈에 자동으로 가져와집니다. 모듈 표현이 문서화되지 않은 경우 이러한 가져오기는 수동으로 수행해야 합니다.

### Global Variables

```julia
"..."
const a = 1

"..."
b = 2

"..."
global c = 3
```

`Binding`의 `a`, `b`, `c`에 docstring `"..."`을 추가합니다.

`Binding`은 참조된 값을 저장하지 않고 `Module` 내에서 특정 `Symbol`에 대한 참조를 저장하는 데 사용됩니다.

!!! note
    `const` 정의가 다른 정의의 별칭을 정의하는 데만 사용되는 경우, 예를 들어 `Base`의 함수 `div`와 그 별칭 `÷`와 같은 경우, 별칭을 문서화하지 말고 실제 함수를 문서화하십시오.

    별칭이 문서화되어 있고 실제 정의가 아닌 경우, 문서 시스템(`?` 모드)은 실제 정의를 검색할 때 별칭에 첨부된 문서 문자열을 반환하지 않습니다.

    예를 들어, 당신은 다음과 같이 작성해야 합니다.

    ```julia
    "..."
    f(x) = x + 1
    const alias = f
    ```

    대신에

    ```julia
    f(x) = x + 1
    "..."
    const alias = f
    ```


```julia
"..."
sym
```

`sym`에 연결된 값에 `"..."`라는 docstring을 추가합니다. 그러나 `sym`은 정의된 곳에서 문서화하는 것이 더 바람직합니다.

### Multiple Objects

```julia
"..."
a, b
```

`a`와 `b` 각각에 문서화 가능한 표현식이어야 하는 docstring `"..."`을 추가합니다. 이 구문은 다음과 동일합니다.

```julia
"..."
a

"..."
b
```

이러한 방식으로 여러 개의 표현식을 함께 문서화할 수 있습니다. 이 구문은 비변경형과 변경형 버전 `f`와 `f!`와 같이 두 함수가 관련될 때 유용할 수 있습니다.

### Macro-generated code

```julia
"..."
@m expression
```

`@m` 표현식을 확장하여 생성된 표현식에 `"..."` 문서 문자열을 추가합니다. 이를 통해 `@inline`, `@noinline`, `@generated` 또는 기타 매크로로 장식된 표현식도 장식되지 않은 표현식과 동일한 방식으로 문서화할 수 있습니다.

매크로 작성자는 단일 표현식을 생성하는 매크로만 자동으로 문서 문자열을 지원한다는 점에 유의해야 합니다. 매크로가 여러 하위 표현식을 포함하는 블록을 반환하는 경우, 문서화해야 하는 하위 표현식은 [`@__doc__`](@ref Core.@__doc__) 매크로를 사용하여 표시해야 합니다.

[`@enum`](@ref) 매크로는 `@__doc__`를 사용하여 [`Enum`](@ref)의 문서를 작성할 수 있도록 합니다. 그 정의를 살펴보는 것은 `@__doc__`를 올바르게 사용하는 방법의 예가 될 것입니다.

```@docs
Core.@__doc__
```
