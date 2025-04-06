# Working with LLVM

이것은 LLVM 문서의 대체물이 아니라, Julia를 위한 LLVM 작업에 대한 팁 모음입니다.

## Overview of Julia to LLVM Interface

Julia는 기본적으로 LLVM에 동적으로 링크됩니다. 정적으로 링크하려면 `USE_LLVM_SHLIB=0`으로 빌드하십시오.

Julia AST를 LLVM IR로 낮추거나 직접 해석하는 코드는 `src/` 디렉토리에 있습니다.

| File                             | Description                                                        |
|:-------------------------------- |:------------------------------------------------------------------ |
| `aotcompile.cpp`                 | Compiler C-interface entry and object file emission                |
| `builtins.c`                     | Builtin functions                                                  |
| `ccall.cpp`                      | Lowering [`ccall`](@ref)                                           |
| `cgutils.cpp`                    | Lowering utilities, notably for array and tuple accesses           |
| `codegen.cpp`                    | Top-level of code generation, pass list, lowering builtins         |
| `debuginfo.cpp`                  | Tracks debug information for JIT code                              |
| `disasm.cpp`                     | Handles native object file and JIT code diassembly                 |
| `gf.c`                           | Generic functions                                                  |
| `intrinsics.cpp`                 | Lowering intrinsics                                                |
| `jitlayers.cpp`                  | JIT-specific code, ORC compilation layers/utilities                |
| `llvm-alloc-helpers.cpp`         | Julia-specific escape analysis                                     |
| `llvm-alloc-opt.cpp`             | Custom LLVM pass to demote heap allocations to the stack           |
| `llvm-cpufeatures.cpp`           | Custom LLVM pass to lower CPU-based functions (e.g. haveFMA)       |
| `llvm-demote-float16.cpp`        | Custom LLVM pass to lower 16b float ops to 32b float ops           |
| `llvm-final-gc-lowering.cpp`     | Custom LLVM pass to lower GC calls to their final form             |
| `llvm-gc-invariant-verifier.cpp` | Custom LLVM pass to verify Julia GC invariants                     |
| `llvm-julia-licm.cpp`            | Custom LLVM pass to hoist/sink Julia-specific intrinsics           |
| `llvm-late-gc-lowering.cpp`      | Custom LLVM pass to root GC-tracked values                         |
| `llvm-lower-handlers.cpp`        | Custom LLVM pass to lower try-catch blocks                         |
| `llvm-muladd.cpp`                | Custom LLVM pass for fast-match FMA                                |
| `llvm-multiversioning.cpp`       | Custom LLVM pass to generate sysimg code on multiple architectures |
| `llvm-propagate-addrspaces.cpp`  | Custom LLVM pass to canonicalize addrspaces                        |
| `llvm-ptls.cpp`                  | Custom LLVM pass to lower TLS operations                           |
| `llvm-remove-addrspaces.cpp`     | Custom LLVM pass to remove Julia addrspaces                        |
| `llvm-remove-ni.cpp`             | Custom LLVM pass to remove Julia non-integral addrspaces           |
| `llvm-simdloop.cpp`              | Custom LLVM pass for [`@simd`](@ref)                               |
| `pipeline.cpp`                   | New pass manager pipeline, pass pipeline parsing                   |
| `sys.c`                          | I/O and operating system utility functions                         |

일부 `.cpp` 파일은 단일 객체로 컴파일되는 그룹을 형성합니다.

내재 함수(intrinsic)와 내장 함수(builtin)의 차이는 내장 함수가 다른 줄리아 함수처럼 사용할 수 있는 일급 함수라는 점입니다. 반면, 내재 함수는 언박스된 데이터에서만 작동할 수 있으며, 따라서 그 인자는 정적으로 타입이 지정되어야 합니다.

### [Alias Analysis](@id LLVM-Alias-Analysis)

Julia currently uses LLVM's [Type Based Alias Analysis](https://llvm.org/docs/LangRef.html#tbaa-metadata). To find the comments that document the inclusion relationships, look for `static MDNode*` in `src/codegen.cpp`.

`-O` 옵션은 LLVM의 [Basic Alias Analysis](https://llvm.org/docs/AliasAnalysis.html#the-basic-aa-pass)를 활성화합니다.

## Building Julia with a different version of LLVM

기본 LLVM 버전은 `deps/llvm.version`에 지정되어 있습니다. 이를 재정의하려면 최상위 디렉토리에 `Make.user`라는 파일을 생성하고 다음과 같은 줄을 추가하면 됩니다:

```
LLVM_VER = 13.0.0
```

LLVM 릴리스 번호 외에도 `USE_BINARYBUILDER_LLVM = 0`와 함께 `DEPS_GIT = llvm`을 사용하여 최신 개발 버전의 LLVM에 대해 빌드할 수 있습니다.

LLVM의 디버그 버전을 빌드하도록 지정할 수도 있습니다. `Make.user` 파일에서 `LLVM_DEBUG = 1` 또는 `LLVM_DEBUG = Release` 중 하나를 설정하면 됩니다. 전자는 LLVM의 완전히 비최적화된 빌드가 되고, 후자는 최적화된 LLVM 빌드를 생성합니다. 필요에 따라 후자가 충분하며 훨씬 더 빠릅니다. `LLVM_DEBUG = Release`를 사용하는 경우, 다양한 패스에 대한 진단을 활성화하기 위해 `LLVM_ASSERTIONS = 1`을 설정하는 것도 원할 것입니다. `LLVM_DEBUG = 1`만이 기본적으로 해당 옵션을 의미합니다.

## Passing options to LLVM

LLVM에 옵션을 전달하려면 환경 변수 [`JULIA_LLVM_ARGS`](@ref JULIA_LLVM_ARGS)를 사용할 수 있습니다. 다음은 `bash` 구문을 사용한 예제 설정입니다:

  * `export JULIA_LLVM_ARGS=-print-after-all`는 각 패스 후에 IR을 덤프합니다.
  * `export JULIA_LLVM_ARGS=-debug-only=loop-vectorize`는 루프 벡터화에 대한 LLVM `DEBUG(...)` 진단을 덤프합니다. "알 수 없는 명령줄 인수"에 대한 경고가 발생하면 `LLVM_ASSERTIONS = 1`로 LLVM을 다시 빌드하십시오.
  * `export JULIA_LLVM_ARGS=-help`는 사용 가능한 옵션 목록을 보여줍니다. `export JULIA_LLVM_ARGS=-help-hidden`은 더 많은 옵션을 보여줍니다.
  * `export JULIA_LLVM_ARGS="-fatal-warnings -print-options"`는 여러 옵션을 사용하는 방법의 예입니다.

### Useful `JULIA_LLVM_ARGS` parameters

  * `-print-after=PASS`: `PASS` 실행 후 IR을 출력합니다. 이는 패스에 의해 수행된 변경 사항을 확인하는 데 유용합니다.
  * `-print-before=PASS`: `PASS` 실행 전에 IR을 출력합니다. 이는 패스에 대한 입력을 확인하는 데 유용합니다.
  * `-print-changed`: IR이 변경될 때마다 IR을 출력하며, 문제를 일으키는 패스를 좁히는 데 유용합니다.
  * `-print-(before|after)=MARKER-PASS`: 줄리아 파이프라인은 문제나 최적화가 발생하는 위치를 식별하는 데 사용할 수 있는 여러 마커 패스를 포함하고 있습니다. 마커 패스는 파이프라인에 한 번 나타나고 IR에 대한 변환을 수행하지 않으며, print-before/print-after를 타겟팅하는 데만 유용한 패스로 정의됩니다. 현재 파이프라인에는 다음과 같은 마커 패스가 존재합니다:

      * BeforeOptimization
      * BeforeEarlySimplification
      * AfterEarlySimplification
      * BeforeEarlyOptimization
      * AfterEarlyOptimization
      * BeforeLoopOptimization
      * BeforeLICM
      * AfterLICM
      * BeforeLoopSimplification
      * AfterLoopSimplification
      * AfterLoopOptimization
      * BeforeScalarOptimization
      * AfterScalarOptimization
      * BeforeVectorization
      * AfterVectorization
      * BeforeIntrinsicLowering
      * AfterIntrinsicLowering
      * BeforeCleanup
      * AfterCleanup
      * AfterOptimization
  * `-time-passes`: 각 패스에 소요된 시간을 출력하며, 어떤 패스가 오랜 시간이 걸리는지 식별하는 데 유용합니다.
  * `-print-module-scope`: `-print-(before|after)`와 함께 사용되며, 패스에 의해 수신된 IR 단위가 아닌 전체 모듈을 가져옵니다.
  * `-debug`: LLVM 전반에 걸쳐 많은 디버깅 정보를 출력합니다.
  * `-debug-only=NAME`, `DEBUG_TYPE`가 `NAME`으로 정의된 파일에서 디버깅 문장을 출력하며, 문제에 대한 추가적인 맥락을 얻는 데 유용합니다.

## Debugging LLVM transformations in isolation

때때로 LLVM의 변환을 줄리아 시스템의 나머지 부분과 분리하여 디버깅하는 것이 유용할 수 있습니다. 예를 들어, `julia` 내에서 문제를 재현하는 데 너무 오랜 시간이 걸리거나, LLVM의 도구(예: bugpoint)를 활용하고 싶기 때문입니다.

시작하려면, LLVM과 함께 작업하기 위해 개발자 도구를 설치할 수 있습니다:

```
make -C deps install-llvm-tools
```

전체 시스템 이미지에 대한 최적화되지 않은 IR을 얻으려면 시스템 이미지 빌드 프로세스에 `--output-unopt-bc unopt.bc` 옵션을 전달하면 됩니다. 이 옵션은 최적화되지 않은 IR을 `unopt.bc` 파일로 출력합니다. 이 파일은 일반적으로 LLVM 도구에 전달될 수 있습니다. `libjulia`는 LLVM 패스 플러그인으로 기능할 수 있으며, LLVM 도구에 로드되어 이 환경에서 julia 전용 패스를 사용할 수 있게 합니다. 또한, IR에 대해 전체 Julia 패스 파이프라인을 실행하는 `-julia` 메타 패스를 노출합니다. 예를 들어, 이전 패스 관리자를 사용하여 시스템 이미지를 생성하려면 다음과 같이 할 수 있습니다:

```

llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

새로운 패스 관리자를 사용하여 시스템 이미지를 생성하려면 다음과 같이 할 수 있습니다:

```
opt -load-pass-plugin=libjulia-codegen.so --passes='julia' -o opt.bc unopt.bc
llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

이 시스템 이미지는 이후에 `julia`로 일반적으로 로드될 수 있습니다.

하나의 Julia 함수에 대해 LLVM IR 모듈을 덤프하는 것도 가능합니다. 사용법은 다음과 같습니다:

```julia
fun, T = +, Tuple{Int,Int} # Substitute your function of interest here
optimize = false
open("plus.ll", "w") do file
    println(file, InteractiveUtils._dump_function(fun, T, false, false, false, true, :att, optimize, :default, false))
end
```

이 파일들은 위에 표시된 최적화되지 않은 sysimg IR과 동일한 방식으로 처리될 수 있습니다.

## Running the LLVM test suite

로컬에서 llvm 테스트를 실행하려면 먼저 도구를 설치하고, julia를 빌드한 다음 테스트를 실행할 수 있습니다:

```
make -C deps install-llvm-tools
make -j julia-src-release
make -C test/llvmpasses
```

개별 테스트 파일을 직접 실행하려면 각 테스트 파일 상단의 명령어를 통해, 여기서 첫 번째 단계는 도구를 `./usr/tools/opt`에 설치하는 것입니다. 그런 다음 `%s`를 테스트 파일의 이름으로 수동으로 교체해야 합니다.

## Improving LLVM optimizations for Julia

LLVM 코드 생성을 개선하는 것은 일반적으로 Julia의 하향 변환을 LLVM의 패스에 더 친화적으로 변경하거나 패스를 개선하는 것과 관련이 있습니다.

패스를 개선할 계획이라면 [LLVM developer policy](https://llvm.org/docs/DeveloperPolicy.html)를 반드시 읽어보세요. 가장 좋은 전략은 LLVM의 `opt` 도구를 사용하여 관심 있는 패스와 함께 코드를 격리된 형태로 연구할 수 있는 코드 예제를 만드는 것입니다.

1. Create an example Julia code of interest.
2. `JULIA_LLVM_ARGS=-print-after-all`를 사용하여 IR을 덤프합니다.
3. 관심 있는 패스가 실행되기 직전의 IR을 선택하세요.
4. 디버그 메타데이터를 제거하고 TBAA 메타데이터를 수동으로 수정하십시오.

마지막 단계는 노동 집약적입니다. 더 나은 방법에 대한 제안이 있으면 감사하겠습니다.

## The jlcall calling convention

줄리아는 최적화되지 않은 코드에 대한 일반적인 호출 규칙을 가지고 있으며, 대략 다음과 같은 형태입니다:

```c
jl_value_t *any_unoptimized_call(jl_value_t *, jl_value_t **, int);
```

첫 번째 인자는 박스된 함수 객체이고, 두 번째 인자는 스택에 있는 인수 배열이며, 세 번째는 인수의 수입니다. 이제 우리는 간단한 하향 변환을 수행하고 인수 배열에 대한 alloca를 생성할 수 있습니다. 그러나 이렇게 하면 호출 지점에서의 사용의 SSA 특성이 손상되어 최적화(가비지 수집 루트 배치 포함)가 훨씬 더 어려워집니다. 대신, 우리는 다음과 같이 이를 생성합니다:

```llvm
call %jl_value_t *@julia.call(jl_value_t *(*)(...) @any_unoptimized_call, %jl_value_t *%arg1, %jl_value_t *%arg2)
```

이것은 최적화기 전반에 걸쳐 SSA 특성을 유지할 수 있게 해줍니다. GC 루트 배치는 나중에 이 호출을 원래 C ABI로 낮출 것입니다.

## GC root placement

GC 루트 배치는 LLVM 패스 파이프라인의 후반부에서 수행됩니다. 이렇게 늦게 GC 루트 배치를 수행하면 LLVM이 GC 루트가 필요한 코드 주변에서 더 공격적인 최적화를 수행할 수 있으며, 필요한 GC 루트와 GC 루트 저장 작업의 수를 줄일 수 있습니다(LLVM이 우리의 GC를 이해하지 못하기 때문에 GC 프레임에 저장된 값으로 무엇을 할 수 있고 무엇을 할 수 없는지 알지 못하므로 보수적으로 매우 적은 작업만 수행합니다). 예를 들어, 오류 경로를 고려해 보십시오.

```julia
if some_condition()
    #= Use some variables maybe =#
    error("An error occurred")
end
```

상수 접기 동안, LLVM은 조건이 항상 거짓임을 발견할 수 있으며, 기본 블록을 제거할 수 있습니다. 그러나 GC 루트 하강이 조기에 수행되면, 삭제된 블록에서 사용된 GC 루트 슬롯과 오류 경로에서만 사용되었기 때문에 유지되는 값들이 LLVM에 의해 계속 유지될 수 있습니다. GC 루트 하강을 늦게 수행함으로써, 우리는 LLVM이 어떤 일반적인 최적화(상수 접기, 죽은 코드 제거 등)를 수행할 수 있도록 허용하며, 어떤 값이 GC 추적될 수 있는지에 대해 (너무) 걱정할 필요가 없습니다.

그러나 늦은 GC 루트 배치를 수행할 수 있으려면 a) 어떤 포인터가 GC로 추적되는지와 b) 그러한 포인터의 모든 사용을 식별할 수 있어야 합니다. 따라서 GC 배치 패스의 목표는 간단합니다:

GC 루트/저장소의 수를 최소화하되, 모든 세이프포인트에서 살아있는 GC 추적 포인터(즉, 이 지점 이후에 이 포인터의 사용이 포함된 경로가 있는 포인터)가 어떤 GC 슬롯에 있어야 한다는 제약 조건을 따릅니다.

### Representation

주요 어려움은 프로그램이 최적화기를 통과한 후에도 GC 추적 포인터와 그 사용을 식별할 수 있는 IR 표현을 선택하는 것입니다. 우리의 설계는 이를 달성하기 위해 세 가지 LLVM 기능을 활용합니다:

  * 사용자 정의 주소 공간
  * 오퍼랜드 번들
  * 비정수 포인터

사용자 정의 주소 공간은 최적화를 통해 유지해야 하는 정수로 모든 지점을 태그할 수 있게 해줍니다. 컴파일러는 원래 프로그램에 존재하지 않았던 주소 공간 간에 캐스트를 삽입하지 않아야 하며, 로드/스토어/기타 작업에서 포인터의 주소 공간을 변경해서는 안 됩니다. 이는 최적화 저항 방식으로 어떤 포인터가 GC 추적되는지를 주석 처리할 수 있게 해줍니다. 메타데이터는 동일한 목적을 달성할 수 없다는 점에 유의해야 합니다. 메타데이터는 프로그램의 의미를 변경하지 않고 항상 폐기 가능해야 합니다. 그러나 GC 추적 포인터를 식별하지 못하면 결과 프로그램의 동작이 극적으로 변경됩니다 - 아마도 충돌하거나 잘못된 결과를 반환할 것입니다. 현재 우리는 세 가지 다른 주소 공간을 사용하고 있습니다(그 숫자는 `src/codegen_shared.cpp`에 정의되어 있습니다):

  * GC 추적 포인터(현재 10개): 이는 GC 프레임에 넣을 수 있는 박스된 값에 대한 포인터입니다. C 측의 `jl_value_t*` 포인터와 대략적으로 동등합니다. 주의: 이 주소 공간에 GC 슬롯에 저장될 수 없는 포인터를 두는 것은 불법입니다.
  * 파생 포인터(현재 11개): 이는 GC 추적 포인터에서 파생된 포인터입니다. 이러한 포인터의 사용은 원래 포인터의 사용을 생성합니다. 그러나 이들은 반드시 GC에 의해 알려져 있을 필요는 없습니다. GC 루트 배치 패스는 항상 이 포인터가 파생된 GC 추적 포인터를 찾아야 하며, 이를 루트 포인터로 사용해야 합니다.
  * Callee Rooted Pointers (현재 12개): 이는 피호출자 루트 값을 표현하기 위한 유틸리티 주소 공간입니다. 이 주소 공간의 모든 값은 GC 루트에 저장 가능해야 합니다(향후 이 조건을 완화할 수 있지만), 그러나 다른 포인터와 달리 호출에 전달될 때 루트가 필요하지 않습니다(정의와 호출 사이의 다른 안전 지점을 넘길 경우 여전히 루트가 필요합니다).
  * 추적된 객체에서 로드된 포인터(현재 13개): 이는 배열에서 사용되며, 배열 자체가 관리되는 데이터에 대한 포인터를 포함합니다. 이 데이터 영역은 배열이 소유하지만, 그 자체로는 GC(가비지 컬렉션)에서 추적되는 객체가 아닙니다. 컴파일러는 이 포인터가 살아 있는 한, 이 포인터가 로드된 객체도 계속 살아 있을 것임을 보장합니다.

### Invariants

GC 루트 배치 패스는 여러 불변 조건을 사용하며, 이는 프론트엔드에서 준수해야 하고 최적화 도구에 의해 유지됩니다.

먼저, 다음 주소 공간 캐스트만 허용됩니다:

  * 0->{추적됨, 파생됨, 호출자 루트}: 추적되지 않은 포인터를 다른 포인터로 변환하는 것은 허용됩니다. 그러나 최적화 프로그램은 이러한 값을 루트로 만들지 않을 광범위한 권한을 가지고 있음을 유의해야 합니다. GC 루트가 필요한 값에서 파생된 값이거나 그 값이 주소 공간 0에 있는 것은 프로그램의 어떤 부분에서도 안전하지 않습니다.
  * 추적됨->파생됨: 이것은 내부 값에 대한 표준 감쇠 경로입니다. 배치 패스는 이러한 값을 찾아 사용에 대한 기본 포인터를 식별합니다.
  * Tracked->CalleeRooted: Addrspace CalleeRooted는 GC 루트가 필요하지 않다는 힌트로만 사용됩니다. 그러나 Derived->CalleeRooted의 감소는 금지되어 있으므로, 포인터는 일반적으로 이 주소 공간에서도 GC 슬롯에 저장 가능해야 합니다.

이제 사용을 구성하는 요소에 대해 생각해 봅시다:

  * 로드는 로드된 값이 주소 공간 중 하나에 있는 경우입니다.
  * 주소 공간 중 하나의 값 저장소를 위치에 저장
  * 주소 공간 중 하나에 포인터를 저장합니다.
  * 주소 공간 중 하나의 값이 피연산자인 호출
  * jlcall ABI에서 호출 시 인수 배열에 값이 포함되어 있습니다.
  * Please provide the Markdown content or text you would like me to translate into Korean.

우리는 Tracked/Derived 주소 공간에서 로드/스토어 및 간단한 호출을 명시적으로 허용합니다. jlcall 인수 배열의 요소는 항상 Tracked 주소 공간에 있어야 합니다(이는 유효한 `jl_value_t*` 포인터여야 한다는 ABI에 의해 요구됩니다). 반환 명령어에 대해서도 동일하게 적용됩니다(단, 구조체 반환 인수는 모든 주소 공간을 가질 수 있습니다). CalleeRooted 포인터의 유일한 허용 사용은 적절한 유형의 피연산자를 가진 호출에 전달하는 것입니다.

또한, addrspace Tracked에서 `getelementptr`를 허용하지 않습니다. 이는 해당 작업이 noop이 아닌 경우, 결과 포인터가 GC 슬롯에 유효하게 저장될 수 없으며 따라서 이 주소 공간에 존재하지 않을 수 있기 때문입니다. 이러한 포인터가 필요하다면, 먼저 addrspace Derived로 변환해야 합니다.

마지막으로, 우리는 이러한 주소 공간에서 `inttoptr`/`ptrtoint` 명령어를 허용하지 않습니다. 이러한 명령어가 존재한다는 것은 일부 `i64` 값이 실제로 GC에 의해 추적된다는 것을 의미합니다. 이는 GC 관련 포인터를 식별할 수 있다는 명시된 요구 사항을 깨뜨리기 때문에 문제가 됩니다. 이 불변성은 LLVM 5.0에서 새롭게 도입된 "비정수 포인터" 기능을 사용하여 달성됩니다. 이 기능은 최적화기가 이러한 연산을 도입하는 최적화를 수행하지 못하도록 금지합니다. JIT 시간에 주소 공간 0에서 `inttoptr`를 사용하여 정적 상수를 삽입한 다음, 그 후에 적절한 주소 공간으로 변환하는 것은 여전히 가능합니다.

### Supporting [`ccall`](@ref)

지금까지의 논의에서 빠진 중요한 측면은 [`ccall`](@ref)의 처리입니다. `4d61726b646f776e2e436f64652822222c20226363616c6c2229_40726566`는 사용의 위치와 범위가 일치하지 않는 특이한 특징을 가지고 있습니다. 예를 들어 다음을 고려해 보십시오:

```julia
A = randn(1024)
ccall(:foo, Cvoid, (Ptr{Float64},), A)
```

배열에서 포인터로의 변환이 삽입되어 배열 값에 대한 참조가 제거됩니다. 그러나 우리는 물론 [`ccall`](@ref)를 수행하는 동안 배열이 살아있도록 해야 합니다. 이것이 어떻게 이루어지는지 이해하기 위해, 위 코드를 가정한 대략적인 낮춤 과정을 살펴보겠습니다:

```julia
return $(Expr(:foreigncall, :(:foo), Cvoid, svec(Ptr{Float64}), 0, :(:ccall), Expr(:foreigncall, :(:jl_array_ptr), Ptr{Float64}, svec(Any), 0, :(:ccall), :(A)), :(A)))
```

마지막 `:(A)`는 하향 변환 중에 삽입된 추가 인수 목록으로, 코드 생성기에게 이 [`ccall`](@ref)의 지속 시간 동안 유지해야 할 줄리아 레벨 값을 알려줍니다. 그런 다음 이 정보를 사용하여 IR 수준에서 "오퍼랜드 번들"로 표현합니다. 오퍼랜드 번들은 본질적으로 호출 지점에 첨부된 가짜 사용입니다. IR 수준에서 이것은 다음과 같이 보입니다:

```llvm
call void inttoptr (i64 ... to void (double*)*)(double* %5) [ "jl_roots"(%jl_value_t addrspace(10)* %A) ]
```

GC 루트 배치 패스는 `jl_roots` 오퍼랜드 번들을 일반 오퍼랜드처럼 취급합니다. 그러나 최종 단계로, GC 루트가 삽입된 후에는 오퍼랜드 번들을 제거하여 명령어 선택에 혼란을 주지 않도록 합니다.

### Supporting [`pointer_from_objref`](@ref)

[`pointer_from_objref`](@ref)는 사용자가 GC 루팅을 명시적으로 제어해야 하기 때문에 특별합니다. 위의 불변 조건에 따르면, 이 함수는 10에서 0으로 주소 공간 캐스트를 수행하므로 불법입니다. 그러나 특정 상황에서는 유용할 수 있으므로 특별한 내장 함수를 제공합니다:

```llvm
declared %jl_value_t *julia.pointer_from_objref(%jl_value_t addrspace(10)*)
```

GC 루트 하강 후 해당 주소 공간 캐스트로 낮춰집니다. 그러나 이 내장 함수를 사용함으로써 호출자는 해당 값이 루트화되어 있는지 확인하는 모든 책임을 지게 됩니다. 또한 이 내장 함수는 사용으로 간주되지 않으므로 GC 루트 배치 패스는 함수에 대한 GC 루트를 제공하지 않습니다. 결과적으로 외부 루팅은 값이 여전히 시스템에 의해 추적되는 동안 정리되어야 합니다. 즉, 이 작업의 결과를 사용하여 전역 루트를 설정하려고 시도하는 것은 유효하지 않습니다. 최적화 프로그램이 이미 값을 삭제했을 수 있습니다.

### Keeping values alive in the absence of uses

특정 경우에는 컴파일러에서 보이는 해당 객체의 사용이 없더라도 객체를 살아있게 유지해야 할 필요가 있습니다. 이는 객체의 메모리 표현을 직접 조작하는 저수준 코드나 C 코드와 인터페이스해야 하는 코드의 경우일 수 있습니다. 이를 허용하기 위해, 우리는 LLVM 수준에서 다음과 같은 내장 함수를 제공합니다:

```
token @llvm.julia.gc_preserve_begin(...)
void @llvm.julia.gc_preserve_end(token)
```

(`llvm.`이라는 이름의 일부는 `token` 유형을 사용하기 위해 필요합니다.) 이러한 내장 함수의 의미는 다음과 같습니다: `gc_preserve_begin` 호출에 의해 지배되는 모든 안전 지점에서, 그러나 해당 `gc_preserve_end` 호출에 의해 지배되지 않는 경우(즉, `gc_preserve_begin` 호출에 의해 반환된 토큰이 인수인 호출), 해당 `gc_preserve_begin`에 인수로 전달된 값들은 살아있게 유지됩니다. `gc_preserve_begin`은 여전히 이러한 값들의 일반적인 사용으로 간주되므로, 표준 생애 주기 의미론은 값들이 보존 영역에 들어가기 전에 살아있게 유지되도록 보장합니다.
