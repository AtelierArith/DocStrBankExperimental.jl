```
sprint(f::Function, args...; context=nothing, sizehint=0)
```

주어진 함수를 I/O 스트림과 함께 호출하고 제공된 추가 인수를 사용합니다. 이 I/O 스트림에 작성된 모든 내용은 문자열로 반환됩니다. `context`는 속성이 사용될 [`IOContext`](@ref)일 수 있으며, 속성과 그 값을 지정하는 `Pair`일 수도 있고, 여러 속성과 그 값을 지정하는 `Pair`의 튜플일 수도 있습니다. `sizehint`는 버퍼의 용량(바이트 단위)을 제안합니다.

선택적 키워드 인수 `context`는 `:key=>value` 쌍, `:key=>value` 쌍의 튜플, 또는 `f`에 전달되는 I/O 스트림에 사용되는 속성이 있는 `IO` 또는 [`IOContext`](@ref) 객체로 설정할 수 있습니다. 선택적 `sizehint`는 문자열을 쓰는 데 사용되는 버퍼에 할당할 제안된 크기(바이트 단위)입니다.

!!! compat "Julia 1.7"
    키워드 `context`에 튜플을 전달하려면 Julia 1.7 이상이 필요합니다.


# 예제

```jldoctest
julia> sprint(show, 66.66666; context=:compact => true)
"66.6667"

julia> sprint(showerror, BoundsError([1], 100))
"BoundsError: attempt to access 1-element Vector{Int64} at index [100]"
```
