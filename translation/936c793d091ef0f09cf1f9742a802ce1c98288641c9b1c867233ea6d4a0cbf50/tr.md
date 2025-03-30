```
getproperty(value, name::Symbol)
getproperty(value, name::Symbol, order::Symbol)
```

`a.b` sözdizimi `getproperty(a, :b)` çağrısını yapar. `@atomic order a.b` sözdizimi `getproperty(a, :b, :order)` çağrısını yapar ve `@atomic a.b` sözdizimi `getproperty(a, :b, :sequentially_consistent)` çağrısını yapar.

# Örnekler

```jldoctest
julia> struct MyType{T <: Number}
           x::T
       end

julia> function Base.getproperty(obj::MyType, sym::Symbol)
           if sym === :special
               return obj.x + 1
           else # getfield'e geri dön
               return getfield(obj, sym)
           end
       end

julia> obj = MyType(1);

julia> obj.special
2

julia> obj.x
1
```

`getproperty` yalnızca gerekli olduğunda aşırı yüklenmelidir, çünkü `obj.f` sözdiziminin davranışı alışılmadık olduğunda kafa karıştırıcı olabilir. Ayrıca, yöntemlerin kullanımı genellikle tercih edilir. Daha fazla bilgi için bu stil kılavuzu belgesine bakın: [Doğrudan alan erişimi yerine dışa aktarılan yöntemleri tercih edin](@ref).

Ayrıca [`getfield`](@ref Core.getfield), [`propertynames`](@ref Base.propertynames) ve [`setproperty!`](@ref Base.setproperty!) ile ilgili bilgilere de bakın.
