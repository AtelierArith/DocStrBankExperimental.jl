```
remote([p::AbstractWorkerPool], f) -> Function
```

사용 가능한 작업자에서 함수 `f`를 실행하는 익명 함수를 반환합니다(제공된 경우 [`WorkerPool`](@ref) `p`에서 가져옴) [`remotecall_fetch`](@ref)를 사용하여.
