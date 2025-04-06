```
Ref{T}
```

타입 `T`의 데이터를 안전하게 참조하는 객체입니다. 이 타입은 올바른 타입의 유효한 Julia 할당 메모리를 가리키도록 보장됩니다. `Ref` 자체가 참조되는 한, 기본 데이터는 가비지 컬렉터에 의해 해제되는 것으로부터 보호됩니다.

Julia에서 `Ref` 객체는 `[]`로 역참조(로드 또는 저장)됩니다.

타입 `T`의 값 `x`에 대한 `Ref`의 생성은 일반적으로 `Ref(x)`로 작성됩니다. 또한, 컨테이너(예: Array 또는 Ptr)에 대한 내부 포인터를 생성할 때는 `Ref(a, i)`로 작성하여 `a`의 `i`-번째 요소에 대한 참조를 생성할 수 있습니다.

`Ref{T}()`는 초기화 없이 타입 `T`의 값에 대한 참조를 생성합니다. 비트 타입 `T`의 경우, 값은 현재 할당된 메모리에 있는 어떤 것이든 될 것입니다. 비비트 타입 `T`의 경우, 참조는 정의되지 않으며 이를 역참조하려고 하면 "UndefRefError: access to undefined reference"라는 오류가 발생합니다.

`Ref`가 정의되지 않은 참조인지 확인하려면 [`isassigned(ref::RefValue)`](@ref)를 사용하십시오. 예를 들어, `isassigned(Ref{T}())`는 `T`가 비트 타입이 아닐 경우 `false`입니다. `T`가 비트 타입인 경우, `isassigned(Ref{T}())`는 항상 true입니다.

`ccall` 인수로 전달될 때( `Ptr` 또는 `Ref` 타입으로), `Ref` 객체는 참조하는 데이터에 대한 네이티브 포인터로 변환됩니다. 대부분의 `T`에 대해, 또는 `Ptr{Cvoid}`로 변환될 때, 이는 객체 데이터에 대한 포인터입니다. `T`가 `isbits` 타입인 경우, 이 값은 안전하게 변형될 수 있지만, 그렇지 않으면 변형은 엄격히 정의되지 않은 동작입니다.

특별한 경우로, `T = Any`로 설정하면 `Ptr{Any}`로 변환될 때 참조 자체에 대한 포인터가 생성됩니다(불변인 경우 `jl_value_t const* const*`, 그렇지 않으면 `jl_value_t *const *`). `Ptr{Cvoid}`로 변환될 때는 여전히 다른 `T`와 마찬가지로 데이터 영역에 대한 포인터를 반환합니다.

`C_NULL` 인스턴스의 `Ptr`는 초기화하기 위해 `ccall` `Ref` 인수로 전달될 수 있습니다.

# 브로드캐스팅에서의 사용

`Ref`는 때때로 브로드캐스팅에서 참조된 값을 스칼라로 처리하기 위해 사용됩니다.

# 예제

```jldoctest
julia> r = Ref(5) # 초기 값으로 Ref 생성
Base.RefValue{Int64}(5)

julia> r[] # Ref에서 값 가져오기
5

julia> r[] = 7 # Ref에 새 값 저장
7

julia> r # Ref는 이제 7을 포함합니다
Base.RefValue{Int64}(7)

julia> isa.(Ref([1,2,3]), [Array, Dict, Int]) # 브로드캐스팅 중 참조 값을 스칼라로 처리
3-element BitVector:
 1
 0
 0

julia> Ref{Function}()  # 비비트 타입인 Function에 대한 정의되지 않은 참조
Base.RefValue{Function}(#undef)

julia> try
           Ref{Function}()[] # 정의되지 않은 참조를 역참조하면 오류가 발생합니다
       catch e
           println(e)
       end
UndefRefError()

julia> Ref{Int64}()[]; # 비트 타입에 대한 참조는 주어지지 않으면 미정의 값을 참조합니다

julia> isassigned(Ref{Int64}()) # 비트 타입에 대한 참조는 항상 할당됩니다
true
```
