# [Workflow Tips](@id man-workflow-tips)

여기 줄리아를 효율적으로 작업하는 몇 가지 팁이 있습니다.

## REPL-based workflow

이미 [The Julia REPL](@ref)에서 설명한 바와 같이, Julia의 REPL은 효율적인 인터랙티브 워크플로우를 촉진하는 풍부한 기능을 제공합니다. 다음은 명령줄에서의 경험을 더욱 향상시킬 수 있는 몇 가지 팁입니다.

### A basic editor/REPL workflow

가장 기본적인 Julia 워크플로우는 텍스트 편집기를 `julia` 명령줄과 함께 사용하는 것입니다.

파일을 생성하고, 그 안에 다음 내용을 포함하세요:

```julia
module Tmp

say_hello() = println("Hello!")

# Your other definitions here

end # module

using .Tmp
```

그런 다음, 같은 디렉토리에서 Julia REPL을 시작합니다( `julia` 명령어 사용). 새 파일을 다음과 같이 실행합니다:

```
julia> include("Tmp.jl")

julia> Tmp.say_hello()
Hello!
```

REPL에서 아이디어를 탐색하세요. 좋은 아이디어는 `Tmp.jl`에 저장하세요. 파일이 변경된 후 다시 로드하려면, 다시 `include`하면 됩니다.

위의 핵심은 귀하의 코드가 모듈에 캡슐화되어 있다는 것입니다. 이를 통해 `struct` 정의를 편집하고 메서드를 제거할 수 있으며, Julia를 재시작할 필요가 없습니다.

(설명: `struct`는 정의 후 수정할 수 없으며, 메서드를 삭제할 수도 없습니다. 그러나 모듈의 정의를 덮어쓸 수는 있으며, 이는 `include("Tmp.jl")`를 다시 실행할 때 우리가 하는 일입니다).

또한, 모듈에 코드가 캡슐화되면 REPL의 이전 상태에 의해 영향을 받지 않도록 보호되어, 발견하기 어려운 오류로부터 보호됩니다.

## Browser-based workflow

브라우저에서 Julia와 상호작용하는 몇 가지 방법이 있습니다:

  * [Pluto.jl](https://github.com/fonsp/Pluto.jl)를 통해 Pluto 노트북 사용하기
  * Jupyter 노트북 사용하기 [IJulia.jl](https://github.com/JuliaLang/IJulia.jl)

## Revise-based workflows

REPL이나 IJulia에서 작업할 때, [Revise](https://github.com/timholy/Revise.jl)를 통해 개발 경험을 향상시킬 수 있습니다. 일반적으로 julia가 시작될 때마다 Revise를 시작하도록 구성하는 것이 일반적이며, 이는 [Revise documentation](https://timholy.github.io/Revise.jl/stable/)의 지침에 따릅니다. 구성된 후, Revise는 로드된 모듈의 파일 변경 사항과 `includet`로 REPL에 로드된 파일의 변경 사항을 추적합니다(일반 `include`로는 안 됨); 그런 다음 파일을 편집하면 변경 사항이 julia 세션을 재시작하지 않고도 적용됩니다. 표준 워크플로우는 위의 REPL 기반 워크플로우와 유사하며, 다음과 같은 수정 사항이 있습니다:

1. 코드를 로드 경로의 어딘가에 모듈로 넣으세요. 이를 달성하는 방법에는 여러 가지 옵션이 있으며, 그 중 두 가지 추천 선택지는:

      * 장기 프로젝트의 경우 [PkgTemplates](https://github.com/invenia/PkgTemplates.jl)를 사용하세요:

        ```julia
        using PkgTemplates
        t = Template()
        t("MyPkg")
        ```

        이렇게 하면 `.julia/dev` 디렉토리에 빈 패키지 `"MyPkg"`가 생성됩니다. PkgTemplates는 `Template` 생성자를 통해 다양한 옵션을 제어할 수 있도록 해줍니다.

        2단계에서 `MyPkg/src/MyPkg.jl`의 소스 코드를 변경하고, `MyPkg/test/runtests.jl`에서 테스트를 수정하세요.
      * "버리기" 프로젝트의 경우, 작업을 임시 디렉토리(예: `/tmp`)에서 수행함으로써 정리할 필요를 피할 수 있습니다.

        임시 디렉토리로 이동한 후 Julia를 실행하고 다음을 수행하세요:

        ```julia-repl
        pkg> generate MyPkg            # type ] to enter pkg mode
        julia> push!(LOAD_PATH, pwd())   # hit backspace to exit pkg mode
        ```

        Julia 세션을 재시작하면 `LOAD_PATH`를 수정하는 해당 명령을 다시 실행해야 합니다.

        2단계에서 `MyPkg/src/MyPkg.jl`를 편집하여 소스 코드를 변경하고, 원하는 테스트 파일을 생성하세요.
2. 패키지 개발하기

    *코드* 로드를 하기 전에, Revise가 실행되고 있는지 확인하세요: `using Revise`라고 입력하거나 자동으로 실행되도록 설정하는 방법에 대한 문서를 참조하세요.

    그런 다음 테스트 파일이 포함된 디렉토리로 이동합니다(여기서는 `"runtests.jl"`로 가정됨) 그리고 다음을 수행합니다:

    ```julia-repl
    julia> using MyPkg

    julia> include("runtests.jl")
    ```

    You can iteratively modify the code in MyPkg in your editor and re-run the tests with `include("runtests.jl")`.  You generally should not need to restart your Julia session to see the changes take effect (subject to a few [limitations](https://timholy.github.io/Revise.jl/stable/limitations/)).
