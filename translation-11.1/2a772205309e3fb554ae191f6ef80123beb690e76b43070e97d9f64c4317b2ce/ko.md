```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Markdown/docs/src/index.md"
```

# [Markdown](@id markdown_stdlib)

이 섹션에서는 Markdown 표준 라이브러리에 의해 활성화된 Julia의 Markdown 구문을 설명합니다. 다음 Markdown 요소가 지원됩니다:

## Inline elements

여기서 "인라인"은 텍스트 블록, 즉 단락 내에서 발견될 수 있는 요소를 의미합니다. 여기에는 다음 요소가 포함됩니다.

### Bold

단어를 두 개의 별표 `**`로 감싸면, 포함된 텍스트가 굵게 표시됩니다.

```
A paragraph containing a **bold** word.
```

### Italics

단어를 하나의 별표 `*`로 감싸면, 감싸진 텍스트가 이탤릭체로 표시됩니다.

```
A paragraph containing an *italicized* word.
```

### Literals

텍스트를 정확히 작성된 대로 표시해야 하는 경우에는 단일 백틱으로 감싸십시오, ``` ` ``` .

```
A paragraph containing a `literal` word.
```

리터럴은 변수, 함수 또는 다른 Julia 프로그램의 부분을 참조하는 텍스트를 작성할 때 사용해야 합니다.

!!! tip
    리터럴 텍스트 내에 백틱 문자를 포함하려면 텍스트를 감싸기 위해 하나가 아닌 세 개의 백틱을 사용하세요.

    ```
    A paragraph containing ``` `backtick` characters ```.
    ```

    확장에 의해 홀수 개의 백틱을 사용하여 더 적은 수의 백틱을 둘러쌀 수 있습니다.


### $\LaTeX$

수학으로 표시해야 하는 텍스트는 $\LaTeX$ 구문을 사용하여 이중 백틱으로 감싸야 합니다: ``` `` ``` .

```
A paragraph containing some ``\LaTeX`` markup.
```

!!! tip
    이전 섹션의 리터럴과 마찬가지로, 이중 백틱 내에 리터럴 백틱을 작성해야 하는 경우 두 개보다 큰 짝수 개수를 사용해야 합니다. 단일 리터럴 백틱이 $\LaTeX$ 마크업 내에 포함되어야 하는 경우 두 개의 감싸는 백틱이면 충분합니다.


!!! note
    `\` 문자는 Julia 소스 코드에 텍스트가 포함될 경우 적절하게 이스케이프되어야 합니다. 예를 들어, ```"``\\LaTeX`` 문법이 문서 문자열에 있습니다."```와 같이 문자열 리터럴로 해석되기 때문입니다. 또는 이스케이프를 피하기 위해 `@doc` 매크로와 함께 `raw` 문자열 매크로를 사용할 수 있습니다:

    ```
    @doc raw"``\LaTeX`` syntax in a docstring." functionname
    ```


### Links

링크는 다음 구문을 사용하여 외부 또는 내부 대상을 작성할 수 있습니다. 대괄호 `[ ]`로 묶인 텍스트는 링크의 이름이고, 괄호 `( )`로 묶인 텍스트는 URL입니다.

```
A paragraph containing a link to [Julia](https://www.julialang.org).
```

Julia 문서 내에서 다른 문서화된 함수/메서드/변수에 대한 교차 참조를 추가하는 것도 가능합니다. 예를 들어:

```julia
"""
    tryparse(type, str; base)

Like [`parse`](@ref), but returns either a value of the requested type,
or [`nothing`](@ref) if the string does not contain a valid number.
"""
```

이것은 생성된 문서에 [`parse`](@ref) 문서에 대한 링크를 생성합니다(이 함수가 실제로 수행하는 작업에 대한 더 많은 정보가 포함되어 있습니다) 및 [`nothing`](@ref) 문서에 대한 링크를 생성합니다. 함수의 변형/비변형 버전에 대한 교차 참조를 포함하거나 두 개의 유사한 함수 간의 차이를 강조하는 것이 좋습니다.

!!! note
    위의 교차 참조는 *마크다운* 기능이 아니며, 기본 줄리아 문서를 작성하는 데 사용되는 [Documenter.jl](https://github.com/JuliaDocs/Documenter.jl)에 의존합니다.


### Footnote references

명명되고 번호가 매겨진 각주 참조는 다음 구문을 사용하여 작성할 수 있습니다. 각주 이름은 구두점이 없는 단일 영숫자 단어여야 합니다.

```
A paragraph containing a numbered footnote [^1] and a named one [^named].
```

!!! note
    각주와 관련된 텍스트는 각주 참조와 동일한 페이지 내의 아무 곳에나 작성할 수 있습니다. 각주 텍스트를 정의하는 데 사용되는 구문은 아래의 [Footnotes](@ref) 섹션에서 논의됩니다.


## Toplevel elements

다음 요소는 문서의 "최상위"에 작성하거나 다른 "최상위" 요소 내에 작성할 수 있습니다.

### Paragraphs

단락은 위의 [Inline elements](@ref) 섹션에서 정의된 인라인 요소를 포함할 수 있는 일반 텍스트 블록으로, 그 위와 아래에 하나 이상의 빈 줄이 있습니다.

```
This is a paragraph.

And this is *another* paragraph containing some emphasized text.
A new line, but still part of the same paragraph.
```

### Headers

문서는 헤더를 사용하여 다양한 섹션으로 나눌 수 있습니다. 헤더는 다음 구문을 사용합니다:

```julia
# Level One
## Level Two
### Level Three
#### Level Four
##### Level Five
###### Level Six
```

헤더 줄은 문단과 마찬가지로 모든 인라인 구문을 포함할 수 있습니다.

!!! tip
    문서 내에서 너무 많은 수준의 헤더를 사용하는 것을 피하십시오. 지나치게 중첩된 문서는 구조를 재조정하거나 별도의 주제를 다루는 여러 페이지로 나누어야 할 필요성을 나타낼 수 있습니다.


### Code blocks

소스 코드는 다음 예제와 같이 네 개의 공백 또는 하나의 탭으로 들여쓰기를 사용하여 리터럴 블록으로 표시할 수 있습니다.

```
This is a paragraph.

    function func(x)
        # ...
    end

Another paragraph.
```

또한, 코드 블록은 선택적으로 "언어"를 사용하여 코드 블록이 어떻게 강조되어야 하는지를 지정하는 세 개의 백틱으로 둘러쌀 수 있습니다.

````
A code block without a "language":

```
function func(x)
    # ...
end
```

and another one with the "language" specified as `julia`:

```julia
function func(x)
    # ...
end
```
````

!!! note
    "펜스" 코드 블록은 마지막 예제에서 보여준 것처럼 들여쓰기된 코드 블록보다 선호되어야 합니다. 왜냐하면 들여쓰기된 코드 블록이 어떤 언어로 작성되었는지 지정할 방법이 없기 때문입니다.


### Block quotes

텍스트는 외부 출처에서 인용할 수 있으며, 인용문 각 줄 앞에 `>` 문자를 추가하여 다음과 같이 표시할 수 있습니다.

```
Here's a quote:

> Julia is a high-level, high-performance dynamic programming language for
> technical computing, with syntax that is familiar to users of other
> technical computing environments.
```

Markdown.Paragraph(Any["한 줄의 각 줄에서 ", Markdown.Code("", ">"), " 문자 뒤에 단일 공백이 있어야 합니다. 인용 블록은 다른 최상위 또는 인라인 요소를 포함할 수 있습니다."])

### Images

이미지의 구문은 위에서 언급한 링크 구문과 유사합니다. 링크 앞에 `!` 문자를 추가하면 지정된 URL에서 이미지를 표시하고 링크 대신 이미지를 표시합니다.

```julia
![alternative text](link/to/image.png)
```

### Lists

순서가 없는 목록은 목록의 각 항목 앞에 `*`, `+` 또는 `-`를 추가하여 작성할 수 있습니다.

```
A list of items:

  * item one
  * item two
  * item three
```

각 `*` 앞에 두 개의 공백과 각 `*` 뒤에 하나의 공백이 있음을 주의하세요.

목록은 목록, 코드 블록 또는 인용 블록과 같은 다른 중첩된 최상위 요소를 포함할 수 있습니다. 목록 내에 최상위 요소를 포함할 때는 각 목록 항목 사이에 빈 줄을 남겨야 합니다.

```
Another list:

  * item one

  * item two

    ```
    f(x) = x
    ```

  * And a sublist:

      + sub-item one
      + sub-item two
```

!!! note
    각 항목의 내용은 항목의 첫 번째 줄과 정렬되어야 합니다. 위의 예에서 차단된 코드 블록은 `item two`의 `i`와 정렬되도록 네 칸 들여쓰기를 해야 합니다.


순서가 있는 목록은 "글머리 기호" 문자, 즉 `*`, `+` 또는 `-`를 양의 정수와 `.` 또는 `)`로 대체하여 작성됩니다.

```
Two ordered lists:

 1. item one
 2. item two
 3. item three

 5) item five
 6) item six
 7) item seven
```

순서가 있는 목록은 위의 예에서 두 번째 목록처럼 1이 아닌 다른 숫자에서 시작할 수 있습니다. 순서가 없는 목록과 마찬가지로, 순서가 있는 목록은 중첩된 최상위 요소를 포함할 수 있습니다.

### Display equations

큰 $\LaTeX$ 방정식은 문단 내에 인라인으로 맞지 않을 경우, 아래 예와 같이 "language" `math`가 있는 괄호 코드 블록을 사용하여 표시 방정식으로 작성할 수 있습니다.

````julia
```math
f(a) = \frac{1}{2\pi}\int_{0}^{2\pi} (\alpha+R\cos(\theta))d\theta
```
````

### Footnotes

이 구문은 [Footnote references](@ref)에 대한 인라인 구문과 쌍을 이룹니다. 해당 섹션도 반드시 읽어보세요.

각주 텍스트는 다음 구문을 사용하여 정의되며, 이는 각주 참조 구문과 유사하지만 각주 레이블 뒤에 `:` 문자가 추가됩니다.

```
[^1]: Numbered footnote text.

[^note]:

    Named footnote text containing several toplevel elements
    indented by 4 spaces or one tab.

      * item one
      * item two
      * item three

    ```julia
    function func(x)
        # ...
    end
    ```
```

!!! note
    파싱 중에 모든 각주 참조가 일치하는 각주가 있는지 확인하는 검사는 수행되지 않습니다.


### Horizontal rules

세 개의 하이픈(`---`)을 사용하여 `<hr>` HTML 태그와 동일한 효과를 얻을 수 있습니다. 예를 들어:

```
Text above the line.

---

And text below the line.
```

### Tables

기본 테이블은 아래에 설명된 구문을 사용하여 작성할 수 있습니다. 마크다운 테이블은 기능이 제한적이며, 위에서 논의된 다른 요소들과 달리 중첩된 최상위 요소를 포함할 수 없습니다. 오직 인라인 요소만 허용됩니다. 테이블은 항상 열 이름이 있는 헤더 행을 포함해야 합니다. 셀은 테이블의 여러 행이나 열을 가로지를 수 없습니다.

```
| Column One | Column Two | Column Three |
|:---------- | ---------- |:------------:|
| Row `1`    | Column `2` |              |
| *Row* 2    | **Row** 2  | Column ``3`` |
```

!!! note
    위의 예시에서 보여주듯이 각 `|` 문자 열은 수직으로 정렬되어야 합니다.

    열 헤더 구분자의 양쪽 끝에 있는 `:` 문자는 해당 행이 왼쪽 정렬, 오른쪽 정렬 또는 (양쪽 끝에 `:`가 있을 때) 가운데 정렬인지 지정합니다. `:` 문자를 제공하지 않으면 열이 기본적으로 오른쪽 정렬됩니다.


### Admonitions

특별히 형식화된 블록, 즉 주의 사항(admonitions)은 특정 발언을 강조하는 데 사용될 수 있습니다. 다음 `!!!` 구문을 사용하여 정의할 수 있습니다:

```
!!! note

    This is the content of the note.
    It is indented by 4 spaces. A tab would work as well.

!!! warning "Beware!"

    And this is another one.

    This warning admonition has a custom title: `"Beware!"`.
```

`!!!` 뒤의 첫 번째 단어는 주의의 유형을 선언합니다. 특별한 스타일을 생성해야 하는 표준 주의 유형이 있습니다. 즉, (심각도에 따라 내림차순으로) `danger`, `warning`, `info`/`note`, 그리고 `tip`입니다.

자신만의 주의 유형을 사용할 수도 있습니다. 단, 유형 이름은 소문자 라틴 문자(a-z)만 포함해야 합니다. 예를 들어, 다음과 같은 `terminology` 블록을 가질 수 있습니다:

```
!!! terminology "julia vs Julia"

    Strictly speaking, "Julia" refers to the language,
    and "julia" to the standard implementation.
```

그러나 Markdown을 렌더링하는 코드가 해당 특정 주의 유형을 특별 처리하지 않는 한, 기본 스타일링이 적용됩니다.

상자에 대한 사용자 정의 제목은 주의 유형 뒤에 문자열(따옴표로 묶인)로 제공될 수 있습니다. 주의 유형 뒤에 제목 텍스트가 지정되지 않으면 유형 이름이 제목으로 사용됩니다(예: `note` 주의의 경우 `"Note"`).

경고는 대부분의 다른 최상위 요소와 마찬가지로 다른 최상위 요소(예: 목록, 이미지)를 포함할 수 있습니다.

## [Markdown String Literals](@id stdlib-markdown-literals)

`md""` 매크로는 Markdown 문자열을 직접 Julia 코드에 삽입할 수 있게 해줍니다. 이 매크로는 Julia 소스 파일 내에 Markdown 형식의 텍스트를 포함하는 것을 간소화하도록 설계되었습니다.

### Usage

```julia
result = md"This is a **custom** Markdown string with [a link](http://example.com)."
```

## Markdown Syntax Extensions

줄리아의 마크다운은 기본 문자열 리터럴과 매우 유사한 방식으로 보간을 지원합니다. 차이점은 객체 자체를 마크다운 트리에 저장한다는 점입니다(문자열로 변환하는 것이 아닙니다). 마크다운 콘텐츠가 렌더링될 때 일반적인 `show` 메서드가 호출되며, 이러한 메서드는 일반적으로 재정의할 수 있습니다. 이 디자인은 기본 구문을 복잡하게 만들지 않고도 임의로 복잡한 기능(예: 참조)을 추가할 수 있도록 합니다.

원칙적으로, Markdown 파서는 패키지에 의해 임의로 확장될 수 있으며, 완전히 사용자 정의된 Markdown 버전을 사용할 수도 있지만, 일반적으로 이는 불필요합니다.

## [API reference](@id stdlib-markdown-api)

```@docs
Markdown.MD
Markdown.@md_str
Markdown.@doc_str
Markdown.html
Markdown.latex
```
