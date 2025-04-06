```
CachingPool(workers::Vector{Int})
```

`AbstractWorkerPool`의 구현입니다. [`remote`](@ref), [`remotecall_fetch`](@ref), [`pmap`](@ref) (및 원격으로 함수를 실행하는 다른 원격 호출)은 특히 클로저(대량의 데이터를 캡처할 수 있음)에서 작업 노드에 직렬화/역직렬화된 함수를 캐싱하는 것의 이점을 누립니다.

원격 캐시는 반환된 `CachingPool` 객체의 수명 동안 유지됩니다. 캐시를 더 일찍 지우려면 `clear!(pool)`을 사용하세요.

전역 변수의 경우, 클로저에서 캡처되는 것은 바인딩만이며 데이터는 아닙니다. 전역 데이터를 캡처하기 위해 `let` 블록을 사용할 수 있습니다.

# 예제

```julia
const foo = rand(10^8);
wp = CachingPool(workers())
let foo = foo
    pmap(i -> sum(foo) + i, wp, 1:100);
end
```

위 코드는 `foo`를 각 작업자에게 한 번만 전송합니다.
