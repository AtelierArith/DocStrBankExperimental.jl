# Custom LLVM Passes

줄리아는 여러 개의 사용자 정의 LLVM 패스를 가지고 있습니다. 대체로, 이들은 줄리아의 의미를 유지하기 위해 실행해야 하는 패스와 줄리아의 의미를 활용하여 LLVM IR을 최적화하는 패스로 분류될 수 있습니다.

## Semantic Passes

이 패스는 LLVM IR을 CPU에서 실행할 수 있는 코드로 변환하는 데 사용됩니다. 이들의 주요 목적은 코드 생성에 의해 더 간단한 IR이 생성되도록 하여, 이후 다른 LLVM 패스가 일반적인 패턴을 최적화할 수 있도록 하는 것입니다.

### CPUFeatures

  * 파일 이름: `llvm-cpufeatures.cpp`
  * 클래스 이름: `CPUFeaturesPass`
  * 옵션 이름: `module(CPUFeatures)`

이 패스는 `julia.cpu.have_fma.(f32|f64)` 내재 함수를 대상 아키텍처와 함수에 존재하는 대상 기능에 따라 true 또는 false로 낮춥니다. 이 내재 함수는 종종 빠른 [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add) 연산에 의존하는 알고리즘을 사용하는 것이 그러한 명령어에 의존하지 않는 표준 알고리즘을 사용하는 것보다 더 나은지 결정하는 데 사용됩니다.

### DemoteFloat16

  * 파일 이름: `llvm-demote-float16.cpp`
  * 클래스 이름: `DemoteFloat16Pass`
  * 옵션 이름 `function(DemoteFloat16)`

이 패스는 [float16](https://en.wikipedia.org/wiki/Half-precision_floating-point_format) 연산을 float32 연산으로 대체합니다. 이는 float16 연산을 본래 지원하지 않는 아키텍처에서 `fpext` 및 `fptrunc` 명령어를 float16 연산 주위에 삽입하여 수행됩니다. 본래 float16 연산을 지원하는 아키텍처에서는 이 패스가 아무 작업도 수행하지 않습니다.

### LateGCLowering

  * 파일 이름: `llvm-late-gc-lowering.cpp`
  * 클래스 이름: `LateLowerGCPass`
  * 옵션 이름: `function(LateLowerGCFrame)`

이 패스는 GC 안전 지점 간의 포인터를 추적하는 데 필요한 대부분의 GC 루팅 작업을 수행합니다. 또한 여러 내재 함수를 해당하는 명령어 변환으로 낮추며, 이전에 설정된 비정수 불변을 위반하는 것이 허용됩니다(`pointer_from_objref`는 여기서 `ptrtoint` 명령어로 낮춰집니다). 이 패스는 일반적으로 모든 사용자 정의 Julia 패스 중에서 가장 많은 시간을 차지하며, 이는 안전 지점에서 살아 있는 객체 수를 최소화하기 위한 데이터 흐름 알고리즘 때문입니다.

### FinalGCLowering

  * 파일 이름: `llvm-final-gc-lowering.cpp`
  * 클래스 이름: `FinalLowerGCPass`
  * 옵션 이름: `module(FinalLowerGC)`

이 패스는 `libjulia` 라이브러리의 함수에 대한 최종 형태로 몇 가지 마지막 내재 함수를 낮춥니다. 이를 `LateGCLowering`과 분리함으로써 다른 백엔드(GPU 컴파일)가 이러한 내재 함수에 대한 사용자 정의 낮춤을 제공할 수 있게 하여, Julia 파이프라인이 해당 백엔드에서도 사용될 수 있도록 합니다.

### LowerHandlers

  * 파일 이름: `llvm-lower-handlers.cpp`
  * 클래스 이름: `LowerExcHandlersPass`
  * 옵션 이름: `function(LowerExcHandlers)`

이 패스는 예외 처리를 위한 내장 함수를 실제로 예외를 처리할 때 호출되는 런타임 함수 호출로 낮춥니다.

### RemoveNI

  * 파일 이름: `llvm-remove-ni.cpp`
  * 클래스 이름: `RemoveNIPass`
  * 옵션 이름: `module(RemoveNI)`

이 패스는 모듈의 데이터 레이아웃 문자열에서 비정수 주소 공간을 제거합니다. 이를 통해 백엔드는 모든 포인터 작업을 주소 공간 0으로 다시 작성하는 비용이 많이 드는 작업 없이 줄리아의 사용자 정의 주소 공간을 기계 코드로 직접 낮출 수 있습니다.

### SIMDLoop

  * 파일 이름: `llvm-simdloop.cpp`
  * 클래스 이름: `LowerSIMDLoopPass`
  * 옵션 이름: `loop(LowerSIMDLoop)`

이 패스는 `@simd` 주석의 주요 드라이버 역할을 합니다. 코드 생성은 루프의 백 브랜치에 `!llvm.loopid` 마커를 삽입하며, 이 패스는 이를 사용하여 원래 `@simd`로 표시된 루프를 식별합니다. 그런 다음 이 패스는 축소를 형성하는 부동 소수점 연산의 체인을 찾아 `contract` 및 `reassoc` 빠른 수학 플래그를 추가하여 재연관(따라서 벡터화)을 허용합니다. 이 패스는 루프 정보나 추론 정확성을 보존하지 않으므로, 예기치 않은 방식으로 Julia 의미론을 위반할 수 있습니다. 루프가 `ivdep`로 주석이 달린 경우, 이 패스는 루프에 루프 전파 종속성이 없다고 표시합니다(사용자 주석이 잘못되었거나 잘못된 루프에 적용된 경우 결과 동작은 정의되지 않습니다).

### LowerPTLS

  * 파일 이름: `llvm-ptls.cpp`
  * 클래스 이름: `LowerPTLSPass`
  * 옵션 이름: `module(LowerPTLSPass)`

이 패스는 스레드 로컬 Julia 내장 함수를 어셈블리 명령어로 낮춥니다. Julia는 가비지 컬렉션 및 멀티스레딩 작업 스케줄링을 위해 스레드 로컬 저장소에 의존합니다. 시스템 이미지 및 패키지 이미지에 대한 코드를 컴파일할 때, 이 패스는 로드 시간에 초기화된 전역 변수에서의 로드로 내장 함수 호출을 대체합니다.

코드 생성이 `swiftself` 인수와 호출 규칙을 가진 함수를 생성하는 경우, 이 패스는 `swiftself` 인수가 pgcstack이라고 가정하고 해당 인트린식을 그 인수로 대체합니다. 이렇게 하면 느린 스레드 로컬 저장소 접근이 있는 아키텍처에서 속도 향상을 제공합니다.

### RemoveAddrspaces

  * 파일 이름: `llvm-remove-addrspaces.cpp`
  * 클래스 이름: `RemoveAddrspacesPass`
  * 옵션 이름: `module(RemoveAddrspaces)`

이 패스는 하나의 주소 공간에서 다른 주소 공간으로 포인터의 이름을 바꿉니다. 이는 LLVM IR에서 Julia 전용 주소 공간을 제거하는 데 사용됩니다.

### RemoveJuliaAddrspaces

  * 파일 이름: `llvm-remove-addrspaces.cpp`
  * 클래스 이름: `RemoveJuliaAddrspacesPass`
  * 옵션 이름: `module(RemoveJuliaAddrspaces)`

이 패스는 LLVM IR에서 Julia-specific 주소 공간을 제거합니다. 주로 LLVM IR을 덜 복잡한 형식으로 표시하는 데 사용됩니다. 내부적으로는 RemoveAddrspaces 패스를 기반으로 구현됩니다.

### Multiversioning

  * 파일 이름: `llvm-multiversioning.cpp`
  * 클래스 이름: `MultiVersioningPass`
  * 옵션 이름: `module(JuliaMultiVersioning)`

이 패스는 모듈에 수정을 수행하여 다양한 아키텍처에서 실행하기 위해 최적화된 함수를 생성합니다(자세한 내용은 sysimg.md 및 pkgimg.md를 참조하십시오). 구현 측면에서, 이 패스는 함수를 복제하고 해당 플랫폼에 대해 벡터화 및 명령어 스케줄링과 같은 고급 기능을 사용하도록 최적화 프로그램이 허용할 수 있도록 다양한 대상 특정 속성을 적용합니다. 또한 Julia 이미지 로더가 로더가 실행 중인 아키텍처에 따라 호출할 함수의 적절한 버전을 선택할 수 있도록 일부 인프라를 생성합니다. 대상 특정 속성은 `julia.mv.specs` 모듈 플래그에 의해 제어되며, 컴파일 중에 [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) 환경 변수에서 파생됩니다. 이 패스는 또한 값이 1인 `julia.mv.enable` 모듈 플래그를 제공하여 활성화해야 합니다.

!!! warning
    `llvmcall`을 멀티버전으로 사용하는 것은 위험합니다. `llvmcall`은 일반적으로 Julia API에서 노출되지 않는 기능에 접근할 수 있게 해주며, 따라서 모든 아키텍처에서 사용할 수 있는 것은 아닙니다. 멀티버전이 활성화되고 `llvmcall` 표현식에 필요한 기능을 지원하지 않는 대상 아키텍처에 대한 코드 생성을 요청하면, LLVM은 아마도 오류를 발생시킬 것이며, 아마도 중단과 함께 `LLVM ERROR: Do not know how to split the result of this operator!`라는 메시지가 표시될 것입니다.


### GCInvariantVerifier

  * 파일 이름: `llvm-gc-invariant-verifier.cpp`
  * 클래스 이름: `GCInvariantVerifierPass`
  * 옵션 이름: `module(GCInvariantVerifier)`

이 패스는 LLVM IR에 대한 Julia의 불변성을 검증하는 데 사용됩니다. 여기에는 Julia의 [non-integral address spaces](https://llvm.org/docs/LangRef.html#non-integral-pointer-type) [^nislides]에서 `ptrtoint`의 존재하지 않음과 오직 축복된 `addrspacecast` 명령어만 존재하는 것(Tracked -> Derived, 0 -> Tracked 등)이 포함됩니다. IR에 대한 변환은 수행하지 않습니다.

[^nislides]: https://llvm.org/devmtg/2015-02/slides/chisnall-pointers-not-int.pdf

## Optimization Passes

이 패스는 LLVM이 스스로 수행하지 않는 LLVM IR에 대한 변환을 수행하는 데 사용됩니다. 예를 들어, 빠른 수학 플래그 전파, 탈출 분석 및 줄리아 전용 내부 함수에 대한 최적화가 있습니다. 이들은 줄리아의 의미론에 대한 지식을 사용하여 이러한 최적화를 수행합니다.

### CombineMulAdd

  * 파일 이름: `llvm-muladd.cpp`
  * 클래스 이름: `CombineMulAddPass`
  * 옵션 이름: `function(CombineMulAdd)`

이 패스는 일반 `fmul`과 빠른 `fadd`의 특정 조합을 계약 `fmul`과 빠른 `fadd`로 최적화하는 데 사용됩니다. 이는 나중에 백엔드에 의해 [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add) 명령어로 최적화되어, 더 많은 [unpredictable semantics](https://simonbyrne.github.io/notes/fastmath/)의 대가로 상당히 빠른 연산을 제공할 수 있습니다.

!!! note
    이 최적화는 `fmul`이 단일 사용을 가질 때만 발생하며, 이는 빠른 `fadd`입니다.


### AllocOpt

  * 파일 이름: `llvm-alloc-opt.cpp`
  * 클래스 이름: `AllocOptPass`
  * 옵션 이름: `function(AllocOpt)`

줄리아는 가변 객체를 할당할 장소로서 프로그램 스택의 개념이 없습니다. 그러나 스택에서 객체를 할당하면 GC 압력이 줄어들고 GPU 컴파일에 중요합니다. 따라서 `AllocOpt`는 현재 함수에서 [escape](https://en.wikipedia.org/wiki/Escape_analysis)하지 않는다고 증명할 수 있는 객체의 힙에서 스택으로의 변환을 수행합니다. 또한 사용되지 않는 할당을 제거하고, 새로 할당된 객체에 대한 typeof 호출을 최적화하며, 즉시 덮어쓰여지는 할당에 대한 저장을 제거하는 등 할당에 대한 여러 가지 다른 최적화를 수행합니다. 탈출 분석 구현은 `llvm-alloc-helpers.cpp`에 위치해 있습니다. 현재 이 패스는 `EscapeAnalysis.jl`의 정보를 사용하지 않지만, 이는 미래에 변경될 수 있습니다.

### PropagateJuliaAddrspaces

  * 파일 이름: `llvm-propagate-addrspaces.cpp`
  * 클래스 이름: `PropagateJuliaAddrspacesPass`
  * 옵션 이름: `function(PropagateJuliaAddrspaces)`

이 패스는 포인터에 대한 연산을 통해 Julia-specific 주소 공간을 전파하는 데 사용됩니다. LLVM은 최적화에 의해 addrspacecast 명령어를 추가하거나 제거하는 것이 허용되지 않으므로, 이 패스는 Julia 주소 공간에서 동등한 연산으로 대체하여 중복된 addrspace 캐스트를 제거하는 역할을 합니다. Julia의 주소 공간에 대한 자세한 정보는 (TODO link to llvm.md)를 참조하십시오.

### JuliaLICM

  * 파일 이름: `llvm-julia-licm.cpp`
  * 클래스 이름: `JuliaLICMPass`
  * 옵션 이름: `loop(JuliaLICM)`

이 패스는 루프에서 줄리아 전용 내재 함수를 끌어내는 데 사용됩니다. 구체적으로, 다음과 같은 변환을 수행합니다:

1. 루프에서 보존된 객체가 루프 불변일 때 `gc_preserve_begin`을 올리고 `gc_preserve_end`를 루프 밖으로 내보내십시오.

    1. 루프 내에서 보존된 객체는 루프의 지속 시간 동안 보존될 가능성이 높기 때문에, 이 변환은 IR에서 `gc_preserve_begin`/`gc_preserve_end` 쌍의 수를 줄일 수 있습니다. 이는 `LateLowerGCPass`가 특정 객체가 어디에서 보존되는지를 식별하는 데 더 쉽게 만듭니다.
2. 불변 객체로 쓰기 장벽을 끌어올리기

    1. 여기서는 객체가 속할 수 있는 세대가 두 개뿐이라고 가정합니다. 이를 바탕으로, 동일한 객체 쌍에 대해 쓰기 장벽이 한 번만 실행되면 됩니다. 따라서, 쓰기 대상 객체가 루프 불변일 때 쓰기 장벽을 루프 밖으로 끌어낼 수 있습니다.
3. 루프에서 탈출하지 않을 때 할당을 루프 밖으로 끌어내기

    1. 여기서 우리는 `AllocOptPass`에서 사용되는 것과 동일한 매우 보수적인 탈출 정의를 사용합니다. 이 변환은 할당이 함수 전체에서 탈출하더라도 IR에서 할당 수를 줄일 수 있습니다.

!!! note
    이 패스는 LLVM의 [MemorySSA](https://llvm.org/docs/MemorySSA.html) ([Short Video](https://www.youtube.com/watch?v=bdxWmryoHak), [Longer Video](https://www.youtube.com/watch?v=1e5y6WDbXCQ)) 및 [ScalarEvolution](https://baziotis.cs.illinois.edu/compilers/introduction-to-scalar-evolution.html) ([Newer Slides](https://llvm.org/devmtg/2018-04/slides/Absar-ScalarEvolution.pdf) [Older Slides](https://llvm.org/devmtg/2009-10/ScalarEvolutionAndLoopOptimization.pdf)) 분석을 보존하는 데 필요합니다.

