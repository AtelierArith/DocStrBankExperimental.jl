```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/NEWS.md"
```

# Julia v1.11 Release Notes

## New language features

  * 새로운 `Memory` 유형은 `Array`의 대안으로서 더 낮은 수준의 컨테이너를 제공합니다. `Memory`는 오버헤드가 적고 생성자가 더 빠르기 때문에 `Array`의 모든 기능(예: 다차원)을 필요로 하지 않는 상황에서 좋은 선택입니다. 이제 `Array` 유형의 대부분은 `Memory` 위에 구현되어 있어 여러 함수(예: `push!`)의 속도가 크게 향상되었으며, 더 유지 관리하기 쉬운 코드로 이어집니다. ([#51319](https://github.com/JuliaLang/julia/issues/51319))
  * `public` is a new keyword. Symbols marked with `public` are considered public API. Symbols marked with `export` are now also treated as public API. The difference between `public` and `export` is that `public` names do not become available when `using` a package/module ([#50105](https://github.com/JuliaLang/julia/issues/50105)).
  * `ScopedValue`는 작업 간 상속을 통한 동적 범위를 구현합니다 ([#50958](https://github.com/JuliaLang/julia/issues/50958)).
  * `Manifest.toml` 파일은 이제 `Manifest-v{major}.{minor}.toml` 형식으로 이름을 변경할 수 있으며, 주어진 줄리아 버전에서 우선적으로 선택됩니다. 즉, 같은 폴더 내에서 `Manifest-v1.11.toml`은 v1.11에 의해 사용되고, `Manifest.toml`은 다른 모든 줄리아 버전에 의해 사용됩니다. 이는 여러 줄리아 버전을 동시에 관리하는 것을 더 쉽게 만듭니다 ([#43845](https://github.com/JuliaLang/julia/issues/43845)).
  * 유니코드 15.1 지원 ([#51799](https://github.com/JuliaLang/julia/issues/51799)).

## Language changes

  * 프리컴파일 중에 `atexit` 후크가 이제 출력 파일을 저장하기 전에 실행됩니다. 이를 통해 사용자는 프로그램이 종료를 시작하고자 할 때 백그라운드 상태(예: `Timer` 닫기 및 하트비트 작업에 대한 연결 끊기 알림 전송)를 안전하게 정리하고 다른 리소스를 정리할 수 있습니다.
  * 코드 커버리지 및 malloc 추적은 더 이상 패키지 사전 컴파일 단계에서 생성되지 않습니다. 또한 이러한 모드에서는 추적되지 않는 패키지에 대해 pkgimage 캐시가 이제 사용됩니다. 이는 커버리지 테스트(`julia-actions/julia-runtest`의 기본값)가 테스트 중인 패키지를 제외한 모든 다른 패키지에 대해 기본적으로 pkgimage 캐시를 사용하게 됨을 의미하며, 이는 테스트 실행 속도가 빨라질 가능성이 있습니다. ([#52123](https://github.com/JuliaLang/julia/issues/52123))
  * `JULIA_DEPOT_PATH`에 경로를 지정하면 이제 빈 문자열이 확장되어 기본 사용자 저장소([#51448](https://github.com/JuliaLang/julia/issues/51448))를 생략하게 됩니다.
  * 프리컴파일 캐시 파일은 이제 이동 가능하며, 그 유효성은 `mtime` 대신 소스 파일의 콘텐츠 해시를 통해 검증됩니다 ([#49866](https://github.com/JuliaLang/julia/issues/49866)).
  * 확장 프로그램은 이제 다른 확장 프로그램에 의존할 수 있으며, 그 트리거가 의존하고자 하는 확장 프로그램의 모든 트리거를 포함하고 있어야 합니다 (+ 최소한 하나의 다른 트리거). 이 요구 사항을 충족하지 않는 확장 간 의존성은 확장 사이클을 방지하기 위해 사전 컴파일 중에 `Base.get_extension`을 사용하는 것이 차단됩니다 [#55557](https://github.com/JuliaLang/julia/issues/55557).

## Compiler/Runtime improvements

  * 업데이트된 GC 휴리스틱은 개별 객체 대신 할당된 페이지를 계산합니다 ([#50144](https://github.com/JuliaLang/julia/issues/50144)).
  * `Base.@assume_effects`에 대한 주석을 코드 블록에 추가하는 지원이 추가되었습니다 ([#52400](https://github.com/JuliaLang/julia/issues/52400)).

## Command-line option changes

  * Julia의 진입점은 `Main.main(args)`로 표준화되었습니다. 이는 `@main` 매크로를 사용하여 명시적으로 선택해야 합니다(자세한 내용은 문서 문자열을 참조하십시오). 선택한 경우, `julia`가 스크립트나 표현식을 실행하기 위해 호출되면(즉, `julia script.jl` 또는 `julia -e expr`를 사용하여), `julia`는 이후에 자동으로 `Main.main` 함수를 실행합니다. 이는 스크립트와 컴파일 워크플로우를 통합하기 위한 것으로, 코드 로딩이 컴파일러에서 발생할 수 있고 `Main.main`의 실행이 결과 실행 파일에서 발생할 수 있습니다. 대화형 사용의 경우, `main` 함수를 정의하는 것과 스크립트 끝에서 코드를 직접 실행하는 것 사이에는 의미상의 차이가 없습니다 ([#50974](https://github.com/JuliaLang/julia/issues/50974)).
  * `--compiled-modules` 및 `--pkgimages` 플래그는 이제 `existing`으로 설정할 수 있으며, 이는 Julia가 기존 캐시 파일을 로드하는 것을 고려하지만 새로운 파일을 생성하지 않도록 합니다 ([#50586](https://github.com/JuliaLang/julia/issues/50586), [#52573](https://github.com/JuliaLang/julia/issues/52573)).
  * `--project` 인자는 이제 `@script`를 허용하여 전달된 스크립트 파일에 상대적인 Project.toml이 있는 디렉토리의 경로를 제공합니다. `--project=@script/foo`는 `foo` 하위 디렉토리를 나타냅니다. 경로가 주어지지 않으면 (즉, `--project=@script`) (마치 `--project=@.`처럼) 디렉토리와 그 부모 디렉토리에서 Project.toml을 검색합니다 ([#50864](https://github.com/JuliaLang/julia/issues/50864) 및 [#53352](https://github.com/JuliaLang/julia/issues/53352))

## Multi-threading changes

  * `Threads.@threads`는 비균일 작업 부하를 위한 `:greedy` 스케줄러를 지원합니다 ([#52096](https://github.com/JuliaLang/julia/issues/52096)).
  * 새로운 공개(하지만 내보내지 않은) 구조체 `Base.Lockable{T, L<:AbstractLock}`은 리소스와 그 잠금을 함께 묶는 것을 쉽게 만들어 줍니다 ([#52898](https://github.com/JuliaLang/julia/issues/52898)).

## Build system changes

  * 새로운 `Makefile`이 프로파일 기반 및 링크 타임 최적화(PGO 및 LTO) 전략을 사용하여 Julia와 LLVM을 빌드하기 위해 추가되었습니다. `contrib/pgo-lto/Makefile`을 참조하세요 ([#45641](https://github.com/JuliaLang/julia/issues/45641)).

## New library functions

  * 세 가지 새로운 유형이 "주석"(`Pair{Symbol, Any}` 항목, 예: `:lang => "en"` 또는 `:face => :magenta`) 아이디어를 중심으로 만들어졌습니다. 이러한 주석은 가능한 경우 연산(예: `*`를 사용한 문자열 연결) 간에 유지됩니다.

      * `AnnotatedString`는 새로운 `AbstractString` 유형입니다. 이는 기본 문자열을 감싸고 문자열의 특정 영역에 주석을 첨부할 수 있도록 합니다. 이 유형은 새로운 `StyledStrings` 표준 라이브러리에서 스타일링 정보를 보유하는 데 광범위하게 사용됩니다.
      * `AnnotatedChar`는 새로운 `AbstractChar` 유형입니다. 다른 char를 감싸고 해당 char에 적용되는 주석 목록을 보유합니다.
      * `AnnotatedIOBuffer`는 `IOBuffer`를 모방한 새로운 `IO` 유형으로, 주석이 달린 콘텐츠를 위한 특화된 `read`/`write` 메서드를 가지고 있습니다. 이는 일종의 "문자열 빌더"로 생각할 수 있으며, 주석이 달린 콘텐츠와 주석이 없는 콘텐츠 간의 연결 역할도 합니다.
  * `in!(x, s::AbstractSet)`는 `x`가 `s`에 있는지 여부를 반환하며, `x`가 없으면 `s`에 `x`를 삽입합니다 ([#45156](https://github.com/JuliaLang/julia/issues/45156), [#51636](https://github.com/JuliaLang/julia/issues/51636)).
  * 새로운 `Libc.mkfifo` 함수는 Unix 플랫폼에서 `mkfifo` C 함수를 래핑합니다 ([#34587](https://github.com/JuliaLang/julia/issues/34587)).
  * `logrange(start, stop; length)` makes a range of constant ratio, instead of constant step ([#39071](https://github.com/JuliaLang/julia/issues/39071))
  * `copyuntil(out, io, delim)` 및 `copyline(out, io)`는 `out::IO` 스트림으로 데이터를 복사합니다 ([#48273](https://github.com/JuliaLang/julia/issues/48273)).
  * `eachrsplit(string, pattern)`은 오른쪽에서 왼쪽으로 분할된 부분 문자열을 반복합니다 ([#51646](https://github.com/JuliaLang/julia/issues/51646)).
  * `Sys.username()`는 현재 사용자의 사용자 이름을 반환하는 데 사용할 수 있습니다 ([#51897](https://github.com/JuliaLang/julia/issues/51897)).
  * `Sys.isreadable(), Sys.iswritable()`는 현재 사용자가 각각 읽기 및 쓰기를 허용하는 접근 권한이 있는지 확인하는 데 사용할 수 있습니다. ([#53320](https://github.com/JuliaLang/julia/issues/53320)).
  * `GC.logging_enabled()`는 `GC.enable_logging`를 통해 GC 로깅이 활성화되었는지 테스트하는 데 사용할 수 있습니다 ([#51647](https://github.com/JuliaLang/julia/issues/51647)).
  * `IdSet`는 이제 Base에서 내보내지며 공개적으로 간주됩니다 ([#53262](https://github.com/JuliaLang/julia/issues/53262)).
  * `@time`는 `ReentrantLock`이 대기해야 했던 모든 잠금 충돌의 수를 보고하며, 새로운 매크로 `@lock_conflicts`는 해당 수를 반환합니다 ([#52883](https://github.com/JuliaLang/julia/issues/52883)).
  * 새로운 매크로 `Base.Cartesian.@ncallkw`는 `Base.Cartesian.@ncall`과 유사하지만, 함수 호출에 키워드 인수를 추가할 수 있습니다 ([#51501](https://github.com/JuliaLang/julia/issues/51501)).
  * 새로운 함수 `Docs.hasdoc(module, symbol)`는 이름에 docstring이 있는지 여부를 알려줍니다 ([#52139](https://github.com/JuliaLang/julia/issues/52139)).
  * 새로운 함수 `Docs.undocumented_names(module)`는 모듈의 문서화되지 않은 공개 이름을 반환합니다 ([#52413](https://github.com/JuliaLang/julia/issues/52413)).

## New library features

  * `invmod(n, T)`는 이제 `T`가 정의하는 모듈러 정수 링에서 `n`의 모듈러 역수를 계산합니다 ([#52180](https://github.com/JuliaLang/julia/issues/52180)).
  * `invmod(n)`는 기본 정수 유형에 대해 `invmod(n, typeof(n))`의 약어입니다 ([#52180](https://github.com/JuliaLang/julia/issues/52180)).
  * `replace(string, pattern...)`는 이제 문자열을 반환하는 대신 출력을 스트림에 쓰기 위한 선택적 `IO` 인수를 지원합니다 ([#48625](https://github.com/JuliaLang/julia/issues/48625)).
  * 새로운 메서드 `allequal(f, itr)` 및 `allunique(f, itr)`가 프레디케이트 함수([#47679](https://github.com/JuliaLang/julia/issues/47679))를 사용합니다.
  * `sizehint!(s, n)`는 축소를 비활성화하는 선택적 `shrink` 인수를 지원합니다 ([#51929](https://github.com/JuliaLang/julia/issues/51929)).
  * Passing an `IOBuffer` as a stdout argument for `Process` spawn now works as expected, synchronized with `wait` or `success`, so a `Base.BufferStream` is no longer required there for correctness to avoid data races ([#52461](https://github.com/JuliaLang/julia/issues/52461)).
  * 프로세스가 종료된 후, `closewrite`는 전달된 스트림에서 자동으로 호출되지 않습니다. 대신 프로세스에서 `wait`를 호출하여 내용이 완전히 기록되었는지 확인한 다음, 데이터 경합을 피하기 위해 수동으로 `closewrite`를 호출하거나 `open`의 콜백 형식을 사용하여 모든 작업을 자동으로 처리하도록 하십시오 ([#52461](https://github.com/JuliaLang/julia/issues/52461)).
  * `@timed` 이제 추가로 경과된 컴파일 및 재컴파일 시간을 반환합니다 ([#52889](https://github.com/JuliaLang/julia/issues/52889)).
  * `filter`는 이제 `NamedTuple`에서 작동할 수 있습니다 ([#50795](https://github.com/JuliaLang/julia/issues/50795)).
  * `Iterators.cycle(iter, n)`는 `iter`를 무한히 반복하는 대신 고정된 횟수만큼 실행합니다. ([#47354](https://github.com/JuliaLang/julia/issues/47354))
  * `zero(::AbstractArray)`는 이제 재귀적으로 적용되므로 `zero([[1,2],[3,4,5]])`는 오류를 발생시키는 대신 덧셈 항등원 `[[0,0],[0,0,0]]`을 생성합니다 ([#38064](https://github.com/JuliaLang/julia/issues/38064)).
  * `include_dependency(path; track_content=true)`는 사전 컴파일 캐시의 재배치 가능성을 복원하기 위해 `mtime` 대신 사전 컴파일 종속성의 해싱을 사용하는 것으로 전환할 수 있게 해줍니다 ([#51798](https://github.com/JuliaLang/julia/issues/51798)).

## Standard library changes

  * 대체 방법 `write(::IO, ::AbstractArray)`는 각 요소에 대해 `write`를 재귀적으로 호출하던 방식에서, 이제는 각 값의 메모리 내 표현을 작성합니다. 예를 들어, `write(io, 'a':'b')`는 이제 각 문자의 UTF-8 표현을 작성하는 대신 각 문자에 대해 4바이트를 작성합니다. 새로운 형식은 `Array`에서 사용되는 형식과 호환되어, `read!`를 사용하여 데이터를 다시 가져올 수 있습니다 ([#42593](https://github.com/JuliaLang/julia/issues/42593)).
  * 상태가 있는 반복자에 대해 `length`를 일반적으로 일관된 방식으로 정의하는 것은 불가능합니다. `Stateful` 반복자에 대한 잘못된 결과가 조용히 발생할 가능성은 `length(::Stateful)` 메서드를 삭제함으로써 해결되었습니다. `Stateful`의 마지막 타입 매개변수도 사라졌습니다. 이슈: ([#47790](https://github.com/JuliaLang/julia/issues/47790)), PR: ([#51747](https://github.com/JuliaLang/julia/issues/51747)).

#### Package Manager

  * 이제 Project.toml의 `[sources]` 섹션에서 패키지에 대한 "sources"를 지정할 수 있습니다. 이를 통해 비등록된 일반 또는 테스트 종속성을 추가할 수 있습니다.
  * Pkg는 이제 `[compat]` 경계를 준수하며, 실행 중인 Julia 바이너리의 버전이 `Project.toml`의 경계와 호환되지 않을 경우 오류를 발생시킵니다. Pkg는 항상 Registry 패키지 작업 시 이 호환성을 준수해왔습니다. 이 변경 사항은 주로 로컬 패키지에 영향을 미칩니다.
  * `pkg> add` 및 `Pkg.add`는 활성 환경이 패키지(이름 및 uuid 항목이 있음)인 경우 새로운 직접 종속성에 대한 호환성 항목을 추가합니다.
  * 이제 종속성을 `pkg> add --weak/extra Foo` 또는 `Pkg.add("Foo", target=:weakdeps/:extras)` 형식을 통해 약한 종속성 또는 추가 항목으로 직접 추가할 수 있습니다.

#### StyledStrings

  * 새로운 표준 라이브러리로 스타일링을 보다 포괄적이고 구조화된 방식으로 처리합니다 ([#49586](https://github.com/JuliaLang/julia/issues/49586)).
  * 새로운 `Faces` 구조체는 텍스트 스타일링 정보를 담는 컨테이너 역할을 하며(타입페이스, 색상 및 장식 등을 생각해보세요), 편리하고 확장 가능(`addface!`를 통해)하며 사용자 맞춤형(`Faces.toml` 및 `loadfaces!`를 통해) 스타일이 적용된 콘텐츠에 대한 접근 방식을 제공합니다 ([#49586](https://github.com/JuliaLang/julia/issues/49586)).
  * 새로운 `@styled_str` 문자열 매크로는 다양한 얼굴이나 다른 속성이 적용된 `AnnotatedString`을 생성하는 편리한 방법을 제공합니다 ([#49586](https://github.com/JuliaLang/julia/issues/49586)).

#### Libdl

  * 새로운 `LazyLibrary` 유형이 `Libdl`에서 내보내져 체인된 지연 라이브러리 로드를 구축하는 데 사용됩니다. 주로 JLL 내에서 사용됩니다 ([#50074](https://github.com/JuliaLang/julia/issues/50074)).

#### LinearAlgebra

  * `cbrt(::AbstractMatrix{<:Real})`는 이제 정의되었으며, 실수 행렬의 실수 값 행렬 세제곱근을 반환합니다 ([#50661](https://github.com/JuliaLang/julia/issues/50661)).
  * `eigvals/eigen(A, bunchkaufman(B))` 및 `eigvals/eigen(A, lu(B))`는 각각 `B`의 Bunchkaufman (LDL) 및 LU 분해를 활용하여 이제 `A`와 `B`의 일반화된 고유값(`eigen`: 및 고유벡터)을 효율적으로 계산합니다. 참고: 두 번째 인수는 `bunchkaufman` 또는 `lu`의 출력입니다 ([#50471](https://github.com/JuliaLang/julia/issues/50471)).
  * 이제 `eigvals/eigen(::Hermitian{<:Tridiagonal})`에 대한 전문 디스패치가 있으며, 이는 유사 변환을 수행하여 실수 대칭 삼대각 행렬을 생성하고, 이를 LAPACK 루틴을 사용하여 해결합니다 ([#49546](https://github.com/JuliaLang/julia/issues/49546)).
  * 구조화된 행렬은 이제 부모의 축(`대칭`/`에르미트`/`추상삼각`/`상부 헤센베르크`)을 유지하거나, 주 대각선의 축(밴드 행렬의 경우)을 유지합니다. ([#52480](https://github.com/JuliaLang/julia/issues/52480))
  * `bunchkaufman` 및 `bunchkaufman!`는 이제 모든 `AbstractFloat`, `Rational` 및 그 복소수 변형에 대해 작동합니다. `bunchkaufman`은 내부적으로 `Rational{BigInt}`로 변환하여 `Integer` 유형을 지원합니다. 실 대칭 또는 에르미트 행렬의 `BunchKaufman` 분해 객체에 의해 주어진 대각 요소의 관성을 계산하는 새로운 함수 `inertia`가 추가되었습니다. 복소수 대칭 행렬의 경우, `inertia`는 대각 요소의 영 고유값 수만 계산합니다 ([#51487](https://github.com/JuliaLang/julia/issues/51487)).
  * Packages that specialize matrix-matrix `mul!` with a method signature of the form `mul!(::AbstractMatrix, ::MyMatrix, ::AbstractMatrix, ::Number, ::Number)` no longer encounter method ambiguities when interacting with `LinearAlgebra`. Previously, ambiguities used to arise when multiplying a `MyMatrix` with a structured matrix type provided by LinearAlgebra, such as `AbstractTriangular`, which used to necessitate additional methods to resolve such ambiguities. Similar sources of ambiguities have also been removed for matrix-vector `mul!` operations ([#52837](https://github.com/JuliaLang/julia/issues/52837)).
  * `lu`와 `issuccess(::LU)`는 이제 `allowsingular` 키워드 인수를 허용합니다. `true`로 설정하면, 랭크가 결핍된 U 인수를 가진 유효한 인수분해가 오류를 발생시키는 대신 성공으로 처리됩니다. 이러한 인수분해는 "실패한 인수분해" 메시지를 출력하는 대신 "랭크 결핍" 노트와 함께 인수를 출력하여 표시됩니다. ([#52957](https://github.com/JuliaLang/julia/issues/52957))

#### Random

  * `rand`는 이제 `Tuple` 타입에 대한 샘플링을 지원합니다 ([#35856](https://github.com/JuliaLang/julia/issues/35856), [#50251](https://github.com/JuliaLang/julia/issues/50251)).
  * `rand`는 이제 `Pair` 타입에 대한 샘플링을 지원합니다 ([#28705](https://github.com/JuliaLang/julia/issues/28705)).
  * `Random`에서 제공하는 RNG를 시드할 때, 이제 음의 정수 시드를 사용할 수 있습니다 ([#51416](https://github.com/JuliaLang/julia/issues/51416)).
  * `Random`의 시드 가능한 난수 생성기는 이제 문자열로 시드할 수 있습니다. 예: `seed!(rng, "a random seed")` ([#51527](https://github.com/JuliaLang/julia/issues/51527)).

#### REPL

  * 탭 완성 힌트는 이제 REPL에서 입력할 때 더 밝은 텍스트로 표시됩니다. 비활성화하려면 `Base.active_repl.options.hint_tab_completes = false`를 대화식으로 설정하거나 startup.jl에 다음을 추가하세요:

    ```
    if VERSION >= v"1.11.0-0"
      atreplinit() do repl
          repl.options.hint_tab_completes = false
      end
    end
    ```

    ([#51229](https://github.com/JuliaLang/julia/issues/51229)).
  * Meta-M은 빈 프롬프트로 이전 비주요 컨텍스트 모듈과 주요 모듈 간의 전환을 간단하게 하여 쉽게 왔다 갔다 할 수 있도록 합니다 ([#51616](https://github.com/JuliaLang/julia/issues/51616), [#52670](https://github.com/JuliaLang/julia/issues/52670)).

#### Dates

문서화되지 않은 함수 `adjust`는 더 이상 내보내지지 않지만 이제 문서화되었습니다 ([#53092](https://github.com/JuliaLang/julia/issues/53092)).

#### Statistics

  * 통계는 이제 업그레이드 가능한 표준 라이브러리입니다 ([#46501](https://github.com/JuliaLang/julia/issues/46501)).

#### Distributed

  * `pmap`는 이제 기본적으로 `CachingPool`을 사용합니다 ([#33892](https://github.com/JuliaLang/julia/issues/33892)).

## Deprecated or removed

  * `Base.map`, `Iterators.map`, 및 `foreach`는 단일 인수 메서드를 잃었습니다 ([#52631](https://github.com/JuliaLang/julia/issues/52631)).

## External dependencies

  * libuv 라이브러리가 v1.44.2에서 v1.48.0으로 업데이트되었습니다 ([#49937](https://github.com/JuliaLang/julia/issues/49937)).
  * `tput`는 더 이상 터미널 기능을 확인하는 데 사용되지 않으며, 순수 Julia terminfo 파서로 대체되었습니다 ([#50797](https://github.com/JuliaLang/julia/issues/50797)).
  * 터미널 정보 데이터베이스인 `terminfo`는 이제 기본적으로 포함되어 있어, 시스템에 `terminfo`가 없을 때 더 나은 REPL 사용자 경험을 제공합니다. Julia는 Makefile 옵션 `WITH_TERMINFO=0`을 사용하여 데이터베이스를 포함하지 않고 빌드할 수 있습니다. ([#55411](https://github.com/JuliaLang/julia/issues/55411))

## Tooling Improvements

  * CI는 이제 모든 PR에서 제한된 자동 오타 감지를 수행합니다. 오타 CI 검사가 실패한 PR을 병합하면, 보고된 오타는 동일한 파일을 편집하는 PR의 향후 CI 실행에서 자동으로 무시됩니다 ([#51704](https://github.com/JuliaLang/julia/issues/51704)).
