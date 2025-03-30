# Fixing precompilation hangs due to open tasks or IO

Julia 1.10 이상에서는 다음 메시지를 볼 수 있습니다:

![사전 컴파일 중단 스크린샷](./img/precompilation_hang.png)

이것은 반복될 수 있습니다. 만약 스스로 해결될 것이라는 힌트 없이 계속 반복된다면, "프리컴파일 정지"가 발생했을 수 있으며, 이를 수정해야 할 필요가 있습니다. 일시적일지라도, 사용자가 이 경고로 인해 불편을 겪지 않도록 해결하는 것이 좋습니다. 이 페이지는 이러한 문제를 분석하고 수정하는 방법을 안내합니다.

조언을 따르고 `Ctrl-C`를 누르면 다음과 같은 내용을 볼 수 있습니다.

```
^C Interrupted: Exiting precompilation...

  1 dependency had warnings during precompilation:
┌ Test1 [ac89d554-e2ba-40bc-bc5c-de68b658c982]
│  [pid 2745] waiting for IO to finish:
│   Handle type        uv_handle_t->data
│   timer              0x55580decd1e0->0x7f94c3a4c340
```

이 메시지는 두 가지 주요 정보를 전달합니다:

  * `Test2`를 로드하려고 할 때 발생하는 `Test1`의 전처리 중에 정지가 발생하고 있습니다 (의존성).
  * `Test1`의 사전 컴파일 중에 Julia는 여전히 열려 있는 `Timer` 객체를 생성했습니다(타이머에 익숙하지 않다면 `?Timer`를 사용하세요); 그 객체가 닫힐 때까지 프로세스는 멈춰 있습니다.

이것이 `timer = Timer(args...)`가 어떻게 생성되는지를 파악하는 데 충분한 힌트라면, `timer`가 결국 스스로 종료된다면 `wait(timer)`를 추가하는 것이 좋고, 강제로 종료해야 한다면 모듈의 최종 `end` 전에 `close(timer)`를 사용하는 것이 좋습니다.

그러나 경우에 따라 그렇게 간단하지 않을 수 있습니다. 일반적으로 가장 좋은 방법은 Test1의 코드로 인한 정지인지 아니면 Test1의 종속성 중 하나로 인한 것인지 확인하는 것부터 시작하는 것입니다:

  * 옵션 1: `Pkg.add("Aqua")`를 사용하고 [`Aqua.test_persistent_tasks`](https://juliatesting.github.io/Aqua.jl/dev/#Aqua.test_persistent_tasks-Tuple{Base.PkgId})를 사용하세요. 이렇게 하면 어떤 패키지가 문제를 일으키는지 식별하는 데 도움이 될 것이며, 그 후에는 [below](@ref pchang_fix) 지침을 따라야 합니다. 필요하다면 `PkgId`를 `Base.PkgId(UUID("..."), "Test1")`로 생성할 수 있으며, 여기서 `...`는 `Test1/Project.toml`의 `uuid` 항목에서 가져옵니다.
  * 옵션 2: 수동으로 멈춤의 원인을 진단합니다.

수동으로 진단하려면:

1. `Pkg.develop("Test1")`
2. Comment out all the code `include`d or defined in `Test1`, *except* the `using/import` statements.
3. `Test2`를 다시 사용해 보세요 (혹은 `Test1`을 사용해도 멈춘다고 가정할 때).

이제 우리는 길의 갈림길에 도달했습니다: 또는

  * 해당 정지가 지속되며, 이는 [due to one of your dependencies](@ref pchang_deps)를 나타냅니다.
  * 행이 사라지며, 이는 [due to something in your code](@ref pchang_fix)을(를) 나타냅니다.

## [Diagnosing and fixing hangs due to a package dependency](@id pchang_deps)

문제가 있는 의존성을 식별하기 위해 이진 검색을 사용하세요: 의존성의 절반을 주석 처리하는 것으로 시작한 다음, 어떤 절반이 문제인지 확인되면 그 절반의 절반을 주석 처리하는 식으로 진행하세요. (프로젝트에서 제거할 필요는 없으며, 단지 `using`/`import` 문을 주석 처리하면 됩니다.)

문제를 일으키고 있다고 생각되는 패키지(`ThePackageYouThinkIsCausingTheProblem`)를 식별한 후, 먼저 해당 패키지를 미리 컴파일해 보십시오. 미리 컴파일하는 동안에도 멈춘다면, 문제를 거슬러 올라가며 계속 추적하십시오.

그러나, 대부분의 경우 `ThePackageYouThinkIsCausingTheProblem`은 정상적으로 사전 컴파일될 것입니다. 이는 `ThePackageYouThinkIsCausingTheProblem.__init__` 함수에 문제가 있음을 시사하며, 이 함수는 `ThePackageYouThinkIsCausingTheProblem`의 사전 컴파일 중에는 실행되지 않지만 `ThePackageYouThinkIsCausingTheProblem`을 로드하는 모든 패키지에서는 *실행됩니다*. 이 이론을 테스트하기 위해 최소한의 작동 예제(MWE)를 설정하세요, 예를 들어 다음과 같은 것을 만들어 보세요.

```julia
(@v1.10) pkg> generate MWE
  Generating  project MWE:
    MWE\Project.toml
    MWE\src\MWE.jl
```

`MWE.jl`의 소스 코드는 어디에 있나요?

```julia
module MWE
using ThePackageYouThinkIsCausingTheProblem
end
```

그리고 `ThePackageYouThinkIsCausingTheProblem`을 MWE의 종속성에 추가했습니다.

해당 MWE가 멈춤 현상을 재현한다면, 당신은 원인을 찾은 것입니다: `ThePackageYouThinkIsCausingTheProblem.__init__`가 `Timer` 객체를 생성하고 있어야 합니다. 타이머 객체를 안전하게 `close`할 수 있다면, 그것이 좋은 선택입니다. 그렇지 않다면, 가장 일반적인 해결책은 *어떤* 패키지가 미리 컴파일되는 동안 타이머를 생성하지 않는 것입니다: 추가하세요.

```julia
ccall(:jl_generating_output, Cint, ()) == 1 && return nothing
```

`ThePackageYouThinkIsCausingTheProblem.__init__`의 첫 번째 줄로, 패키지를 미리 컴파일하는 목적의 어떤 줄리아 프로세스에서도 초기화를 수행하지 않도록 할 것입니다.

## [Fixing package code to avoid hangs](@id pchang_fix)

패키지에서 "Timer"와 같은 암시적인 단어를 검색하고 문제가 발생하는 위치를 확인해 보세요. 메서드 *정의*와 같은 사항에 유의하세요.

```julia
maketimer() = Timer(timer -> println("hi"), 0; interval=1)
```

문제 자체는 아니지만, `maketimer`가 모듈이 정의되는 동안 호출될 경우에만 이 문제가 발생할 수 있습니다. 이는 다음과 같은 최상위 문장에서 발생할 수 있습니다.

```julia
const GLOBAL_TIMER = maketimer()
```

또는 [precompile workload](https://github.com/JuliaLang/PrecompileTools.jl)에서 발생할 수 있습니다.

문제의 원인을 파악하는 데 어려움이 있다면 이진 검색을 고려해 보세요: 패키지의 섹션을 주석 처리하거나 전체 파일을 생략하기 위해 `include` 라인을 추가하여 문제의 범위를 줄일 때까지 진행하세요.
