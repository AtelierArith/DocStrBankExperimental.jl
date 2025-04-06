# External Profiler Support

Julia는 일부 외부 추적 프로파일러에 대한 명시적인 지원을 제공하여 런타임의 실행 동작에 대한 높은 수준의 개요를 얻을 수 있도록 합니다.

현재 지원되는 프로파일러는:

  * [Tracy](https://github.com/wolfpld/tracy)
  * [Intel VTune (ITTAPI)](https://github.com/intel/ittapi)

### Adding New Zones

새로운 영역을 추가하려면 `JL_TIMING` 매크로를 사용하세요. 코드베이스에서 `JL_TIMING`을 검색하면 수많은 예제를 찾을 수 있습니다. 새로운 유형의 영역을 추가하려면 `JL_TIMING_OWNERS`에 추가하고, 필요에 따라 `JL_TIMING_EVENTS`에도 추가합니다.

### Dynamically Enabling and Disabling Zones

[`JULIA_TIMING_SUBSYSTEMS`](@ref JULIA_TIMING_SUBSYSTEMS) 환경 변수는 특정 Julia 실행에 대해 영역을 활성화하거나 비활성화할 수 있게 해줍니다. 예를 들어, 변수를 `+GC,-INFERENCE`로 설정하면 `GC` 영역이 활성화되고 `INFERENCE` 영역이 비활성화됩니다.

## Tracy Profiler

[Tracy](https://github.com/wolfpld/tracy)는 선택적으로 줄리아와 통합할 수 있는 유연한 프로파일러입니다.

전형적인 Tracy 세션은 다음과 같을 수 있습니다:

![전형적인 트레이시 사용법](tracy.png)

### Building Julia with Tracy

Tracy 통합을 활성화하려면 `Make.user` 파일에서 추가 옵션 `WITH_TRACY=1`으로 Julia를 빌드하세요.

### Installing the Tracy Profile Viewer

프로필 뷰어를 얻는 가장 쉬운 방법은 `TracyProfiler_jll` 패키지를 추가하고 다음과 같이 프로파일러를 실행하는 것입니다:

```julia
run(TracyProfiler_jll.tracy())
```

!!! note
    macOS에서는 프로파일러의 UI 요소가 지나치게 크게 보일 경우 `TRACY_DPI_SCALE` 환경 변수를 `1.0`으로 설정할 수 있습니다.


"헤드리스" 인스턴스를 실행하여 추적을 디스크에 저장하려면 다음을 사용하십시오.

```julia
run(`$(TracyProfiler_jll.capture()) -o mytracefile.tracy`)
```

대신.

Tracy UI 사용에 대한 정보는 Tracy 매뉴얼을 참조하십시오.

### Profiling Julia with Tracy

트레이시로 줄리아 프로파일링을 위한 전형적인 워크플로우는 줄리아를 다음과 같이 시작하는 것입니다:

```julia
JULIA_WAIT_FOR_TRACY=1 ./julia -e '...'
```

환경 변수는 Julia가 Tracy 프로파일러에 성공적으로 연결될 때까지 실행을 기다리도록 보장합니다. 이후 Tracy 프로파일러 UI를 사용하여 `Connect`를 클릭하면 Julia 실행이 재개되고 프로파일링이 시작됩니다.

### Profiling package precompilation with Tracy

패키지 사전 컴파일 프로세스를 프로파일링하려면, 사전 컴파일하려는 패키지를 사용하여 `Base.compilecache`를 명시적으로 호출하는 것이 가장 쉽습니다:

```julia
pkg = Base.identify_package("SparseArrays")
withenv("JULIA_WAIT_FOR_TRACY" => 1, "TRACY_PORT" => 9001) do
    Base.compilecache(pkg)
end
```

여기에서는 tracy에 대한 사용자 지정 포트를 사용하여 Tracy UI에서 연결할 올바른 클라이언트를 찾기 쉽게 만듭니다.

### Adding metadata to zones

다양한 `jl_timing_show_*` 및 `jl_timing_printf` 함수는 문자열(또는 문자열들)을 영역에 연결하는 데 사용할 수 있습니다. 예를 들어, 추론을 위한 추적 영역은 추론되고 있는 메서드 인스턴스를 보여줍니다.

`TracyCZoneColor` 함수를 사용하여 특정 영역의 색상을 설정할 수 있습니다. 코드베이스를 검색하여 어떻게 사용되는지 확인하세요.

### Viewing Tracy files in your browser

https://topolarity.github.io/trace-viewer/에서 Tracy 트레이스를 위한 (실험적인) 웹 뷰어를 방문하세요.

로컬 `.tracy` 파일을 열거나 웹에서 URL을 제공할 수 있습니다(예: Github 리포지토리의 파일). 웹에서 추적 파일을 로드하면 다른 사람과 페이지 URL을 직접 공유할 수 있어 동일한 추적을 볼 수 있습니다.

### Enabling stack trace samples

Tracy에서 호출 스택 샘플링을 활성화하려면, `Make.user` 파일에 다음 옵션으로 Julia를 빌드하세요:

```
WITH_TRACY := 1
WITH_TRACY_CALLSTACKS := 1
USE_BINARYBUILDER_LIBTRACYCLIENT := 0
```

`make -C deps clean-libtracyclient`를 실행하여 Tracy의 재빌드를 강제로 수행해야 할 수도 있습니다.

이 기능은 추적 크기와 프로파일링 오버헤드에 상당한 영향을 미치므로, 가능할 경우 호출 스택 샘플링을 끄는 것이 좋습니다. 특히 추적 파일을 온라인으로 공유할 계획이라면 더욱 그렇습니다.

Julia JIT 런타임은 아직 Tracy의 심볼화 통합을 지원하지 않으므로, Julia 함수는 일반적으로 이러한 스택 추적에서 알 수 없습니다.

## Intel VTune (ITTAPI) Profiler

*이 섹션은 아직 작성되지 않았습니다.*
