```
GC.@preserve x1 x2 ... xn expr
```

객체 `x1, x2, ...`를 표현식 `expr`의 평가 중에 *사용 중*으로 표시합니다. 이는 `expr`이 `x` 중 하나가 소유한 메모리 또는 기타 자원을 *암묵적으로 사용*하는 안전하지 않은 코드에서만 필요합니다.

`x`의 *암묵적 사용*은 컴파일러가 볼 수 없는 `x`가 논리적으로 소유한 자원의 간접적인 사용을 포함합니다. 몇 가지 예는 다음과 같습니다:

  * `Ptr`를 통해 객체의 메모리에 직접 접근하기
  * `ccall`에 `x`의 포인터 전달하기
  * 최종화기에서 정리될 `x`의 자원 사용하기

`@preserve`는 일반적으로 객체 수명을 잠시 연장하는 전형적인 사용 사례에서 성능에 영향을 미치지 않아야 합니다. 구현에서 `@preserve`는 동적으로 할당된 객체를 가비지 수집으로부터 보호하는 등의 효과를 가집니다.

# 예제

`unsafe_load`로 포인터에서 로드할 때, 기본 객체가 암묵적으로 사용됩니다. 예를 들어, 다음에서 `unsafe_load(p)`에 의해 `x`가 암묵적으로 사용됩니다:

```jldoctest
julia> let
           x = Ref{Int}(101)
           p = Base.unsafe_convert(Ptr{Int}, x)
           GC.@preserve x unsafe_load(p)
       end
101
```

`ccall`에 포인터를 전달할 때, 가리키는 객체가 암묵적으로 사용되며 보존되어야 합니다. (그러나 일반적으로 `x`를 `ccall`에 직접 전달하는 것이 명시적 사용으로 간주되므로 선호됩니다.)

```jldoctest
julia> let
           x = "Hello"
           p = pointer(x)
           Int(GC.@preserve x @ccall strlen(p::Cstring)::Csize_t)
           # 선호되는 대안
           Int(@ccall strlen(x::Cstring)::Csize_t)
       end
5
```
