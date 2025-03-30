```
@with (var::ScopedValue{T} => val)... expr
```

`with` makrosu. `@with var=>val expr` ifadesi, `var`'ı `val` olarak ayarlayarak yeni bir dinamik kapsamda `expr`'i değerlendirir. `val`, `T` türüne dönüştürülecektir. `@with var=>val expr`, `with(var=>val) do expr end` ile eşdeğerdir, ancak `@with` bir kapanış oluşturmaktan kaçınır.

Ayrıca bakınız: [`ScopedValues.with`](@ref), [`ScopedValues.ScopedValue`](@ref), [`ScopedValues.get`](@ref).

# Örnekler

```jldoctest
julia> using Base.ScopedValues

julia> const a = ScopedValue(1);

julia> f(x) = a[] + x;

julia> @with a=>2 f(10)
12

julia> @with a=>3 begin
           x = 100
           f(x)
       end
103
```
