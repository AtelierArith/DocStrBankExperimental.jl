```
@generated f
```

`@generated`는 생성될 함수를 주석 처리하는 데 사용됩니다. 생성된 함수의 본문에서는 인수의 타입만 읽을 수 있으며(값은 읽을 수 없음), 함수는 호출될 때 평가되는 인용된 표현식을 반환합니다. `@generated` 매크로는 전역 범위를 변경하거나 변경 가능한 요소에 의존하는 함수에는 사용해서는 안 됩니다.

자세한 내용은 [메타프로그래밍](@ref)을 참조하세요.

# 예제

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generic function with 1 method)

julia> bar(4)
16

julia> bar("baz")
"baz"
```
