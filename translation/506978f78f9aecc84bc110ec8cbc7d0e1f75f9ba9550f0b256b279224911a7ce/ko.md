# Reflection and introspection

줄리아는 다양한 런타임 반사 기능을 제공합니다.

## Module bindings

`Module`의 공개 이름은 [`names(m::Module)`](@ref)를 사용하여 확인할 수 있으며, 이는 공개 바인딩을 나타내는 [`Symbol`](@ref) 요소의 배열을 반환합니다. `names(m::Module, all = true)`는 공개 상태에 관계없이 `m`의 모든 바인딩에 대한 기호를 반환합니다.

## DataType fields

`DataType` 필드의 이름은 [`fieldnames`](@ref)를 사용하여 조회할 수 있습니다. 예를 들어, 다음 유형이 주어지면 `fieldnames(Point)`는 필드 이름을 나타내는 [`Symbol`](@ref)의 튜플을 반환합니다:

```jldoctest struct_point
julia> struct Point
           x::Int
           y
       end

julia> fieldnames(Point)
(:x, :y)
```

`Point` 객체의 각 필드 유형은 `Point` 변수 자체의 `types` 필드에 저장됩니다:

```jldoctest struct_point
julia> Point.types
svec(Int64, Any)
```

`x`는 `Int`로 주석이 달려 있지만, `y`는 타입 정의에서 주석이 없으므로 `y`는 기본적으로 `Any` 타입이 됩니다.

유형은 `DataType`이라고 하는 구조체로 표현됩니다:

```jldoctest struct_point
julia> typeof(Point)
DataType
```

`fieldnames(DataType)`는 `DataType` 자체의 각 필드 이름을 제공하며, 이 필드 중 하나가 위의 예에서 관찰된 `types` 필드입니다.

## Subtypes

`DataType`의 *직접* 하위 유형은 [`subtypes`](@ref)를 사용하여 나열할 수 있습니다. 예를 들어, 추상 `DataType` [`AbstractFloat`](@ref)는 네 개의 (구체적인) 하위 유형을 가지고 있습니다:

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.subtypes(AbstractFloat)
5-element Vector{Any}:
 BigFloat
 Core.BFloat16
 Float16
 Float32
 Float64
```

이 목록에는 모든 추상 하위 유형도 포함되지만, 그 하위 유형은 포함되지 않습니다; [`subtypes`](@ref)의 재귀적 적용을 통해 전체 유형 트리를 검사할 수 있습니다.

[`subtypes`](@ref)는 [`InteractiveUtils`](@ref man-interactive-utils) 내부에 위치하지만, REPL을 사용할 때 자동으로 내보내집니다.

## DataType layout

`DataType`의 내부 표현은 C 코드와 인터페이스할 때 매우 중요하며, 이러한 세부 정보를 검사할 수 있는 여러 함수가 제공됩니다. [`isbitstype(T::DataType)`](@ref)는 `T`가 C 호환 정렬로 저장되어 있으면 true를 반환합니다. [`fieldoffset(T::DataType, i::Integer)`](@ref)는 필드 *i*의 (바이트) 오프셋을 타입의 시작에 상대적으로 반환합니다.

## Function methods

어떤 일반 함수의 메서드는 [`methods`](@ref)를 사용하여 나열할 수 있습니다. 주어진 유형을 수용하는 메서드를 찾기 위해 메서드 디스패치 테이블을 검색할 수 있습니다 [`methodswith`](@ref).

## Expansion and lowering

As discussed in the [Metaprogramming](@ref) section, the [`macroexpand`](@ref) function gives the unquoted and interpolated expression ([`Expr`](@ref)) form for a given macro. To use `macroexpand`, `quote` the expression block itself (otherwise, the macro will be evaluated and the result will be passed instead!). For example:

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.macroexpand(@__MODULE__, :(@edit println("")) )
:(InteractiveUtils.edit(println, (Base.typesof)("")))
```

함수 `Base.Meta.show_sexpr`와 [`dump`](@ref)는 모든 표현식에 대해 S-표현식 스타일 보기와 깊이 중첩된 세부 정보 보기를 표시하는 데 사용됩니다.

마침내, [`Meta.lower`](@ref) 함수는 모든 표현식의 `lowered` 형태를 제공하며, 이는 언어 구조가 할당, 분기 및 호출과 같은 원시 작업에 어떻게 매핑되는지를 이해하는 데 특히 중요합니다:

```jldoctest; setup = (using Base: +, sin)
julia> Meta.lower(@__MODULE__, :( [1+2, sin(0.5)] ))
:($(Expr(:thunk, CodeInfo(
    @ none within `top-level scope`
1 ─ %1 = 1 + 2
│   %2 = sin(0.5)
│   %3 = Base.vect(%1, %2)
└──      return %3
))))
```

## Intermediate and compiled representations

함수를 위한 낮춘 형태를 검사하려면, 특정 방법을 선택하여 표시해야 합니다. 일반 함수는 서로 다른 타입 서명을 가진 여러 방법을 가질 수 있기 때문입니다. 이 목적을 위해, 방법별 코드 낮추기가 [`code_lowered`](@ref)를 사용하여 가능합니다. 타입 추론된 형태는 [`code_typed`](@ref)를 사용하여 이용할 수 있습니다. [`code_warntype`](@ref)는 `4d61726b646f776e2e436f64652822222c2022636f64655f74797065642229_40726566`의 출력에 하이라이팅을 추가합니다.

기계에 더 가까운 LLVM 중간 표현은 [`code_llvm`](@ref)를 사용하여 인쇄할 수 있으며, 마지막으로 컴파일된 기계 코드는 [`code_native`](@ref)를 사용하여 사용할 수 있습니다(이는 이전에 호출되지 않은 모든 함수에 대해 JIT 컴파일/코드 생성을 트리거합니다).

편의를 위해 위의 함수들의 매크로 버전이 있으며, 이는 표준 함수 호출을 받아들이고 인수 유형을 자동으로 확장합니다:

```julia-repl
julia> @code_llvm +(1,1)
;  @ int.jl:87 within `+`
; Function Attrs: sspstrong uwtable
define i64 @"julia_+_476"(i64 signext %0, i64 signext %1) #0 {
top:
  %2 = add i64 %1, %0
  ret i64 %2
}
```

자세한 내용은 [`@code_lowered`](@ref), [`@code_typed`](@ref), [`@code_warntype`](@ref), [`@code_llvm`](@ref), 및 [`@code_native`](@ref)를 참조하십시오.

### Printing of debug information

앞서 언급한 함수와 매크로는 출력되는 디버그 정보의 수준을 제어하는 키워드 인수 `debuginfo`를 사용합니다.

```jldoctest; setup = :(using InteractiveUtils), filter = r"int.jl:\d+"
julia> InteractiveUtils.@code_typed debuginfo=:source +(1,1)
CodeInfo(
    @ int.jl:87 within `+`
1 ─ %1 = Base.add_int(x, y)::Int64
└──      return %1
) => Int64
```

`debuginfo`의 가능한 값은 `:none`, `:source`, `:default`입니다. 기본적으로 디버그 정보는 출력되지 않지만, `Base.IRShow.default_debuginfo[] = :source`를 설정하면 변경할 수 있습니다.
