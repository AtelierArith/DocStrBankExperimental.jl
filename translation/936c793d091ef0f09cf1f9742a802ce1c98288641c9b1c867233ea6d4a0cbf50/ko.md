```
getproperty(value, name::Symbol)
getproperty(value, name::Symbol, order::Symbol)
```

구문 `a.b`는 `getproperty(a, :b)`를 호출합니다. 구문 `@atomic order a.b`는 `getproperty(a, :b, :order)`를 호출하고, 구문 `@atomic a.b`는 `getproperty(a, :b, :sequentially_consistent)`를 호출합니다.

# 예제

```jldoctest
julia> struct MyType{T <: Number}
           x::T
       end

julia> function Base.getproperty(obj::MyType, sym::Symbol)
           if sym === :special
               return obj.x + 1
           else # fallback to getfield
               return getfield(obj, sym)
           end
       end

julia> obj = MyType(1);

julia> obj.special
2

julia> obj.x
1
```

`getproperty`는 필요할 때만 오버로드해야 하며, `obj.f` 구문의 동작이 비정상적일 경우 혼란스러울 수 있습니다. 또한 메서드를 사용하는 것이 종종 더 바람직하다는 점에 유의하세요. 더 많은 정보는 이 스타일 가이드 문서를 참조하세요: [직접 필드 접근보다 내보낸 메서드를 선호](@ref).

또한 [`getfield`](@ref Core.getfield), [`propertynames`](@ref Base.propertynames) 및 [`setproperty!`](@ref Base.setproperty!)를 참조하세요.
