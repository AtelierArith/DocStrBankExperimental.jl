```
begin
```

`begin...end`는 코드 블록을 나타냅니다.

```julia
begin
    println("Hello, ")
    println("World!")
end
```

일반적으로 `begin`은 필요하지 않습니다. [`function`](@ref) 및 [`let`](@ref)와 같은 키워드는 암묵적으로 코드 블록을 시작합니다. [`;`](@ref)도 참조하십시오.

`begin`은 인덱싱할 때 컬렉션의 첫 번째 인덱스 또는 배열의 차원의 첫 번째 인덱스를 나타내는 데 사용할 수 있습니다. 예를 들어, `a[begin]`은 배열 `a`의 첫 번째 요소입니다.

!!! compat "Julia 1.4"
    인덱스로서의 `begin` 사용은 Julia 1.4 이상이 필요합니다.


# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Array{Int64,2}:
 1  2
 3  4

julia> A[begin, :]
2-element Array{Int64,1}:
 1
 2
```
