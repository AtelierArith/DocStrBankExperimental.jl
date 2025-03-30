# Eval of Julia code

Julia 언어가 코드를 실행하는 방식에 대해 배우는 가장 어려운 부분 중 하나는 코드 블록을 실행하기 위해 모든 구성 요소가 어떻게 함께 작동하는지를 배우는 것입니다.

각 코드 조각은 일반적으로 다음과 같은 생소한 이름을 가진 여러 단계를 거칩니다(특정 순서 없음): flisp, AST, C++, LLVM, `eval`, `typeinf`, `macroexpand`, sysimg(또는 시스템 이미지), 부트스트래핑, 컴파일, 파싱, 실행, JIT, 해석, 박스, 언박스, 내재 함수, 원시 함수 등. 그 후 원하는 결과(바라건대)로 변환됩니다.

!!! sidebar "Definitions"
      * REPL

        REPL은 Read-Eval-Print Loop의 약자입니다. 이것은 우리가 명령줄 환경을 간단히 부르는 방법입니다.
      * AST

        추상 구문 트리   AST는 코드 구조의 디지털 표현입니다. 이 형태에서 코드는 의미에 따라 토큰화되어 조작 및 실행에 더 적합합니다.


![컴파일러 흐름 다이어그램](./img/compiler_diagram.png)

## Julia Execution

전체 프로세스에 대한 10,000피트 뷰는 다음과 같습니다:

1. 사용자가 `julia`를 시작합니다.
2. `cli/loader_exe.c`의 C 함수 `main()`이 호출됩니다. 이 함수는 명령줄 인수를 처리하여 `jl_options` 구조체를 채우고 변수 `ARGS`를 설정합니다. 그런 다음 Julia를 초기화합니다(예: [`julia_init` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c) 호출). 이는 이전에 컴파일된 [sysimg](@ref dev-sysimg)를 로드할 수 있습니다. 마지막으로, [`Base._start()`](https://github.com/JuliaLang/julia/blob/master/base/client.jl)를 호출하여 Julia에 제어를 넘깁니다.
3. `_start()`가 제어를 인수받으면, 이후의 명령어 시퀀스는 주어진 명령줄 인수에 따라 달라집니다. 예를 들어, 파일 이름이 제공되면 해당 파일을 실행하게 됩니다. 그렇지 않으면 대화형 REPL을 시작합니다.
4. 사용자와 REPL 간의 상호작용에 대한 세부 사항은 생략하고, 프로그램이 실행하고자 하는 코드 블록을 갖게 된다고만 말하겠습니다.
5. 코드를 실행할 블록이 파일에 있는 경우, [`jl_load(char *filename)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)가 호출되어 파일을 로드하고 [parse](@ref dev-parsing)가 이를 처리합니다. 각 코드 조각은 `eval`에 전달되어 실행됩니다.
6. 각 코드 조각(또는 AST)은 [`eval()`](@ref)에 전달되어 결과로 변환됩니다.
7. [`eval()`](@ref)는 각 코드 조각을 가져와서 [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)에서 실행하려고 시도합니다.
8. `jl_toplevel_eval_flex()`는 코드가 함수 내에서 유효하지 않은 "최상위" 작업(예: `using` 또는 `module`)인지 여부를 결정합니다. 그렇다면 코드를 최상위 인터프리터에 전달합니다.
9. `jl_toplevel_eval_flex()` 다음에 [expands](@ref dev-macro-expansion) 코드는 모든 매크로를 제거하고 AST를 "하향" 조정하여 실행하기 쉽게 만드는 코드입니다.
10. `jl_toplevel_eval_flex()`는 간단한 휴리스틱을 사용하여 AST를 JIT 컴파일할지 아니면 직접 해석할지를 결정합니다.
11. 코드를 해석하는 작업의 대부분은 [`eval` in `interpreter.c`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c)에 의해 처리됩니다.
12. 코드가 컴파일되는 대신, 대부분의 작업은 `codegen.cpp`에 의해 처리됩니다. 주어진 인수 유형 집합으로 Julia 함수가 처음 호출될 때, [type inference](@ref dev-type-inference)가 해당 함수에서 실행됩니다. 이 정보는 [codegen](@ref dev-codegen) 단계에서 더 빠른 코드를 생성하는 데 사용됩니다.
13. 결국 사용자가 REPL을 종료하거나 프로그램의 끝에 도달하면 `_start()` 메서드가 반환됩니다.
14. 종료 직전에, `main()`은 [`jl_atexit_hook(exit_code)`](https://github.com/JuliaLang/julia/blob/master/src/init.c)를 호출합니다. 이는 Julia 내에서 [`atexit()`](@ref)에 등록된 모든 함수를 호출하는 `Base._atexit()`를 호출합니다. 그런 다음 [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c)를 호출합니다. 마지막으로, 모든 `libuv` 핸들을 우아하게 정리하고 이들이 플러시되고 닫힐 때까지 기다립니다.

## [Parsing](@id dev-parsing)

줄리아 파서는 펨토리습(femtolisp)으로 작성된 작은 리습 프로그램으로, 그 소스 코드는 줄리아 내부의 [src/flisp](https://github.com/JuliaLang/julia/tree/master/src/flisp)에 배포됩니다.

이 인터페이스 기능은 주로 [`jlfrontend.scm`](https://github.com/JuliaLang/julia/blob/master/src/jlfrontend.scm)에 정의되어 있습니다. [`ast.c`](https://github.com/JuliaLang/julia/blob/master/src/ast.c)의 코드는 Julia 측에서 이 핸드오프를 처리합니다.

이 단계에서 다른 관련 파일은 [`julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm)로, 이는 줄리아 코드를 토큰화하고 이를 AST로 변환하는 역할을 하며, [`julia-syntax.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-syntax.scm)로, 이는 복잡한 AST 표현을 더 간단한 "하향된" AST 표현으로 변환하는 역할을 하여 분석 및 실행에 더 적합합니다.

전체적으로 Julia를 다시 빌드하지 않고 파서를 테스트하려면, 다음과 같이 프론트엔드를 독립적으로 실행할 수 있습니다:

```
$ cd src
$ flisp/flisp
> (load "jlfrontend.scm")
> (jl-parse-file "<filename>")
```

## [Macro Expansion](@id dev-macro-expansion)

[`eval()`](@ref)가 매크로를 만날 때, 해당 AST 노드를 확장한 후 표현식을 평가하려고 시도합니다. 매크로 확장은 `4d61726b646f776e2e436f64652822222c20226576616c28292229_40726566` (줄리아에서)에서 파서 함수 `jl_macroexpand()` (flisp로 작성됨)로, 그리고 줄리아 매크로 자체 (다른 무엇보다도 줄리아로 작성됨)로 `fl_invoke_julia_macro()`를 통해 전달된 후 다시 돌아오는 과정을 포함합니다.

일반적으로 매크로 확장은 [`Meta.lower()`](@ref)/`jl_expand()`에 대한 호출의 첫 번째 단계로 호출되지만, [`macroexpand()`](@ref)/`jl_macroexpand()`에 대한 호출을 통해 직접 호출될 수도 있습니다.

## [Type Inference](@id dev-type-inference)

타입 추론은 [`typeinf()` in `compiler/typeinfer.jl`](https://github.com/JuliaLang/julia/blob/master/base/compiler/typeinfer.jl)에 의해 구현됩니다. 타입 추론은 Julia 함수의 변수를 검사하고 각 변수의 타입에 대한 경계와 함수의 반환 값의 타입에 대한 경계를 결정하는 과정입니다. 이는 알려진 불변 값의 언박싱 및 필드 오프셋 및 함수 포인터와 같은 다양한 런타임 작업의 컴파일 타임 호이스팅과 같은 많은 미래 최적화를 가능하게 합니다. 타입 추론은 상수 전파 및 인라인과 같은 다른 단계를 포함할 수도 있습니다.

!!! sidebar "More Definitions"
      * JIT

        Just-In-Time 컴파일 네이티브 머신 코드를 필요할 때 메모리에 생성하는 과정입니다.
      * LLVM

        저수준 가상 머신(컴파일러) Julia JIT 컴파일러는 libLLVM이라는 프로그램/라이브러리입니다. Julia에서의 코드 생성은 Julia AST를 가져와 LLVM 명령어로 변환하는 과정과 LLVM이 이를 최적화하여 네이티브 어셈블리 명령어로 변환하는 과정을 모두 포함합니다.
      * C++

        LLVM이 구현된 프로그래밍 언어, 즉 코드 생성도 이 언어로 구현되어 있다는 의미입니다. Julia의 나머지 라이브러리는 C로 구현되어 있는데, 이는 기능 세트가 더 작아 교차 언어 인터페이스 레이어로서 더 사용하기 쉽기 때문입니다.
      * 상자

        이 용어는 값을 가져와서 데이터 주위에 래퍼를 할당하는 과정을 설명하는 데 사용되며, 이 데이터는 가비지 컬렉터(gc)에 의해 추적되고 객체의 유형으로 태그가 붙습니다.
      * 언박스

        값을 박스하는 것의 반대. 이 작업은 데이터의 유형이 컴파일 타임에 완전히 알려져 있을 때(유형 추론을 통해) 데이터의 보다 효율적인 조작을 가능하게 합니다.
      * 제네릭 함수

        여러 "메서드"로 구성된 Julia 함수는 인수의 타입 시그니처에 따라 동적 디스패치를 기반으로 선택됩니다.
      * 익명 함수 또는 "메서드"

        이름이 없고 타입 분기 기능이 없는 Julia 함수
      * 원시 함수

        C로 구현된 함수가 이름이 "method"인 함수로 Julia에 노출되지만, 일반 함수 분기 기능은 없고 익명 함수와 유사합니다.
      * 내재 함수

        저수준 작업이 Julia에서 함수로 노출됩니다. 이러한 의사 함수는 다른 방법으로 직접 표현할 수 없는 원시 비트에 대한 덧셈 및 부호 확장과 같은 작업을 구현합니다. 비트에 직접 작동하므로 함수로 컴파일되어야 하며, 값에 대한 유형 정보를 재할당하기 위해 `Core.Intrinsics.box(T, ...)` 호출로 둘러싸여야 합니다.


## [JIT Code Generation](@id dev-codegen)

Codegen은 Julia AST를 네이티브 머신 코드로 변환하는 과정입니다.

JIT 환경은 [`jl_init_codegen` in `codegen.cpp`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp)에 대한 초기 호출로 초기화됩니다.

요청에 따라, Julia 메서드는 `emit_function(jl_method_instance_t*)` 함수에 의해 네이티브 함수로 변환됩니다. (참고로, MCJIT(LLVM v3.4+)를 사용할 때, 각 함수는 새로운 모듈로 JIT되어야 합니다.) 이 함수는 전체 함수가 출력될 때까지 재귀적으로 `emit_expr()`를 호출합니다.

이 파일의 나머지 대부분은 특정 코드 패턴에 대한 다양한 수동 최적화에 할애되어 있습니다. 예를 들어, `emit_known_call()`은 여러 인수 유형 조합에 대해 많은 기본 함수(정의된 [`builtins.c`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c))를 인라인하는 방법을 알고 있습니다.

코드 생성의 다른 부분은 다양한 헬퍼 파일에 의해 처리됩니다:

  * [`debuginfo.cpp`](https://github.com/JuliaLang/julia/blob/master/src/debuginfo.cpp)

    JIT 함수에 대한 백트레이스를 처리합니다.
  * [`ccall.cpp`](https://github.com/JuliaLang/julia/blob/master/src/ccall.cpp)

    `abi_*.cpp` 파일과 함께 ccall 및 llvmcall FFI를 처리합니다.
  * [`intrinsics.cpp`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp)

    다양한 저수준 내장 함수의 생성을 처리합니다.

!!! sidebar "Bootstrapping"
    새 시스템 이미지를 생성하는 과정을 "부트스트래핑"이라고 합니다.

    이 단어의 어원은 "부츠 스트랩으로 자신을 끌어올리다"라는 구절에서 유래되었으며, 매우 제한된 기능과 정의의 집합에서 시작하여 완전한 기능을 갖춘 환경을 만드는 아이디어를 나타냅니다.


## [System Image](@id dev-sysimg)

시스템 이미지는 일련의 Julia 파일의 미리 컴파일된 아카이브입니다. Julia와 함께 배포되는 `sys.ji` 파일은 이러한 시스템 이미지 중 하나로, 파일 [`sysimg.jl`](https://github.com/JuliaLang/julia/blob/master/base/sysimg.jl)를 실행하여 생성되고, 결과 환경(타입, 함수, 모듈 및 정의된 모든 값 포함)을 파일로 직렬화합니다. 따라서 `Main`, `Core`, `Base` 모듈의 고정된 버전(부트스트랩이 끝날 때 환경에 있던 다른 모든 것 포함)을 포함하고 있습니다. 이 직렬 변환기/역직렬 변환기는 [`jl_save_system_image`/`jl_restore_system_image` in `staticdata.c`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c)에 의해 구현됩니다.

만약 sysimg 파일이 없다면(`jl_options.image_file == NULL`), 이는 또한 명령줄에서 `--build`가 주어졌음을 의미하므로 최종 결과는 새로운 sysimg 파일이어야 합니다. Julia 초기화 중에 최소한의 `Core` 및 `Main` 모듈이 생성됩니다. 그런 다음 현재 디렉토리에서 `boot.jl`이라는 파일이 평가됩니다. Julia는 명령줄 인수로 주어진 파일을 평가하다가 끝에 도달할 때까지 계속합니다. 마지막으로, 결과 환경을 "sysimg" 파일에 저장하여 향후 Julia 실행의 시작점으로 사용합니다.
