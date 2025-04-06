# [StyledStrings](@id stdlib-styledstrings)

```@meta
CurrentModule = StyledStrings
DocTestSetup = quote
    using StyledStrings
end
```

!!! note
    StyledStrings 및 AnnotatedStrings에 대한 API는 실험적이며 Julia 버전 간에 변경될 수 있습니다.


## [Styling](@id stdlib-styledstrings-styling)

문자열 작업 시, 포맷팅과 스타일링은 종종 부차적인 문제로 여겨진다.

예를 들어, 터미널에 출력할 때 [ANSI escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code#SGR_(Select_Graphic_Rendition)_parameters)를 출력에 추가하고 싶을 수 있습니다. HTML 스타일링 구성 요소(`<span style="...">` 등)를 출력할 때도 유사한 목적을 수행합니다. 원시 스타일링 구성 요소를 콘텐츠 자체 옆에 문자열로 삽입하는 것은 가능하지만, 이는 가장 기본적인 사용 사례를 제외하고는 잘 맞지 않는다는 것이 금방 드러납니다. 모든 터미널이 동일한 ANSI 코드를 지원하는 것은 아니며, 스타일이 적용된 콘텐츠의 너비를 계산할 때 스타일링 구성 요소를 신중하게 제거해야 하고, 이는 여러 출력 형식을 처리하기 전에 발생하는 문제입니다.

이 두통을 하류에서 널리 경험하게 두는 대신, 특별한 문자열 유형([`AnnotatedString`](@ref Base.AnnotatedString))의 도입으로 정면으로 해결됩니다. 이 문자열 유형은 다른 [`AbstractString`](@ref) 유형을 감싸고, 특정 영역(예: 문자 1부터 7까지는 굵고 빨간색)으로 서식 정보를 적용할 수 있게 합니다.

문자열의 영역은 [`Face`](@ref StyledStrings.Face) (타입페이스라고 생각하세요)를 적용하여 스타일링됩니다. 이는 스타일링 정보를 담고 있는 구조입니다. 편의상, 전역 faces 사전의 얼굴(예: `shadow`)은 `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365`를 직접 제공하는 대신 이름으로만 지정할 수 있습니다.

이러한 기능과 함께, 우리는 [`AnnotatedString`](@ref Base.AnnotatedString)를 구성하는 편리한 방법도 제공합니다. 이는 [Styled String Literals](@ref stdlib-styledstring-literals)에 자세히 설명되어 있습니다.

```@repl demo
using StyledStrings
styled"{yellow:hello} {blue:there}"
```

## [Annotated Strings](@id man-annotated-strings)

때때로 문자열의 영역과 관련된 메타데이터를 보유하는 것이 유용할 수 있습니다. [`AnnotatedString`](@ref Base.AnnotatedString)는 다른 문자열을 감싸고 있으며, 그 일부에 레이블이 있는 값(`:label => value`)으로 주석을 달 수 있게 해줍니다. 모든 일반 문자열 작업은 기본 문자열에 적용됩니다. 그러나 가능할 때 스타일링 정보는 보존됩니다. 이는 `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67`를 조작할 수 있음을 의미합니다. 부분 문자열을 가져오고, 패딩을 추가하고, 다른 문자열과 연결하는 등의 작업을 수행하면 메타데이터 주석이 함께 따라옵니다.

이 문자열 유형은 [StyledStrings stdlib](@ref stdlib-styledstrings)에 기본적이며, 스타일링 정보를 보유하기 위해 `:face`로 레이블이 지정된 주석을 사용합니다.

[`AnnotatedString`](@ref Base.AnnotatedString)를 연결할 때, 문자열 주석을 유지하려면 [`annotatedstring`](@ref StyledStrings.annotatedstring)를 사용해야 합니다. [`string`](@ref) 대신에 말이죠.

```jldoctest
julia> str = AnnotatedString("hello there", [(1:5, :word, :greeting), (7:11, :label, 1)])
"hello there"

julia> length(str)
11

julia> lpad(str, 14)
"   hello there"

julia> typeof(lpad(str, 7))
AnnotatedString{String}

julia> str2 = AnnotatedString(" julia", [(2:6, :face, :magenta)])
" julia"

julia> annotatedstring(str, str2)
"hello there julia"

julia> str * str2 == annotatedstring(str, str2) # *-concatenation works
true
```

[`AnnotatedString`](@ref Base.AnnotatedString)의 주석은 [`annotations`](@ref StyledStrings.annotations) 및 [`annotate!`](@ref StyledStrings.annotate!) 함수를 통해 접근하고 수정할 수 있습니다.

## Styling via [`AnnotatedString`](@ref Base.AnnotatedString)s

## [Faces](@id stdlib-styledstrings-faces)

### The `Face` type

A [`Face`](@ref StyledStrings.Face)는 텍스트가 설정될 수 있는 서체의 세부 정보를 지정합니다. 이는 다양한 형식에서 잘 일반화되는 기본 속성 집합을 포함합니다. 즉:

  * `글꼴`
  * `높이`
  * `무게`
  * `기울기`
  * `전경`
  * `배경`
  * `밑줄`
  * `취소선`
  * `역`
  * `상속`

특정 속성이 어떤 형태를 취하는지에 대한 자세한 내용은 [`Face`](@ref StyledStrings.Face) 문서 문자열을 참조하십시오. 특히 관심 있는 것은 `inherit`로, 이는 다른 `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365`에서 속성을 *상속*할 수 있게 해줍니다.

### The global faces dictionary

특정 스타일을 더 편리하게 참조할 수 있도록, `Dict{Symbol, Face}`라는 전역 변수가 있어 [`Face`](@ref StyledStrings.Face)를 이름으로 간단히 참조할 수 있습니다. 패키지는 [`addface!`](@ref StyledStrings.addface!) 함수를 통해 이 사전에 얼굴을 추가할 수 있으며, 로드된 얼굴은 쉽게 [customized](@ref stdlib-styledstrings-face-toml)할 수 있습니다.

!!! warning "Appropriate face naming"
    새로운 얼굴을 등록하는 모든 패키지는 패키지 이름으로 접두사가 붙도록 해야 합니다. 즉, 형식 `mypackage_myface`를 따라야 합니다. 이는 예측 가능성을 위해 중요하며, 이름 충돌을 방지하기 위해서입니다.

    또한, 패키지는 직접적인 색상과 스타일(예: `cyan`)보다 *의미론적* 얼굴(예: `code`)을 사용하고 도입하는 데 주의해야 합니다. 이는 사용 의도를 더 명확하게 하고, 조합 가능성을 높이며, 사용자 맞춤화를 더 직관적으로 만드는 등 여러 면에서 유용합니다.


패키지 접두사 규칙에 대한 두 가지 면제 세트가 있습니다:

  * 기본 얼굴 사전의 기본 값에 포함된 기본 얼굴 세트
  * 줄리아의 표준 라이브러리인 `JuliaSyntaxHighlighting`에 의해 도입된 얼굴들

#### [Basic faces](@id stdlib-styledstrings-basic-faces)

기본 얼굴은 널리 적용 가능한 일반적인 아이디어를 나타내기 위해 의도되었습니다.

특정 속성을 가진 텍스트를 설정하기 위해 `bold`, `light`, `italic`, `underline`, `strikethrough`, 및 `inverse` 글꼴을 사용합니다.

16개의 터미널 색상에 대한 이름이 지정된 얼굴도 있습니다: `검정`, `빨강`, `초록`, `노랑`, `파랑`, `마젠타`, `청록`, `흰색`, `밝은 검정`/`회색`, `밝은 빨강`, `밝은 초록`, `밝은 파랑`, `밝은 마젠타`, `밝은 청록`, `밝은 흰색`.

그림자 텍스트(즉, 희미하지만 존재하는 텍스트)를 위해 `shadow` 페이스가 있습니다. 선택된 영역을 나타내기 위해 `region` 페이스가 있습니다. 강조 및 하이라이팅을 위해 각각 `emphasis`와 `highlight` 페이스가 정의되어 있습니다. 코드와 유사한 텍스트를 위해 `code`도 있습니다.

메시지의 심각성을 시각적으로 나타내기 위해 `error`, `warning`, `success`, `info`, `note`, 및 `tip` 얼굴이 정의되어 있습니다.

### [Customisation of faces (`Faces.toml`)](@id stdlib-styledstrings-face-toml)

글로벌 얼굴 사전의 이름 얼굴이 사용자 정의 가능하다는 것은 좋습니다. 테마와 미학은 멋지며, 접근성 이유로도 중요합니다. TOML 파일은 [`Face`](@ref StyledStrings.Face) 사양의 목록으로 구문 분석될 수 있으며, 이는 얼굴 사전의 기존 항목과 병합됩니다.

A [`Face`](@ref StyledStrings.Face)는 TOML에서 다음과 같이 표현됩니다:

```toml
[facename]
attribute = "value"
...

[package.facename]
attribute = "value"
```

예를 들어, `shadow` 얼굴이 읽기 너무 어렵다면 다음과 같이 더 밝게 만들 수 있습니다:

```toml
[shadow]
foreground = "white"
```

초기화 시, 첫 번째 줄리아 저장소(보통 `~/.julia`) 아래의 `config/faces.toml` 파일이 로드됩니다.

### Applying faces to a `AnnotatedString`

관례적으로, [`AnnotatedString`](@ref Base.AnnotatedString)의 `:face` 속성은 현재 적용되는 [`Face`](@ref StyledStrings.Face)에 대한 정보를 담고 있습니다. 이는 전역 얼굴 사전에서 `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365`의 이름을 지정하는 단일 `Symbol`, `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` 자체, 또는 둘 중 하나의 벡터 형태로 제공될 수 있습니다.

`show(::IO, ::MIME"text/plain", ::AnnotatedString)` 및 `show(::IO, ::MIME"text/html", ::AnnotatedString)` 메서드는 모두 `:face` 속성을 살펴보고 전체 스타일을 결정할 때 이를 모두 병합합니다.

우리는 `AnnotatedString`을 생성할 때 `:face` 속성을 공급하거나, 이후에 속성 목록에 추가하거나, 편리한 [Styled String literals](@ref stdlib-styledstring-literals)를 사용할 수 있습니다.

```@repl demo
str1 = AnnotatedString("blue text", [(1:9, :face, :blue)])
str2 = styled"{blue:blue text}"
str1 == str2
sprint(print, str1, context = :color => true)
sprint(show, MIME("text/html"), str1, context = :color => true)
```

## [Styled String Literals](@id stdlib-styledstring-literals)

[`AnnotatedString`](@ref Base.AnnotatedString)의 구조를 쉽게 하기 위해, [`Face`](@ref StyledStrings.Face)가 적용된 [`styled"..."`](@ref @styled_str) 스타일의 문자열 리터럴은 콘텐츠와 속성을 사용자 정의 문법을 통해 쉽게 표현할 수 있도록 합니다.

[`styled"..."`](@ref @styled_str) 리터럴 내에서 중괄호는 특수 문자로 간주되며 일반 사용에서 이스케이프되어야 합니다(`\{`, `\}`). 이를 통해 (중첩 가능한) `{annotations...:text}` 구조로 주석을 표현할 수 있습니다.

`annotations...` 구성 요소는 세 가지 유형의 주석으로 구성된 쉼표로 구분된 목록입니다.

  * 얼굴 이름
  * 인라인 `Face` 표현 `(key=val,...)`
  * `key=value` 쌍

보간(interpolation)은 인라인 페이스 키를 제외한 모든 곳에서 가능합니다.

자세한 문법 정보는 [`styled"..."`](@ref @styled_str) 문서 문자열의 확장 도움말을 참조하세요.

위에서 언급한 내장 얼굴 목록을 다음과 같이 보여줄 수 있습니다:

```julia-repl
julia> println(styled"
The basic font-style attributes are {bold:bold}, {light:light}, {italic:italic},
{underline:underline}, and {strikethrough:strikethrough}.

In terms of color, we have named faces for the 16 standard terminal colors:
 {black:■} {red:■} {green:■} {yellow:■} {blue:■} {magenta:■} {cyan:■} {white:■}
 {bright_black:■} {bright_red:■} {bright_green:■} {bright_yellow:■} {bright_blue:■} {bright_magenta:■} {bright_cyan:■} {bright_white:■}

Since {code:bright_black} is effectively grey, we define two aliases for it:
{code:grey} and {code:gray} to allow for regional spelling differences.

To flip the foreground and background colors of some text, you can use the
{code:inverse} face, for example: {magenta:some {inverse:inverse} text}.

The intent-based basic faces are {shadow:shadow} (for dim but visible text),
{region:region} for selections, {emphasis:emphasis}, and {highlight:highlight}.
As above, {code:code} is used for code-like text.

Lastly, we have the 'message severity' faces: {error:error}, {warning:warning},
{success:success}, {info:info}, {note:note}, and {tip:tip}.

Remember that all these faces (and any user or package-defined ones) can
arbitrarily nest and overlap, {region,tip:like {bold,italic:so}}.")
```

```@raw comment
Documenter doesn't properly represent all the styling above, so I've converted it manually to HTML and LaTeX.
```

```@raw html
<pre>
 The basic font-style attributes are <span style="font-weight: 700;">bold</span>, <span style="font-weight: 300;">light</span>, <span style="font-style: italic;">italic</span>,
 <span style="text-decoration: underline;">underline</span>, and <span style="text-decoration: line-through">strikethrough</span>.

 In terms of color, we have named faces for the 16 standard terminal colors:
  <span style="color: #1c1a23;">■</span> <span style="color: #a51c2c;">■</span> <span style="color: #25a268;">■</span> <span style="color: #e5a509;">■</span> <span style="color: #195eb3;">■</span> <span style="color: #803d9b;">■</span> <span style="color: #0097a7;">■</span> <span style="color: #dddcd9;">■</span>
  <span style="color: #76757a;">■</span> <span style="color: #ed333b;">■</span> <span style="color: #33d079;">■</span> <span style="color: #f6d22c;">■</span> <span style="color: #3583e4;">■</span> <span style="color: #bf60ca;">■</span> <span style="color: #26c6da;">■</span> <span style="color: #f6f5f4;">■</span>

 Since <span style="color: #0097a7;">bright_black</span> is effectively grey, we define two aliases for it:
 <span style="color: #0097a7;">grey</span> and <span style="color: #0097a7;">gray</span> to allow for regional spelling differences.

 To flip the foreground and background colors of some text, you can use the
 <span style="color: #0097a7;">inverse</span> face, for example: <span style="color: #803d9b;">some </span><span style="background-color: #803d9b;">inverse</span><span style="color: #803d9b;"> text</span>.

 The intent-based basic faces are <span style="color: #76757a;">shadow</span> (for dim but visible text),
 <span style="background-color: #3a3a3a;">region</span> for selections, <span style="color: #195eb3;">emphasis</span>, and <span style="background-color: #195eb3;">highlight</span>.
 As above, <span style="color: #0097a7;">code</span> is used for code-like text.

 Lastly, we have the 'message severity' faces: <span style="color: #ed333b;">error</span>, <span style="color: #e5a509;">warning</span>,
 <span style="color: #25a268;">success</span>, <span style="color: #26c6da;">info</span>, <span style="color: #76757a;">note</span>, and <span style="color: #33d079;">tip</span>.

 Remember that all these faces (and any user or package-defined ones) can
 arbitrarily nest and overlap, <span style="color: #33d079;background-color: #3a3a3a;">like <span style="font-weight: 700;font-style: italic;">so</span></span>.</pre>
```

```@raw latex
\begingroup
\ttfamily
\setlength{\parindent}{0pt}
\setlength{\parskip}{\baselineskip}

The basic font-style attributes are {\fontseries{b}\selectfont bold}, {\fontseries{l}\selectfont light}, {\fontshape{it}\selectfont italic},\\
\underline{underline}, and {strikethrough}.

In terms of color, we have named faces for the 16 standard terminal colors:\\
{\color[HTML]{1c1a23}\(\blacksquare\)} {\color[HTML]{a51c2c}\(\blacksquare\)} {\color[HTML]{25a268}\(\blacksquare\)}
{\color[HTML]{e5a509}\(\blacksquare\)} {\color[HTML]{195eb3}\(\blacksquare\)} {\color[HTML]{803d9b}\(\blacksquare\)}
{\color[HTML]{0097a7}\(\blacksquare\)} {\color[HTML]{dddcd9}\(\blacksquare\)} \\
{\color[HTML]{76757a}\(\blacksquare\)} {\color[HTML]{ed333b}\(\blacksquare\)} {\color[HTML]{33d079}\(\blacksquare\)} {\color[HTML]{f6d22c}\(\blacksquare\)} {\color[HTML]{3583e4}\(\blacksquare\)} {\color[HTML]{bf60ca}\(\blacksquare\)} {\color[HTML]{26c6da}\(\blacksquare\)} {\color[HTML]{f6f5f4}\(\blacksquare\)}

Since {\color[HTML]{0097a7}bright\_black} is effectively grey, we define two aliases for it:\\
{\color[HTML]{0097a7}grey} and {\color[HTML]{0097a7}gray} to allow for regional spelling differences.

To flip the foreground and background colors of some text, you can use the\\
{\color[HTML]{0097a7}inverse} face, for example: {\color[HTML]{803d9b}some \colorbox[HTML]{803d9b}{\color[HTML]{000000}inverse} text}.

The intent-based basic faces are {\color[HTML]{76757a}shadow} (for dim but visible text),\\
\colorbox[HTML]{3a3a3a}{region} for selections, {\color[HTML]{195eb3}emphasis}, and \colorbox[HTML]{195eb3}{highlight}.\\
As above, {\color[HTML]{0097a7}code} is used for code-like text.

Lastly, we have the 'message severity' faces: {\color[HTML]{ed333b}error}, {\color[HTML]{e5a509}warning},\\
{\color[HTML]{25a268}success}, {\color[HTML]{26c6da}info}, {\color[HTML]{76757a}note}, and {\color[HTML]{33d079}tip}.

Remember that all these faces (and any user or package-defined ones) can\\
arbitrarily nest and overlap, \colorbox[HTML]{3a3a3a}{\color[HTML]{33d079}like
  {\fontseries{b}\fontshape{it}\selectfont so}}.
\endgroup
```

## [API reference](@id stdlib-styledstrings-api)

### Styling and Faces

```@docs
StyledStrings.@styled_str
StyledStrings.styled
StyledStrings.Face
StyledStrings.addface!
StyledStrings.withfaces
StyledStrings.SimpleColor
StyledStrings.parse(::Type{StyledStrings.SimpleColor}, ::String)
StyledStrings.tryparse(::Type{StyledStrings.SimpleColor}, ::String)
StyledStrings.merge(::StyledStrings.Face, ::StyledStrings.Face)
```
