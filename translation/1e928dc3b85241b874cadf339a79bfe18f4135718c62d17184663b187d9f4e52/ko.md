```
code_typed(f, types; kw...)
```

주어진 일반 함수와 타입 서명에 맞는 메서드의 타입 추론된 낮은 형태(IR)의 배열을 반환합니다.

# 키워드 인수

  * `optimize::Bool = true`: 선택적, 인라인과 같은 추가 최적화가 적용되는지 여부를 제어합니다.
  * `debuginfo::Symbol = :default`: 선택적, 출력에 존재하는 코드 메타데이터의 양을 제어하며, 가능한 옵션은 `:source` 또는 `:none`입니다.

# 내부 키워드 인수

이 섹션은 내부적으로 간주되어야 하며, Julia 컴파일러 내부를 이해하는 사람만을 위한 것입니다.

  * `world::UInt = Base.get_world_counter()`: 선택적, 메서드를 조회할 때 사용할 세계의 나이를 제어하며, 지정하지 않으면 현재 세계의 나이를 사용합니다.
  * `interp::Core.Compiler.AbstractInterpreter = Core.Compiler.NativeInterpreter(world)`: 선택적, 사용할 추상 인터프리터를 제어하며, 지정하지 않으면 네이티브 인터프리터를 사용합니다.

# 예제

인수 타입을 튜플에 넣어 해당 `code_typed`를 얻을 수 있습니다.

```julia
julia> code_typed(+, (Float64, Float64))
1-element Vector{Any}:
 CodeInfo(
1 ─ %1 = Base.add_float(x, y)::Float64
└──      return %1
) => Float64
```
