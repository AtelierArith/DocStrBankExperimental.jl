```
Threads.atomic_cas!(x::Atomic{T}, cmp::T, newval::T) where T
```

원자적으로 `x`를 비교하고 설정합니다.

`x`의 값을 `cmp`와 원자적으로 비교합니다. 같으면 `newval`을 `x`에 씁니다. 그렇지 않으면 `x`는 수정되지 않은 채로 남습니다. `x`의 이전 값을 반환합니다. 반환된 값을 `cmp`와 비교(`===`를 통해)함으로써 `x`가 수정되었는지, 이제 새로운 값 `newval`을 가지고 있는지를 알 수 있습니다.

자세한 내용은 LLVM의 `cmpxchg` 명령어를 참조하십시오.

이 함수는 트랜잭셔널 의미론을 구현하는 데 사용할 수 있습니다. 트랜잭션 전에 `x`의 값을 기록합니다. 트랜잭션 후, 그 동안 `x`가 수정되지 않았다면 새로운 값이 저장됩니다.

# 예제

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 4, 2);

julia> x
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 3, 2);

julia> x
Base.Threads.Atomic{Int64}(2)
```
