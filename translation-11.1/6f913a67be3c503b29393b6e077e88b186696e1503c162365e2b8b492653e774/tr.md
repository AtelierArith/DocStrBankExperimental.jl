```
size(A::AbstractArray, [dim])
```

`A`'nın boyutlarını içeren bir demet döndürür. İsteğe bağlı olarak, yalnızca o boyutun uzunluğunu almak için bir boyut belirtebilirsiniz.

`size`'in standart dışı indekslere sahip diziler için tanımlı olmayabileceğini unutmayın; bu durumda [`axes`](@ref) yararlı olabilir. [Özel indekslere sahip diziler](@ref man-custom-indices) konusundaki kılavuz bölümüne bakın.

Ayrıca bakınız: [`length`](@ref), [`ndims`](@ref), [`eachindex`](@ref), [`sizeof`](@ref).

# Örnekler

```jldoctest
julia> A = fill(1, (2,3,4));

julia> size(A)
(2, 3, 4)

julia> size(A, 2)
3
```
