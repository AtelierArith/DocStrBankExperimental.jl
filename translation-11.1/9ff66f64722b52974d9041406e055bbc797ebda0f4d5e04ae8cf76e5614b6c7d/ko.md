Lockable(value, lock = ReentrantLock())

`value`를 감싸고 제공된 `lock`과 연결된 `Lockable` 객체를 생성합니다. 이 객체는 [`@lock`](@ref), [`lock`](@ref), [`trylock`](@ref), [`unlock`](@ref)를 지원합니다. 값을 접근하려면 잠금을 유지하면서 lockable 객체의 인덱스를 사용해야 합니다.

!!! compat "Julia 1.11"
    최소 Julia 1.11이 필요합니다.


## 예제

```jldoctest
julia> locked_list = Base.Lockable(Int[]);

julia> @lock(locked_list, push!(locked_list[], 1)) # 값을 접근하려면 잠금을 유지해야 합니다
1-element Vector{Int64}:
 1

julia> lock(summary, locked_list)
"1-element Vector{Int64}"
```
