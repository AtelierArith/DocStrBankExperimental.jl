```@eval
io = IOBuffer()
release = isempty(VERSION.prerelease)
v = "$(VERSION.major).$(VERSION.minor)"
!release && (v = v*"-$(first(VERSION.prerelease))")
print(io, """
    # Julia $(v) Documentation

    Welcome to the documentation for Julia $(v).

    """)
if !release
    print(io,"""
        !!! warning "Work in progress!"
            This documentation is for an unreleased, in-development, version of Julia.
        """)
end
import Markdown
Markdown.parse(String(take!(io)))
```

[release notes](NEWS.md)를 읽어보시고 마지막 릴리스 이후 어떤 변화가 있었는지 확인해 주세요.

```@eval
release = isempty(VERSION.prerelease)
file = release ? "julia-$(VERSION).pdf" :
       "julia-$(VERSION.major).$(VERSION.minor).$(VERSION.patch)-$(first(VERSION.prerelease)).pdf"
url = "https://raw.githubusercontent.com/JuliaLang/docs.julialang.org/assets/$(file)"
import Markdown
Markdown.parse("""
!!! note
    The documentation is also available in PDF format: [$file]($url).
""")
```

## [Important Links](@id man-important-links)

다음은 Julia 프로그래밍 언어를 배우고 사용할 때 유용한 링크의 비포괄적인 목록입니다.

  * [Julia Homepage](https://julialang.org)
  * [Download Julia](https://julialang.org/downloads/)
  * [Discussion forum](https://discourse.julialang.org)
  * [Julia YouTube](https://www.youtube.com/user/JuliaLanguage)
  * [Find Julia Packages](https://julialang.org/packages/)
  * [Learning Resources](https://julialang.org/learning/)
  * [Read and write blogs on Julia](https://forem.julialang.org)

## [Introduction](@id man-introduction)

과학적 컴퓨팅은 전통적으로 최고의 성능을 요구했지만, 도메인 전문가들은 일상 작업을 위해 느린 동적 언어로 대부분 이동했습니다. 우리는 이러한 애플리케이션에 동적 언어를 선호해야 할 많은 좋은 이유가 있다고 믿으며, 그 사용이 줄어들 것이라고 예상하지 않습니다. 다행히도 현대 언어 설계 및 컴파일러 기술 덕분에 성능 저하를 대부분 제거하고 프로토타이핑에 충분히 생산적이며 성능 집약적인 애플리케이션을 배포하는 데 충분히 효율적인 단일 환경을 제공할 수 있게 되었습니다. Julia 프로그래밍 언어는 이러한 역할을 수행합니다: 과학적 및 수치적 컴퓨팅에 적합한 유연한 동적 언어로, 전통적인 정적 타입 언어와 유사한 성능을 제공합니다.

Julia의 컴파일러는 Python이나 R과 같은 언어에 사용되는 인터프리터와 다르기 때문에, 처음에는 Julia의 성능이 직관적이지 않을 수 있습니다. 만약 어떤 것이 느리다고 느껴진다면, 다른 것을 시도하기 전에 [Performance Tips](@ref man-performance-tips) 섹션을 읽어보는 것을 강력히 추천합니다. Julia가 어떻게 작동하는지 이해하면, C만큼 빠른 코드를 쉽게 작성할 수 있습니다.

## [Julia Compared to Other Languages](@id man-julia-compared-other-languages)

Julia features optional typing, multiple dispatch, and good performance, achieved using type inference and [just-in-time (JIT) compilation](https://en.wikipedia.org/wiki/Just-in-time_compilation) (and [optional ahead-of-time compilation](https://github.com/JuliaLang/PackageCompiler.jl)), implemented using [LLVM](https://en.wikipedia.org/wiki/Low_Level_Virtual_Machine). It is multi-paradigm, combining features of imperative, functional, and object-oriented programming. Julia provides ease and expressiveness for high-level numerical computing, in the same way as languages such as R, MATLAB, and Python, but also supports general programming. To achieve this, Julia builds upon the lineage of mathematical programming languages, but also borrows much from popular dynamic languages, including [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language)), [Perl](https://en.wikipedia.org/wiki/Perl_(programming_language)), [Python](https://en.wikipedia.org/wiki/Python_(programming_language)), [Lua](https://en.wikipedia.org/wiki/Lua_(programming_language)), and [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language)).

Julia의 전형적인 동적 언어와의 가장 중요한 차이점은 다음과 같습니다:

  * 핵심 언어는 매우 적은 제약을 가합니다. Julia Base와 표준 라이브러리는 Julia 자체로 작성되었으며, 정수 산술과 같은 기본 연산을 포함합니다.
  * 객체를 구성하고 설명하기 위한 풍부한 유형 언어로, 선택적으로 유형 선언을 만드는 데에도 사용할 수 있습니다.
  * 함수 동작을 다양한 인수 유형 조합에 따라 정의할 수 있는 능력 [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch)
  * 다양한 인수 유형에 대한 효율적이고 전문화된 코드의 자동 생성
  * 좋은 성능, C와 같은 정적으로 컴파일된 언어의 성능에 접근하고 있습니다.

비록 때때로 동적 언어를 "타입이 없는" 언어라고 말하지만, 그들은 분명히 그렇지 않습니다. 모든 객체는 원시 객체이든 사용자 정의 객체이든 타입을 가지고 있습니다. 그러나 대부분의 동적 언어에서 타입 선언이 없기 때문에, 컴파일러에게 값의 타입에 대해 지시할 수 없으며, 종종 타입에 대해 명시적으로 이야기할 수 없습니다. 반면 정적 언어에서는 컴파일러를 위해 타입을 주석 처리할 수 있으며(보통 그렇게 해야 하기도 합니다), 타입은 컴파일 시간에만 존재하고 런타임에 조작하거나 표현할 수 없습니다. Julia에서는 타입이 자체적으로 런타임 객체이며, 컴파일러에게 정보를 전달하는 데에도 사용될 수 있습니다.

### [What Makes Julia, Julia?](@id man-what-makes-julia)

일반 프로그래머는 타입이나 다중 디스패치를 명시적으로 사용할 필요가 없지만, 이들은 줄리아의 핵심 통합 기능입니다: 함수는 다양한 인자 타입 조합에 대해 정의되며, 가장 구체적인 일치 정의로 디스패치하여 적용됩니다. 이 모델은 수학적 프로그래밍에 잘 맞으며, 전통적인 객체 지향 디스패치에서 첫 번째 인자가 연산을 "소유"하는 것이 부자연스럽습니다. 연산자는 특별한 표기법을 가진 함수일 뿐입니다 – 새로운 사용자 정의 데이터 타입에 덧셈을 확장하려면 `+` 함수에 대한 새로운 메서드를 정의하면 됩니다. 기존 코드는 그러면 새로운 데이터 타입에 원활하게 적용됩니다.

부분적으로는 런타임 타입 추론(선택적 타입 주석으로 보강됨) 때문이고, 부분적으로는 프로젝트 시작부터 성능에 대한 강한 집중 때문인 줄리아의 계산 효율성은 다른 동적 언어를 초월하며, 정적 컴파일 언어와도 경쟁할 수 있습니다. 대규모 수치 문제의 경우, 속도는 항상 중요했으며, 계속해서 중요할 것이고 아마도 항상 중요할 것입니다: 처리되는 데이터의 양은 지난 수십 년 동안 무어의 법칙을 쉽게 따라왔습니다.

### [Advantages of Julia](@id man-advantages-of-julia)

줄리아는 단일 언어에서 사용의 용이성, 강력함 및 효율성의 전례 없는 조합을 만들고자 합니다. 위의 내용 외에도 줄리아가 유사한 시스템에 비해 갖는 몇 가지 장점은 다음과 같습니다:

  * 무료 및 오픈 소스 ([MIT licensed](https://github.com/JuliaLang/julia/blob/master/LICENSE.md))
  * 사용자 정의 유형은 내장형만큼 빠르고 컴팩트합니다.
  * 성능을 위해 코드를 벡터화할 필요가 없습니다; 비벡터화된 코드는 빠릅니다.
  * 병렬 처리 및 분산 계산을 위해 설계됨
  * 경량 "그린" 스레딩 ([coroutines](https://en.wikipedia.org/wiki/Coroutine))
  * 눈에 띄지 않지만 강력한 타입 시스템
  * 우아하고 확장 가능한 숫자 및 기타 유형에 대한 변환 및 프로모션
  * 효율적인 지원을 위한 [Unicode](https://en.wikipedia.org/wiki/Unicode), 포함하되 이에 국한되지 않는 [UTF-8](https://en.wikipedia.org/wiki/UTF-8)
  * C 함수를 직접 호출하기 (래퍼나 특별한 API 필요 없음)
  * 다른 프로세스를 관리하기 위한 강력한 셸과 같은 기능
  * Lisp와 유사한 매크로 및 기타 메타프로그래밍 기능
