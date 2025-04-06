```
@boundscheck(blk)
```

표현식 `blk`를 경계 검사 블록으로 주석 처리하여 [`@inbounds`](@ref)에 의해 생략될 수 있도록 합니다.

!!! note
    `@boundscheck`가 작성된 함수는 `@inbounds`가 효과를 발휘하기 위해 호출자에 인라인되어야 합니다.


# 예제

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> @inline function g(A, i)
           @boundscheck checkbounds(A, i)
           return "accessing ($A)[$i]"
       end;

julia> f1() = return g(1:2, -1);

julia> f2() = @inbounds return g(1:2, -1);

julia> f1()
ERROR: BoundsError: attempt to access 2-element UnitRange{Int64} at index [-1]
Stacktrace:
 [1] throw_boundserror(::UnitRange{Int64}, ::Tuple{Int64}) at ./abstractarray.jl:455
 [2] checkbounds at ./abstractarray.jl:420 [inlined]
 [3] g at ./none:2 [inlined]
 [4] f1() at ./none:1
 [5] top-level scope

julia> f2()
"accessing (1:2)[-1]"
```

!!! warning
    `@boundscheck` 주석은 라이브러리 작성자로서 *다른 코드*가 [`@inbounds`](@ref)로 경계 검사를 제거할 수 있도록 선택할 수 있게 해줍니다. 거기서 언급했듯이, 호출자는 `@inbounds`를 사용하기 전에 자신의 접근이 유효한지 확인해야 합니다. 예를 들어, [`AbstractArray`](@ref) 하위 클래스에 인덱싱할 때는 인덱스를 해당 [`axes`](@ref)와 비교하여 확인해야 합니다. 따라서 `@boundscheck` 주석은 해당 동작이 올바른지 확신한 후에만 [`getindex`](@ref) 또는 [`setindex!`](@ref) 구현에 추가해야 합니다.

