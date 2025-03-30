```
LinearAlgebra.peakflops(n::Integer=4096; eltype::DataType=Float64, ntrials::Integer=3, parallel::Bool=false)
```

`peakflops`는 이중 정밀도 [`gemm!`](@ref LinearAlgebra.BLAS.gemm!)를 사용하여 컴퓨터의 최대 플롭 비율을 계산합니다. 기본적으로 인수가 지정되지 않으면 `n x n` 크기의 두 개의 `Float64` 행렬을 곱하며, 여기서 `n = 4096`입니다. 기본 BLAS가 여러 스레드를 사용하는 경우 더 높은 플롭 비율이 실현됩니다. BLAS 스레드 수는 [`BLAS.set_num_threads(n)`](@ref)로 설정할 수 있습니다.

키워드 인수 `eltype`이 제공되면, `peakflops`는 최대 플롭 비율을 계산하기 위해 `eltype` 유형의 요소를 가진 행렬을 구성합니다.

기본적으로 `peakflops`는 3회의 실험 중 가장 좋은 타이밍을 사용합니다. `ntrials` 키워드 인수가 제공되면, `peakflops`는 최상의 타이밍을 선택하기 위해 그만큼의 실험을 사용합니다.

키워드 인수 `parallel`이 `true`로 설정되면, `peakflops`는 모든 작업 프로세서에서 병렬로 실행됩니다. 전체 병렬 컴퓨터의 플롭 비율이 반환됩니다. 병렬로 실행할 때는 1개의 BLAS 스레드만 사용됩니다. 인수 `n`은 여전히 각 프로세서에서 해결되는 문제의 크기를 나타냅니다.

!!! compat "Julia 1.1"
    이 함수는 최소한 Julia 1.1이 필요합니다. Julia 1.0에서는 표준 라이브러리 `InteractiveUtils`에서 사용할 수 있습니다.

