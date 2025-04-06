```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/REPL/docs/src/index.md"
```

# The Julia REPL

Julia는 `julia` 실행 파일에 내장된 완전한 기능의 대화형 명령줄 REPL(읽기-평가-출력 루프)을 제공합니다. Julia 문장을 빠르고 쉽게 평가할 수 있을 뿐만 아니라, 검색 가능한 기록, 탭 완성, 많은 유용한 키 바인딩, 전용 도움말 및 셸 모드를 갖추고 있습니다. REPL은 인수 없이 `julia`를 호출하거나 실행 파일을 두 번 클릭하여 시작할 수 있습니다:

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia>\n```")
```

대화형 세션을 종료하려면 빈 줄에서 `^D`를 입력하세요 – 제어 키와 `d` 키를 함께 누릅니다 – 또는 `exit()`를 입력한 후 리턴 또는 엔터 키를 누릅니다. REPL은 배너와 함께 `julia>` 프롬프트로 인사합니다.

## The different prompt modes

### The Julian mode

REPL은 다섯 가지 주요 작동 모드를 가지고 있습니다. 첫 번째이자 가장 일반적인 모드는 줄리아 프롬프트입니다. 이는 기본 작동 모드이며, 각 새로운 줄은 처음에 `julia>`로 시작합니다. 여기에서 줄리아 표현식을 입력할 수 있습니다. 완전한 표현식을 입력한 후 리턴 또는 엔터를 누르면 입력이 평가되고 마지막 표현식의 결과가 표시됩니다.

```jldoctest
julia> string(1 + 2)
"3"
```

대화형 작업에 고유한 유용한 기능이 여러 가지 있습니다. 결과를 보여주는 것 외에도 REPL은 결과를 변수 `ans`에 바인딩합니다. 줄 끝에 세미콜론을 추가하면 결과 표시를 억제하는 플래그로 사용할 수 있습니다.

```jldoctest
julia> string(3 * 4);

julia> ans
"12"
```

줄리아 모드에서 REPL은 *프롬프트 붙여넣기*라는 기능을 지원합니다. 이는 `julia>`로 시작하는 텍스트를 REPL에 붙여넣을 때 활성화됩니다. 이 경우, `julia>`로 시작하는 표현식(및 다른 REPL 모드 프롬프트: `shell>`, `help?>`, `pkg>` )만 구문 분석되며, 나머지는 제거됩니다. 이를 통해 REPL 세션에서 복사한 텍스트 덩어리를 프롬프트와 출력을 지우지 않고 붙여넣을 수 있습니다. 이 기능은 기본적으로 활성화되어 있지만 `REPL.enable_promptpaste(::Bool)`를 사용하여 원할 때 비활성화하거나 활성화할 수 있습니다. 활성화된 경우, 이 단락 위의 코드 블록을 REPL에 직접 붙여넣어 시도해 볼 수 있습니다. 이 기능은 붙여넣기가 발생할 때 감지하는 데 제한이 있는 표준 Windows 명령 프롬프트에서는 작동하지 않습니다.

객체는 [`show`](@ref) 함수를 사용하여 REPL에서 출력되며, 특정 [`IOContext`](@ref)가 사용됩니다. 특히 `:limit` 속성은 `true`로 설정됩니다. 다른 속성은 특정 `show` 메서드에서 이미 설정되어 있지 않은 경우 기본값을 받을 수 있으며, 예를 들어 `:compact`가 있습니다. 실험적 기능으로, `Base.active_repl.options.iocontext` 사전을 통해 REPL에서 사용되는 속성을 지정할 수 있습니다(속성에 값을 연결). 예를 들어:

```julia-repl
julia> rand(2, 2)
2×2 Array{Float64,2}:
 0.8833    0.329197
 0.719708  0.59114

julia> show(IOContext(stdout, :compact => false), "text/plain", rand(2, 2))
 0.43540323669187075  0.15759787870609387
 0.2540832269192739   0.4597637838786053
julia> Base.active_repl.options.iocontext[:compact] = false;

julia> rand(2, 2)
2×2 Array{Float64,2}:
 0.2083967319174056  0.13330606013126012
 0.6244375177790158  0.9777957560761545
```

시작 시 이 사전의 값을 자동으로 정의하기 위해, 예를 들어 `~/.julia/config/startup.jl` 파일에서 [`atreplinit`](@ref) 함수를 사용할 수 있습니다:

```julia
atreplinit() do repl
    repl.options.iocontext[:compact] = false
end
```

### Help mode

커서가 줄의 시작 부분에 있을 때, 프롬프트는 `?`를 입력하여 도움 모드로 변경할 수 있습니다. Julia는 도움 모드에서 입력된 모든 것에 대한 도움이나 문서를 출력하려고 시도합니다:

```julia-repl
julia> ? # upon typing ?, the prompt changes (in place) to: help?>

help?> string
search: string String Cstring Cwstring RevString randstring bytestring SubString

  string(xs...)

  Create a string from any values using the print function.
```

매크로, 유형 및 변수도 쿼리할 수 있습니다:

```
help?> @time
  @time

  A macro to execute an expression, printing the time it took to execute, the number of allocations,
  and the total number of bytes its execution caused to be allocated, before returning the value of the
  expression.

  See also @timev, @timed, @elapsed, and @allocated.

help?> Int32
search: Int32 UInt32

  Int32 <: Signed

  32-bit signed integer type.
```

문자열 또는 정규 표현식 리터럴은 [`apropos`](@ref)를 사용하여 모든 문서 문자열을 검색합니다:

```
help?> "aprop"
REPL.stripmd
Base.Docs.apropos

help?> r"ap..p"
Base.:∘
Base.shell_escape_posixly
Distributed.CachingPool
REPL.stripmd
Base.Docs.apropos
```

도움 모드의 또 다른 기능은 확장된 문서 문자열에 접근할 수 있는 능력입니다. `?Print` 대신 `??Print`와 같은 것을 입력하면 소스 코드 문서의 `# 확장 도움말` 섹션이 표시됩니다.

도움 모드는 줄의 시작에서 백스페이스를 눌러 종료할 수 있습니다.

### [Shell mode](@id man-shell-mode)

도움 모드가 문서에 빠르게 접근하는 데 유용한 것처럼, 또 다른 일반적인 작업은 시스템 셸을 사용하여 시스템 명령을 실행하는 것입니다. 줄의 시작 부분에서 `?`를 입력하면 도움 모드로 들어가듯이, 세미콜론(`;`)을 입력하면 셸 모드로 들어갑니다. 그리고 줄의 시작 부분에서 백스페이스를 눌러서 나갈 수 있습니다.

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> echo hello
hello
```

!!! note
    Windows 사용자의 경우, Julia의 셸 모드는 Windows 셸 명령을 노출하지 않습니다. 따라서, 다음은 실패할 것입니다:


```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> dir
ERROR: IOError: could not spawn `dir`: no such file or directory (ENOENT)
Stacktrace!
.......
```

그러나 다음과 같이 `PowerShell`에 접근할 수 있습니다:

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> powershell
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.
PS C:\Users\elm>
```

... 그리고 `cmd.exe`에 이렇게 ( `dir` 명령어를 참조하세요):

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> cmd
Microsoft Windows [version 10.0.17763.973]
(c) 2018 Microsoft Corporation. All rights reserved.
C:\Users\elm>dir
 Volume in drive C has no label
 Volume Serial Number is 1643-0CD7
  Directory of C:\Users\elm

29/01/2020  22:15    <DIR>          .
29/01/2020  22:15    <DIR>          ..
02/02/2020  08:06    <DIR>          .atom
```

### Pkg mode

패키지 관리자 모드는 패키지를 로드하고 업데이트하기 위한 특수 명령을 수용합니다. 이는 Julian REPL 프롬프트에서 `]` 키를 눌러 진입하며, CTRL-C를 누르거나 줄의 시작 부분에서 백스페이스 키를 눌러 종료합니다. 이 모드의 프롬프트는 `pkg>`입니다. 이 모드는 자체 도움말 모드를 지원하며, 이는 `pkg>` 프롬프트의 줄 시작 부분에서 `?`를 눌러 진입할 수 있습니다. 패키지 관리자 모드는 Pkg 매뉴얼에 문서화되어 있으며, 해당 매뉴얼은 [https://julialang.github.io/Pkg.jl/v1/](https://julialang.github.io/Pkg.jl/v1/)에서 확인할 수 있습니다.

### Search modes

모든 모드에서 실행된 명령어는 검색할 수 있는 히스토리 파일에 저장됩니다. 이전 히스토리를 통해 점진적인 검색을 시작하려면 `^R`을 입력하세요 – 컨트롤 키와 `r` 키를 함께 누릅니다. 프롬프트는 ```(reverse-i-search)`':```로 변경되며, 입력하는 동안 검색 쿼리가 따옴표 안에 나타납니다. 쿼리와 일치하는 가장 최근 결과는 더 많은 내용을 입력할수록 콜론 오른쪽에서 동적으로 업데이트됩니다. 동일한 쿼리를 사용하여 이전 결과를 찾으려면 `^R`을 다시 입력하면 됩니다.

`^R`는 역 검색을 나타내고, `^S`는 정방향 검색을 나타내며, 프롬프트는 ```(i-search)`':```입니다. 두 가지는 서로 결합하여 이전 또는 다음 일치하는 결과를 각각 이동하는 데 사용할 수 있습니다.

모든 실행된 명령은 Julia REPL에서 `~/.julia/logs/repl_history.jl`에 기록되며, 실행된 시간과 현재 REPL 모드가 함께 저장됩니다. 검색 모드는 이전에 실행한 명령을 찾기 위해 이 로그 파일을 조회합니다. 이는 Julia에 `--history-file=no` 플래그를 전달하여 시작 시 비활성화할 수 있습니다.

## Key bindings

Julia REPL은 키 바인딩을 잘 활용합니다. 여러 제어 키 바인딩이 위에서 이미 소개되었습니다(`^D`는 종료, `^R`과 `^S`는 검색용), 하지만 더 많은 바인딩이 있습니다. 제어 키 외에도 메타 키 바인딩이 있습니다. 이는 플랫폼에 따라 다르지만, 대부분의 터미널은 메타 키를 보내기 위해 키와 함께 alt- 또는 option-을 누르도록 기본 설정되어 있거나 그렇게 구성할 수 있습니다. 또는 Esc를 누른 다음 키를 누르는 방법도 있습니다.

| Keybinding           | Description                                                                                                |
|:-------------------- |:---------------------------------------------------------------------------------------------------------- |
| **Program control**  |                                                                                                            |
| `^D`                 | Exit (when buffer is empty)                                                                                |
| `^C`                 | Interrupt or cancel                                                                                        |
| `^L`                 | Clear console screen                                                                                       |
| Return/Enter, `^J`   | New line, executing if it is complete                                                                      |
| meta-Return/Enter    | Insert new line without executing it                                                                       |
| `?` or `;`           | Enter help or shell mode (when at start of a line)                                                         |
| `^R`, `^S`           | Incremental history search, described above                                                                |
| **Cursor movement**  |                                                                                                            |
| Right arrow, `^F`    | Move right one character                                                                                   |
| Left arrow, `^B`     | Move left one character                                                                                    |
| ctrl-Right, `meta-F` | Move right one word                                                                                        |
| ctrl-Left, `meta-B`  | Move left one word                                                                                         |
| Home, `^A`           | Move to beginning of line                                                                                  |
| End, `^E`            | Move to end of line                                                                                        |
| Up arrow, `^P`       | Move up one line (or change to the previous history entry that matches the text before the cursor)         |
| Down arrow, `^N`     | Move down one line (or change to the next history entry that matches the text before the cursor)           |
| Shift-Arrow Key      | Move cursor according to the direction of the Arrow key, while activating the region ("shift selection")   |
| Page-up, `meta-P`    | Change to the previous history entry                                                                       |
| Page-down, `meta-N`  | Change to the next history entry                                                                           |
| `meta-<`             | Change to the first history entry (of the current session if it is before the current position in history) |
| `meta->`             | Change to the last history entry                                                                           |
| `^-Space`            | Set the "mark" in the editing region (and de-activate the region if it's active)                           |
| `^-Space ^-Space`    | Set the "mark" in the editing region and make the region "active", i.e. highlighted                        |
| `^G`                 | De-activate the region (i.e. make it not highlighted)                                                      |
| `^X^X`               | Exchange the current position with the mark                                                                |
| **Editing**          |                                                                                                            |
| Backspace, `^H`      | Delete the previous character, or the whole region when it's active                                        |
| Delete, `^D`         | Forward delete one character (when buffer has text)                                                        |
| meta-Backspace       | Delete the previous word                                                                                   |
| `meta-d`             | Forward delete the next word                                                                               |
| `^W`                 | Delete previous text up to the nearest whitespace                                                          |
| `meta-w`             | Copy the current region in the kill ring                                                                   |
| `meta-W`             | "Kill" the current region, placing the text in the kill ring                                               |
| `^U`                 | "Kill" to beginning of line, placing the text in the kill ring                                             |
| `^K`                 | "Kill" to end of line, placing the text in the kill ring                                                   |
| `^Y`                 | "Yank" insert the text from the kill ring                                                                  |
| `meta-y`             | Replace a previously yanked text with an older entry from the kill ring                                    |
| `^T`                 | Transpose the characters about the cursor                                                                  |
| `meta-Up arrow`      | Transpose current line with line above                                                                     |
| `meta-Down arrow`    | Transpose current line with line below                                                                     |
| `meta-u`             | Change the next word to uppercase                                                                          |
| `meta-c`             | Change the next word to titlecase                                                                          |
| `meta-l`             | Change the next word to lowercase                                                                          |
| `^/`, `^_`           | Undo previous editing action                                                                               |
| `^Q`                 | Write a number in REPL and press `^Q` to open editor at corresponding stackframe or method                 |
| `meta-Left Arrow`    | Indent the current line on the left                                                                        |
| `meta-Right Arrow`   | Indent the current line on the right                                                                       |
| `meta-.`             | Insert last word from previous history entry                                                               |
| `meta-e`             | Edit the current input in an editor                                                                        |

### Customizing keybindings

줄리아의 REPL 키 바인딩은 `REPL.setup_interface`에 사전을 전달하여 사용자의 선호에 맞게 완전히 사용자화할 수 있습니다. 이 사전의 키는 문자 또는 문자열일 수 있습니다. 키 `'*'`는 기본 동작을 나타냅니다. Control과 문자 `x`의 바인딩은 `"^x"`로 표시됩니다. Meta와 `x`는 `"\\M-x"` 또는 `"\ex"`로 쓸 수 있으며, Control과 `x`는 `"\\C-x"` 또는 `"^x"`로 쓸 수 있습니다. 사용자 정의 키맵의 값은 `nothing`(입력을 무시해야 함을 나타냄) 또는 `(PromptState, AbstractREPL, Char)` 서명을 수용하는 함수여야 합니다. `REPL.setup_interface` 함수는 REPL이 초기화되기 전에 호출되어야 하며, [`atreplinit`](@ref)로 작업을 등록해야 합니다. 예를 들어, 위쪽 및 아래쪽 화살표 키를 사용하여 접두사 검색 없이 기록을 탐색하도록 바인딩하려면 다음 코드를 `~/.julia/config/startup.jl`에 넣을 수 있습니다:

```julia
import REPL
import REPL.LineEdit

const mykeys = Dict{Any,Any}(
    # Up Arrow
    "\e[A" => (s,o...)->(LineEdit.edit_move_up(s) || LineEdit.history_prev(s, LineEdit.mode(s).hist)),
    # Down Arrow
    "\e[B" => (s,o...)->(LineEdit.edit_move_down(s) || LineEdit.history_next(s, LineEdit.mode(s).hist))
)

function customize_keys(repl)
    repl.interface = REPL.setup_interface(repl; extra_repl_keymap = mykeys)
end

atreplinit(customize_keys)
```

사용자는 키 입력에 대한 사용 가능한 작업을 발견하기 위해 `LineEdit.jl`을 참조해야 합니다.

## Tab completion

줄리안, pkg 및 도움 모드의 REPL에서 함수나 타입의 첫 몇 글자를 입력한 후 탭 키를 누르면 모든 일치 항목의 목록을 얻을 수 있습니다:

```julia-repl
julia> x[TAB]
julia> xor
```

일부 경우에는 다음의 모호성까지 이름의 일부만 완성합니다:

```julia-repl
julia> mapf[TAB]
julia> mapfold
```

탭을 다시 누르면, 이것을 완성할 수 있는 항목 목록이 표시됩니다:

```julia-repl
julia> mapfold[TAB]
mapfoldl mapfoldr
```

입력 줄 끝에 단일 완전 탭 완성 결과가 있을 때 2개 이상의 문자가 입력되면 완성 힌트가 더 밝은 색상으로 표시됩니다. 이는 `Base.active_repl.options.hint_tab_completes = false`를 통해 비활성화할 수 있습니다.

!!! compat "Julia 1.11"
    탭 자동 완성 힌트가 Julia 1.11에 추가되었습니다.


REPL의 다른 구성 요소와 마찬가지로 검색은 대소문자를 구분합니다:

```julia-repl
julia> stri[TAB]
stride     strides     string      strip

julia> Stri[TAB]
StridedArray    StridedMatrix    StridedVecOrMat  StridedVector    String
```

탭 키는 또한 LaTeX 수학 기호를 해당 유니코드 동등물로 대체하고 LaTeX 일치를 목록으로 가져오는 데 사용할 수 있습니다:

```julia-repl
julia> \pi[TAB]
julia> π
π = 3.1415926535897...

julia> e\_1[TAB] = [1,0]
julia> e₁ = [1,0]
2-element Array{Int64,1}:
 1
 0

julia> e\^1[TAB] = [1 0]
julia> e¹ = [1 0]
1×2 Array{Int64,2}:
 1  0

julia> \sqrt[TAB]2     # √ is equivalent to the sqrt function
julia> √2
1.4142135623730951

julia> \hbar[TAB](h) = h / 2\pi[TAB]
julia> ħ(h) = h / 2π
ħ (generic function with 1 method)

julia> \h[TAB]
\hat              \hermitconjmatrix  \hkswarow          \hrectangle
\hatapprox        \hexagon           \hookleftarrow     \hrectangleblack
\hbar             \hexagonblack      \hookrightarrow    \hslash
\heartsuit        \hksearow          \house             \hspace

julia> α="\alpha[TAB]"   # LaTeX completion also works in strings
julia> α="α"
```

매뉴얼의 [Unicode Input](@ref) 섹션에서 전체 탭 완성 목록을 찾을 수 있습니다.

경로 완료는 문자열과 줄리아의 셸 모드에서 작동합니다:

```julia-repl
julia> path="/[TAB]"
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
shell> /[TAB]
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
```

사전 키는 탭 완성을 통해서도 입력할 수 있습니다:

```julia-repl
julia> foo = Dict("qwer1"=>1, "qwer2"=>2, "asdf"=>3)
Dict{String,Int64} with 3 entries:
  "qwer2" => 2
  "asdf"  => 3
  "qwer1" => 1

julia> foo["q[TAB]

"qwer1" "qwer2"
julia> foo["qwer
```

탭 완성 기능은 필드를 완성하는 데에도 도움이 될 수 있습니다:

```julia-repl
julia> x = 3 + 4im;

julia> x.[TAB][TAB]
im re

julia> import UUIDs

julia> UUIDs.uuid[TAB][TAB]
uuid1        uuid4         uuid5        uuid_version
```

함수의 출력 필드도 완성할 수 있습니다:

```julia-repl
julia> split("","")[1].[TAB]
lastindex  offset  string
```

함수의 출력 필드 완성은 타입 추론을 사용하며, 함수가 타입 안정적일 경우에만 필드를 제안할 수 있습니다.

탭 완성 기능은 입력 인수와 일치하는 사용 가능한 메서드를 조사하는 데 도움이 될 수 있습니다:

```julia-repl
julia> max([TAB] # All methods are displayed, not shown here due to size of the list

julia> max([1, 2], [TAB] # All methods where `Vector{Int}` matches as first argument
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281

julia> max([1, 2], max(1, 2), [TAB] # All methods matching the arguments.
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281
```

키워드는 아래 줄에서 `limit` 및 `keepempty`가 키워드 인수인 것처럼 제안된 방법 후 `;`에 표시됩니다:

```julia-repl
julia> split("1 1 1", [TAB]
split(str::AbstractString; limit, keepempty) in Base at strings/util.jl:302
split(str::T, splitter; limit, keepempty) where T<:AbstractString in Base at strings/util.jl:277
```

메서드의 완료는 타입 추론을 사용하므로, 인수가 함수의 출력일지라도 인수가 일치하는지 확인할 수 있습니다. 완료가 일치하지 않는 메서드를 제거할 수 있으려면 함수가 타입 안정성이 있어야 합니다.

특정 인수 유형과 함께 사용할 수 있는 메서드가 궁금하다면, 함수 이름으로 `?`를 사용하세요. 이는 단일 문자열을 수용하는 InteractiveUtils의 함수를 찾는 예시를 보여줍니다:

```julia-repl
julia> InteractiveUtils.?("somefile")[TAB]
edit(path::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:197
less(file::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:266
```

이것은 문자열에서 호출할 수 있는 `InteractiveUtils` 모듈의 나열된 메서드입니다. 기본적으로 모든 인수가 `Any`로 입력된 메서드는 제외되지만, 대신 SHIFT-TAB을 눌러서 그런 메서드도 볼 수 있습니다:

```julia-repl
julia> InteractiveUtils.?("somefile")[SHIFT-TAB]
apropos(string) in REPL at REPL/src/docview.jl:796
clipboard(x) in InteractiveUtils at InteractiveUtils/src/clipboard.jl:64
code_llvm(f) in InteractiveUtils at InteractiveUtils/src/codeview.jl:221
code_native(f) in InteractiveUtils at InteractiveUtils/src/codeview.jl:243
edit(path::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:197
edit(f) in InteractiveUtils at InteractiveUtils/src/editless.jl:225
eval(x) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:3
include(x) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:3
less(file::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:266
less(f) in InteractiveUtils at InteractiveUtils/src/editless.jl:274
report_bug(kind) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:391
separate_kwargs(args...; kwargs...) in InteractiveUtils at InteractiveUtils/src/macros.jl:7
```

`?("somefile")[TAB]`를 사용하여 모든 모듈을 검색할 수도 있지만, 메서드 목록이 길어질 수 있습니다.

닫는 괄호를 생략함으로써 추가 인수가 필요할 수 있는 함수를 포함할 수 있습니다:

```julia-repl
julia> using Mmap

help?> Mmap.?("file",[TAB]
Mmap.Anonymous(name::String, readonly::Bool, create::Bool) in Mmap at Mmap/src/Mmap.jl:16
mmap(file::AbstractString) in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}) where T<:Array in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}) where {T<:Array, N} in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}, offset::Integer; grow, shared) where {T<:Array, N} in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, len::Integer) where T<:Array in Mmap at Mmap/src/Mmap.jl:251
mmap(file::AbstractString, ::Type{T}, len::Integer, offset::Integer; grow, shared) where T<:Array in Mmap at Mmap/src/Mmap.jl:251
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}) where {T<:BitArray, N} in Mmap at Mmap/src/Mmap.jl:316
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}, offset::Integer; grow, shared) where {T<:BitArray, N} in Mmap at Mmap/src/Mmap.jl:316
mmap(file::AbstractString, ::Type{T}, len::Integer) where T<:BitArray in Mmap at Mmap/src/Mmap.jl:322
mmap(file::AbstractString, ::Type{T}, len::Integer, offset::Integer; grow, shared) where T<:BitArray in Mmap at Mmap/src/Mmap.jl:322
```

## Customizing Colors

Julia와 REPL에서 사용하는 색상도 사용자 정의할 수 있습니다. Julia 프롬프트의 색상을 변경하려면 `~/.julia/config/startup.jl` 파일에 다음과 같은 내용을 추가할 수 있습니다. 이 파일은 홈 디렉토리 안에 위치해야 합니다:

```julia
function customize_colors(repl)
    repl.prompt_color = Base.text_colors[:cyan]
end

atreplinit(customize_colors)
```

사용 가능한 색상 키는 REPL의 도움 모드에서 `Base.text_colors`를 입력하여 확인할 수 있습니다. 또한, 0에서 255까지의 정수를 256색 지원 터미널의 색상 키로 사용할 수 있습니다.

도움 및 셸 프롬프트와 입력 및 답변 텍스트의 색상을 변경하려면 위의 `customize_colors` 함수에서 `repl`의 적절한 필드를 설정하면 됩니다(각각 `help_color`, `shell_color`, `input_color`, 및 `answer_color`). 후자의 두 경우에는 `envcolors` 필드도 false로 설정되어 있는지 확인하세요.

`Base.text_colors[:bold]`를 색상으로 사용하여 굵은 글꼴 형식을 적용하는 것도 가능합니다. 예를 들어, 답변을 굵은 글꼴로 인쇄하려면 다음을 `~/.julia/config/startup.jl`에 사용할 수 있습니다:

```julia
function customize_colors(repl)
    repl.envcolors = false
    repl.answer_color = Base.text_colors[:bold]
end

atreplinit(customize_colors)
```

경고 및 정보 메시지를 렌더링하는 데 사용되는 색상을 적절한 환경 변수를 설정하여 사용자 정의할 수도 있습니다. 예를 들어, 오류, 경고 및 정보 메시지를 각각 마젠타, 노란색 및 청록색으로 렌더링하려면 `~/.julia/config/startup.jl` 파일에 다음을 추가할 수 있습니다:

```julia
ENV["JULIA_ERROR_COLOR"] = :magenta
ENV["JULIA_WARN_COLOR"] = :yellow
ENV["JULIA_INFO_COLOR"] = :cyan
```

## Changing the contextual module which is active at the REPL

REPL에서 표현식을 입력할 때, 기본적으로 `Main` 모듈에서 평가됩니다;

```julia-repl
julia> @__MODULE__
Main
```

이 컨텍스트 모듈은 `REPL.activate(m)` 함수를 통해 변경할 수 있으며, 여기서 `m`은 `Module`입니다. 또는 REPL에서 모듈을 입력하고 모듈 이름에 커서를 놓은 상태에서 Alt-m 키 바인딩을 누르면 됩니다 (MacOS에서는 Esc-m). 빈 프롬프트에서 키 바인딩을 누르면 이전에 활성화된 비-`Main` 모듈과 `Main` 간의 컨텍스트가 전환됩니다. 활성 모듈은 프롬프트에 표시됩니다 (단, `Main`은 제외).

```julia-repl
julia> using REPL

julia> REPL.activate(Base)

(Base) julia> @__MODULE__
Base

(Base) julia> using REPL # Need to load REPL into Base module to use it

(Base) julia> REPL.activate(Main)

julia>

julia> Core<Alt-m> # using the keybinding to change module

(Core) julia>

(Core) julia> <Alt-m> # going back to Main via keybinding

julia>

julia> <Alt-m> # going back to previously-active Core via keybinding

(Core) julia>
```

선택적 모듈 인수를 받는 함수는 종종 REPL 컨텍스트 모듈을 기본값으로 사용합니다. 예를 들어, `varinfo()`를 호출하면 현재 활성 모듈의 변수를 보여줍니다:

```julia-repl
julia> module CustomMod
           export var, f
           var = 1
           f(x) = x^2
       end;

julia> REPL.activate(CustomMod)

(Main.CustomMod) julia> varinfo()
  name         size summary
  ––––––––– ––––––– ––––––––––––––––––––––––––––––––––
  CustomMod         Module
  f         0 bytes f (generic function with 1 method)
  var       8 bytes Int64
```

## Numbered prompt

IPython REPL과 Mathematica 노트북과 유사한 인터페이스를 얻는 것이 가능합니다. 입력 프롬프트에 번호가 매겨지고 출력 접두사가 있는 형태입니다. 이는 `REPL.numbered_prompt!()`를 호출하여 수행됩니다. 시작 시 이를 활성화하려면 추가하세요.

```julia
atreplinit() do repl
    @eval import REPL
    if !isdefined(repl, :interface)
        repl.interface = REPL.setup_interface(repl)
    end
    REPL.numbered_prompt!(repl)
end
```

`startup.jl` 파일에 추가하세요. 번호가 매겨진 프롬프트에서 변수 `Out[n]` (여기서 `n`은 정수)는 이전 결과를 참조하는 데 사용할 수 있습니다:

```julia-repl
In [1]: 5 + 3
Out[1]: 8

In [2]: Out[1] + 5
Out[2]: 13

In [3]: Out
Out[3]: Dict{Int64, Any} with 2 entries:
  2 => 13
  1 => 8
```

!!! note
    이전 REPL 평가의 모든 출력이 `Out` 변수에 저장되므로, 배열과 같은 많은 대형 메모리 객체를 반환할 경우 주의해야 합니다. 이러한 객체에 대한 참조가 `Out`에 남아 있는 한 가비지 컬렉션으로부터 보호됩니다. `Out`에서 객체에 대한 참조를 제거해야 하는 경우, `empty!(Out)`을 사용하여 저장된 전체 기록을 지우거나, `Out[n] = nothing`을 사용하여 개별 항목을 지울 수 있습니다.


## TerminalMenus

TerminalMenus는 Julia REPL의 하위 모듈로, 터미널에서 작고 저프로파일의 대화형 메뉴를 가능하게 합니다.

### Examples

```julia
import REPL
using REPL.TerminalMenus

options = ["apple", "orange", "grape", "strawberry",
            "blueberry", "peach", "lemon", "lime"]

```

#### RadioMenu

RadioMenu는 사용자가 목록에서 하나의 옵션을 선택할 수 있도록 합니다. `request` 함수는 대화형 메뉴를 표시하고 선택한 항목의 인덱스를 반환합니다. 사용자가 'q' 또는 `ctrl-c`를 누르면 `request`는 `-1`을 반환합니다.

```julia
# `pagesize` is the number of items to be displayed at a time.
#  The UI will scroll if the number of options is greater
#   than the `pagesize`
menu = RadioMenu(options, pagesize=4)

# `request` displays the menu and returns the index after the
#   user has selected a choice
choice = request("Choose your favorite fruit:", menu)

if choice != -1
    println("Your favorite fruit is ", options[choice], "!")
else
    println("Menu canceled.")
end

```

출력:

```
Choose your favorite fruit:
^  grape
   strawberry
 > blueberry
v  peach
Your favorite fruit is blueberry!
```

#### MultiSelectMenu

MultiSelectMenu는 사용자가 목록에서 여러 선택을 할 수 있도록 합니다.

```julia
# here we use the default `pagesize` 10
menu = MultiSelectMenu(options)

# `request` returns a `Set` of selected indices
# if the menu us canceled (ctrl-c or q), return an empty set
choices = request("Select the fruits you like:", menu)

if length(choices) > 0
    println("You like the following fruits:")
    for i in choices
        println("  - ", options[i])
    end
else
    println("Menu canceled.")
end
```

출력:

```
Select the fruits you like:
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   [ ] apple
 > [X] orange
   [X] grape
   [ ] strawberry
   [ ] blueberry
   [X] peach
   [ ] lemon
   [ ] lime
You like the following fruits:
  - orange
  - grape
  - peach
```

### Customization / Configuration

#### ConfiguredMenu subtypes

Julia 1.6부터 메뉴를 구성하는 권장 방법은 생성자를 통해서입니다. 예를 들어, 기본 다중 선택 메뉴

```
julia> menu = MultiSelectMenu(options, pagesize=5);

julia> request(menu) # ASCII is used by default
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   [ ] apple
   [X] orange
   [ ] grape
 > [X] strawberry
v  [ ] blueberry
```

대신 유니코드 선택 및 탐색 문자로 렌더링될 수 있습니다.

```julia-repl
julia> menu = MultiSelectMenu(options, pagesize=5, charset=:unicode);

julia> request(menu)
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   ⬚ apple
   ✓ orange
   ⬚ grape
 → ✓ strawberry
↓  ⬚ blueberry
```

더 세분화된 구성도 가능합니다:

```julia-repl
julia> menu = MultiSelectMenu(options, pagesize=5, charset=:unicode, checked="YEP!", unchecked="NOPE", cursor='⧐');

julia> request(menu)
julia> request(menu)
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   NOPE apple
   YEP! orange
   NOPE grape
 ⧐ YEP! strawberry
↓  NOPE blueberry
```

전반적인 `charset` 옵션 외에도 `RadioMenu`의 구성 가능한 옵션은 다음과 같습니다:

  * `cursor::Char='>'|'→'`: 커서를 위해 사용할 문자
  * `up_arrow::Char='^'|'↑'`: 위쪽 화살표에 사용할 문자
  * `down_arrow::Char='v'|'↓'`: 아래 화살표에 사용할 문자
  * `updown_arrow::Char='I'|'↕'`: 한 줄 페이지에서 위/아래 화살표로 사용할 문자
  * `scroll_wrap::Bool=false`: 메뉴의 시작/끝에서 선택을 감싸는 옵션입니다.
  * `ctrl_c_interrupt::Bool=true`: `false`인 경우 ^C에서 빈 값을 반환하고, `true`인 경우 ^C에서 InterruptException()을 발생시킵니다.

`MultiSelectMenu` 추가:

  * `checked::String="[X]"|"✓"`: 체크된 항목에 사용할 문자열
  * `unchecked::String="[ ]"|"⬚")`: 선택되지 않은 항목에 사용할 문자열

자신만의 새로운 메뉴 유형을 만들 수 있습니다. `TerminalMenus.ConfiguredMenu`에서 파생된 유형은 생성 시 메뉴 옵션을 구성합니다.

#### Legacy interface

Julia 1.6 이전 및 Julia 1.x 전반에 걸쳐 지원되는 기능으로, `TerminalMenus.config()`를 호출하여 메뉴를 구성할 수도 있습니다.

## References

### REPL

```@docs
Base.atreplinit
```

### TerminalMenus

### Menus

```@docs
REPL.TerminalMenus.RadioMenu
REPL.TerminalMenus.MultiSelectMenu
```

#### Configuration

```@docs
REPL.TerminalMenus.Config
REPL.TerminalMenus.MultiSelectConfig
REPL.TerminalMenus.config
```

#### User interaction

```@docs
REPL.TerminalMenus.request
```

#### AbstractMenu extension interface

`AbstractMenu`의 모든 하위 유형은 변경 가능해야 하며, `pagesize::Int` 및 `pageoffset::Int` 필드를 포함해야 합니다. 모든 하위 유형은 또한 다음 함수를 구현해야 합니다:

```@docs
REPL.TerminalMenus.pick
REPL.TerminalMenus.cancel
REPL.TerminalMenus.writeline
```

`options` 또는 `numoptions` 중 하나를 구현해야 합니다:

```@docs
REPL.TerminalMenus.options
REPL.TerminalMenus.numoptions
```

하위 유형에 `selected`라는 이름의 필드가 없으면, 또한 구현해야 합니다.

```@docs
REPL.TerminalMenus.selected
```

다음은 선택 사항이지만 추가적인 사용자 지정을 허용할 수 있습니다:

```@docs
REPL.TerminalMenus.header
REPL.TerminalMenus.keypress
```
