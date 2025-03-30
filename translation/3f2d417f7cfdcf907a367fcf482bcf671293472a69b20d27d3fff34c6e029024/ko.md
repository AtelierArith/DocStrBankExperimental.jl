```
struct
```

Julia에서 가장 일반적으로 사용되는 유형은 이름과 필드 집합으로 지정된 struct입니다.

```julia
struct Point
    x
    y
end
```

필드는 유형 제한을 가질 수 있으며, 이는 매개변수화될 수 있습니다:

```julia
struct Point{X}
    x::X
    y::Float64
end
```

struct는 `<:` 구문을 통해 추상 슈퍼 유형을 선언할 수도 있습니다:

```julia
struct Point <: AbstractPoint
    x
    y
end
```

`struct`는 기본적으로 불변입니다; 이러한 유형의 인스턴스는 생성 후 수정할 수 없습니다. 인스턴스를 수정할 수 있는 유형을 선언하려면 [`mutable struct`](@ref)를 대신 사용하십시오.

생성자 정의와 같은 더 많은 세부정보는 [Composite Types](@ref) 매뉴얼 섹션을 참조하십시오.
