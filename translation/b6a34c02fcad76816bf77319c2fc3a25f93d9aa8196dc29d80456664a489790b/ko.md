```
let
```

`let` 블록은 새로운 하드 스코프를 생성하고 선택적으로 새로운 로컬 바인딩을 도입합니다.

다른 스코프 구성 요소와 마찬가지로, `let` 블록은 새로 도입된 로컬 변수가 접근 가능한 코드 블록을 정의합니다. 또한, 구문은 쉼표로 구분된 할당 및 `let`과 같은 줄에 선택적으로 나타날 수 있는 변수 이름에 대해 특별한 의미를 가집니다:

```julia
let var1 = value1, var2, var3 = value3
    code
end
```

이 줄에서 도입된 변수는 `let` 블록에 로컬이며, 할당은 순서대로 평가되며, 각 오른쪽 항은 왼쪽 항의 이름을 고려하지 않고 스코프 내에서 평가됩니다. 따라서 `let x = x`와 같은 것을 작성하는 것이 의미가 있습니다. 두 `x` 변수는 서로 다르며, 왼쪽 항이 외부 스코프의 `x`를 로컬로 가리는 것입니다. 이는 로컬 스코프에 들어갈 때마다 새 로컬 변수가 새로 생성되기 때문에 유용한 관용구가 될 수 있지만, 이는 클로저를 통해 스코프를 초과하는 변수가 있는 경우에만 관찰할 수 있습니다. 위의 예에서 `var2`와 같이 할당이 없는 `let` 변수는 아직 값에 바인딩되지 않은 새로운 로컬 변수를 선언합니다.

대조적으로, [`begin`](@ref) 블록은 여러 표현식을 함께 그룹화하지만 스코프를 도입하거나 특별한 할당 구문을 가지지 않습니다.

### 예제

아래 함수에서는 `map`에 의해 세 번 반복적으로 업데이트되는 단일 `x`가 있습니다. 반환된 클로저는 모두 최종 값에서 그 하나의 `x`를 참조합니다:

```jldoctest
julia> function test_outer_x()
           x = 0
           map(1:3) do _
               x += 1
               return ()->x
           end
       end
test_outer_x (generic function with 1 method)

julia> [f() for f in test_outer_x()]
3-element Vector{Int64}:
 3
 3
 3
```

그러나 새로운 로컬 변수를 도입하는 `let` 블록을 추가하면, 같은 이름을 사용하기로 선택했음에도 불구하고 각 반복에서 캡처되는 세 개의 서로 다른 변수가 생깁니다.

```jldoctest
julia> function test_let_x()
           x = 0
           map(1:3) do _
               x += 1
               let x = x
                   return ()->x
               end
           end
       end
test_let_x (generic function with 1 method)

julia> [f() for f in test_let_x()]
3-element Vector{Int64}:
 1
 2
 3
```

새로운 로컬 변수를 도입하는 모든 스코프 구성 요소는 반복적으로 실행될 때 이렇게 동작합니다. `let`의 특징은 동일한 이름의 외부 변수를 가릴 수 있는 새로운 `local`을 간결하게 선언할 수 있는 능력입니다. 예를 들어, `do` 함수의 인수를 직접 사용하면 세 개의 서로 다른 변수를 캡처합니다:

```jldoctest
julia> function test_do_x()
           map(1:3) do x
               return ()->x
           end
       end
test_do_x (generic function with 1 method)

julia> [f() for f in test_do_x()]
3-element Vector{Int64}:
 1
 2
 3
```
