```
Channel{T=Any}(size::Int=0)
```

`T` 유형의 최대 `size` 개체를 보유할 수 있는 내부 버퍼가 있는 `Channel`을 생성합니다. [`put!`](@ref) 호출은 채널이 가득 차면 [`take!`](@ref)로 개체가 제거될 때까지 차단됩니다.

`Channel(0)`은 버퍼가 없는 채널을 생성합니다. `put!`은 일치하는 `take!`가 호출될 때까지 차단됩니다. 그리고 그 반대도 마찬가지입니다.

기타 생성자:

  * `Channel()`: 기본 생성자로, `Channel{Any}(0)`와 동일합니다.
  * `Channel(Inf)`: `Channel{Any}(typemax(Int))`와 동일합니다.
  * `Channel(sz)`: `Channel{Any}(sz)`와 동일합니다.

!!! compat "Julia 1.3"
    기본 생성자 `Channel()`과 기본 `size=0`은 Julia 1.3에 추가되었습니다.

