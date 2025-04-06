```
AbstractWorkerPool
```

워커 풀의 수퍼타입으로 [`WorkerPool`](@ref) 및 [`CachingPool`](@ref)와 같은. `AbstractWorkerPool`은 다음을 구현해야 합니다:

  * [`push!`](@ref) - 전체 풀에 새로운 워커 추가 (사용 가능 + 바쁜)
  * [`put!`](@ref) - 워커를 사용 가능한 풀로 되돌리기
  * [`take!`](@ref) - 사용 가능한 풀에서 워커를 가져오기 (원격 함수 실행에 사용)
  * [`length`](@ref) - 전체 풀에서 사용 가능한 워커 수
  * [`isready`](@ref) - 풀에서 `take!`가 블록되면 false를 반환하고, 그렇지 않으면 true를 반환

위의 기본 구현( `AbstractWorkerPool`에서)은 다음 필드를 요구합니다:

  * `channel::Channel{Int}`
  * `workers::Set{Int}`

여기서 `channel`은 자유로운 워커 pid를 포함하고 `workers`는 이 풀과 관련된 모든 워커의 집합입니다.
