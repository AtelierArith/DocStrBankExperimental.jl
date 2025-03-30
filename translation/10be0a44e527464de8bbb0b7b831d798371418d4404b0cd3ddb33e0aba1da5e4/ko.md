```
=
```

`=`는 할당 연산자입니다.

  * 변수 `a`와 표현식 `b`에 대해, `a = b`는 `a`가 `b`의 값을 참조하도록 만듭니다.
  * 함수 `f(x)`에 대해, `f(x) = x`는 새로운 함수 상수 `f`를 정의하거나, `f`가 이미 정의되어 있는 경우 `f`에 새로운 메서드를 추가합니다; 이 사용법은 `function f(x); x; end`와 동등합니다.
  * `a[i] = v`는 [`setindex!`](@ref)`(a,v,i)`를 호출합니다.
  * `a.b = c`는 [`setproperty!`](@ref)`(a,:b,c)`를 호출합니다.
  * 함수 호출 내에서, `f(a=b)`는 `b`를 키워드 인수 `a`의 값으로 전달합니다.
  * 쉼표가 있는 괄호 안에서, `(a=1,)`는 [`NamedTuple`](@ref)를 생성합니다.

# 예제

`a`를 `b`에 할당하는 것은 `b`의 복사본을 생성하지 않습니다; 대신 [`copy`](@ref) 또는 [`deepcopy`](@ref)를 사용하십시오.

```jldoctest
julia> b = [1]; a = b; b[1] = 2; a
1-element Array{Int64, 1}:
 2

julia> b = [1]; a = copy(b); b[1] = 2; a
1-element Array{Int64, 1}:
 1

```

함수에 전달된 컬렉션도 복사되지 않습니다. 함수는 인수들이 참조하는 객체의 내용을 수정(변형)할 수 있습니다. (이런 기능을 가진 함수의 이름은 관례적으로 '!'로 끝납니다.)

```jldoctest
julia> function f!(x); x[:] .+= 1; end
f! (generic function with 1 method)

julia> a = [1]; f!(a); a
1-element Array{Int64, 1}:
 2

```

할당은 반복 가능한 객체에서 값을 가져와 여러 변수에 병렬로 작동할 수 있습니다:

```jldoctest
julia> a, b = 4, 5
(4, 5)

julia> a, b = 1:3
1:3

julia> a, b
(1, 2)

```

할당은 여러 변수에 연속적으로 작동할 수 있으며, 가장 오른쪽 표현식의 값을 반환합니다:

```jldoctest
julia> a = [1]; b = [2]; c = [3]; a = b = c
1-element Array{Int64, 1}:
 3

julia> b[1] = 2; a, b, c
([2], [2], [2])

```

범위를 벗어난 인덱스에서의 할당은 컬렉션을 확장하지 않습니다. 컬렉션이 [`Vector`](@ref)인 경우, 대신 [`push!`](@ref) 또는 [`append!`](@ref)로 확장할 수 있습니다.

```jldoctest
julia> a = [1, 1]; a[3] = 2
ERROR: BoundsError: attempt to access 2-element Array{Int64, 1} at index [3]
[...]

julia> push!(a, 2, 3)
4-element Array{Int64, 1}:
 1
 1
 2
 3

```

`[]`를 할당하는 것은 컬렉션에서 요소를 제거하지 않습니다; 대신 [`filter!`](@ref)를 사용하십시오.

```jldoctest
julia> a = collect(1:3); a[a .<= 1] = []
ERROR: DimensionMismatch: tried to assign 0 elements to 1 destinations
[...]

julia> filter!(x -> x > 1, a) # 제자리에서 수행되므로 a = a[a .> 1]보다 더 효율적입니다.
2-element Array{Int64, 1}:
 2
 3

```
