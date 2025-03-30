# Parallel Computing

줄리아는 다음 네 가지 범주의 동시 및 병렬 프로그래밍을 지원합니다:

1. **비동기 "작업", 또는 코루틴**:

    줄리아 작업은 I/O, 이벤트 처리, 생산자-소비자 프로세스 및 유사한 패턴에 대한 계산을 일시 중지하고 다시 시작할 수 있게 해줍니다. 작업은 [`wait`](@ref) 및 [`fetch`](@ref)와 같은 작업을 통해 동기화할 수 있으며, [`Channel`](@ref)를 통해 통신할 수 있습니다. 엄밀히 말하면 병렬 컴퓨팅은 아니지만, 줄리아는 여러 스레드에서 [`Task`](@ref)를 예약할 수 있게 해줍니다.
2. **멀티 스레딩**:

    줄리아의 [multi-threading](@ref man-multithreading)는 메모리를 공유하면서 여러 스레드 또는 CPU 코어에서 작업을 동시에 예약할 수 있는 기능을 제공합니다. 이는 일반적으로 개인 PC나 단일 대형 다중 코어 서버에서 병렬성을 얻는 가장 쉬운 방법입니다. 줄리아의 다중 스레딩은 조합 가능하며, 하나의 다중 스레드 함수가 다른 다중 스레드 함수를 호출할 때 줄리아는 사용 가능한 리소스에 대해 모든 스레드를 전역적으로 예약하며, 과도한 예약을 하지 않습니다.
3. **분산 컴퓨팅**:

    분산 컴퓨팅은 별도의 메모리 공간을 가진 여러 Julia 프로세스를 실행합니다. 이러한 프로세스는 동일한 컴퓨터 또는 여러 컴퓨터에서 실행될 수 있습니다. [`Distributed`](@ref man-distributed) 표준 라이브러리는 Julia 함수의 원격 실행 기능을 제공합니다. 이 기본 빌딩 블록을 사용하여 다양한 종류의 분산 컴퓨팅 추상화를 구축할 수 있습니다. [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl)와 같은 패키지는 이러한 추상화의 예입니다. 반면에 [`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) 및 [`Elemental.jl`](https://github.com/JuliaParallel/Elemental.jl)와 같은 패키지는 기존 MPI 생태계의 라이브러리에 대한 접근을 제공합니다.
4. **GPU 컴퓨팅**:

    Julia GPU 컴파일러는 GPU에서 Julia 코드를 네이티브로 실행할 수 있는 기능을 제공합니다. GPU를 대상으로 하는 Julia 패키지의 풍부한 생태계가 있습니다. [JuliaGPU.org](https://juliagpu.org) 웹사이트는 기능, 지원되는 GPU, 관련 패키지 및 문서 목록을 제공합니다.
