```
setfield!(value, name::Symbol, x, [order::Symbol])
setfield!(value, i::Int, x, [order::Symbol])
```

`value`의 명명된 필드에 `x`를 할당합니다. `value`는 변경 가능해야 하며, `x`는 `fieldtype(typeof(value), name)`의 하위 유형이어야 합니다. 또한 이 작업에 대한 순서를 지정할 수 있습니다. 필드가 `@atomic`으로 선언된 경우, 이 사양은 필수입니다. 그렇지 않으면 `@atomic`으로 선언되지 않은 경우, 지정된 경우 `:not_atomic`이어야 합니다. [`setproperty!`](@ref Base.setproperty!)도 참조하십시오.

# 예제

```jldoctest
julia> mutable struct MyMutableStruct
           field::Int
       end

julia> a = MyMutableStruct(1);

julia> setfield!(a, :field, 2);

julia> getfield(a, :field)
2

julia> a = 1//2
1//2

julia> setfield!(a, :num, 3);
ERROR: setfield!: immutable struct of type Rational cannot be changed
```
