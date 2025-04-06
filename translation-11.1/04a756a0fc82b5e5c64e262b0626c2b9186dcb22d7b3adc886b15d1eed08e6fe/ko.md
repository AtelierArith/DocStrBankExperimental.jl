# [Getting Started](@id man-getting-started)

Julia 설치는 미리 컴파일된 바이너리를 사용하든 소스에서 컴파일하든 간단합니다. [https://julialang.org/downloads/](https://julialang.org/downloads/)의 지침에 따라 Julia를 다운로드하고 설치하세요.

만약 당신이 다음 언어 중 하나에서 줄리아로 오고 있다면, [MATLAB](@ref Noteworthy-differences-from-MATLAB), [R](@ref Noteworthy-differences-from-R), [Python](@ref Noteworthy-differences-from-Python), [C/C++](@ref Noteworthy-differences-from-C/C) 또는 [Common Lisp](@ref Noteworthy-differences-from-Common-Lisp) 섹션을 읽는 것으로 시작해야 합니다. 이는 줄리아가 이러한 언어들과 많은 미묘한 방식에서 다르기 때문에 일반적인 함정을 피하는 데 도움이 될 것입니다.

Julia를 배우고 실험하는 가장 쉬운 방법은 Julia 실행 파일을 두 번 클릭하거나 명령줄에서 `julia`를 실행하여 인터랙티브 세션(읽기-평가-출력 루프 또는 "REPL"이라고도 함)을 시작하는 것입니다:

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia> 1 + 2\n3\n\njulia> ans\n3\n```")
```

대화형 세션을 종료하려면 `CTRL-D`를 입력하세요 (Control/`^` 키와 `d` 키를 함께 누르세요) 또는 `exit()`를 입력하세요. 대화형 모드에서 실행될 때, `julia`는 배너를 표시하고 사용자에게 입력을 요청합니다. 사용자가 `1 + 2`와 같은 완전한 표현식을 입력하고 엔터를 누르면, 대화형 세션은 표현식을 평가하고 그 값을 보여줍니다. 표현식이 대화형 세션에 세미콜론과 함께 입력되면, 그 값은 표시되지 않습니다. 변수 `ans`는 마지막으로 평가된 표현식의 값에 바인딩되며, 이는 표시되든지 않든지 상관없습니다. `ans` 변수는 대화형 세션에서만 바인딩되며, 다른 방법으로 Julia 코드를 실행할 때는 바인딩되지 않습니다.

`file.jl` 파일에 작성된 표현식을 평가하려면 `include("file.jl")`를 작성하세요.

코드를 파일에서 비대화식으로 실행하려면, `julia` 명령의 첫 번째 인수로 제공할 수 있습니다:

```
$ julia script.jl
```

추가 인수를 Julia와 프로그램 `script.jl`에 전달할 수 있습니다. 사용 가능한 모든 옵션의 자세한 목록은 [Command-line Interface](@ref cli) 아래에서 확인할 수 있습니다.

## Resources

새로운 사용자가 시작하는 데 도움이 되는 유용한 학습 리소스의 선별된 목록은 주 Julia 웹사이트의 [learning](https://julialang.org/learning/) 페이지에서 찾을 수 있습니다.

REPL을 학습 자원으로 사용하려면 도움 모드로 전환하면 됩니다. 빈 `julia>` 프롬프트에서 다른 것을 입력하기 전에 `?`를 눌러 도움 모드로 전환하세요. 도움 모드에서 키워드를 입력하면 해당 키워드에 대한 문서와 예제가 제공됩니다. 마찬가지로, 여러분이 만날 수 있는 대부분의 함수나 다른 객체에 대해서도 동일하게 적용됩니다!

```
help?> begin
search: begin disable_sigint reenable_sigint

  begin

  begin...end denotes a block of code.
```

이미 줄리아를 조금 알고 있다면, [Performance Tips](@ref man-performance-tips)와 [Workflow Tips](@ref man-workflow-tips)를 미리 살펴보고 싶을 수도 있습니다.
