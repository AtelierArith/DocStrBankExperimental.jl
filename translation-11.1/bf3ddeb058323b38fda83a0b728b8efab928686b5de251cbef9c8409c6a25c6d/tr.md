```
@nospecialize
```

Bir fonksiyon argümanı adına uygulandığında, derleyiciye o argümanın farklı türler için özelleştirilmemesi gerektiğini, bunun yerine o argüman için belirtilen türün kullanılmasını belirtir. Bu, bir resmi argüman listesi içindeki bir argümana veya fonksiyon gövdesinde uygulanabilir. Bir argümana uygulandığında, makro tüm argüman ifadesini sarmalıdır, örneğin, `@nospecialize(x::Real)` veya `@nospecialize(i::Integer...)` şeklinde, yalnızca argüman adını sarmak yerine. Fonksiyon gövdesinde kullanıldığında, makro, herhangi bir koddan önce ve ifade konumunda yer almalıdır.

Argüman olmadan kullanıldığında, üst kapsamın tüm argümanlarına uygulanır. Yerel kapsamda, bu, içindeki fonksiyonun tüm argümanları anlamına gelir. Küresel (en üst düzey) kapsamda, bu, mevcut modülde daha sonra tanımlanan tüm yöntemler anlamına gelir.

Özelleştirme, [`@specialize`](@ref) kullanılarak varsayılan duruma sıfırlanabilir.

```julia
function example_function(@nospecialize x)
    ...
end

function example_function(x, @nospecialize(y = 1))
    ...
end

function example_function(x, y, z)
    @nospecialize x y
    ...
end

@nospecialize
f(y) = [x for x in y]
@specialize
```

!!! not
    `@nospecialize` kod üretimini etkiler ancak çıkarımı etkilemez: sonuçlanan yerel kodun çeşitliliğini sınırlar, ancak tür çıkarımı üzerinde (standart olanlar dışında) herhangi bir kısıtlama getirmez. Çıkarımı ayrıca bastırmak için [`Base.@nospecializeinfer`](@ref) ile birlikte `@nospecialize` kullanın.


# Örnekler

```julia
julia> f(A::AbstractArray) = g(A)
f (generic function with 1 method)

julia> @noinline g(@nospecialize(A::AbstractArray)) = A[1]
g (generic function with 1 method)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Float64
└──      return %1
) => Float64
```

Burada, `@nospecialize` notasyonu, aşağıdakinin eşdeğeri olan bir sonuç verir:

```julia
f(A::AbstractArray) = invoke(g, Tuple{AbstractArray}, A)
```

Bu, `g` için yalnızca bir yerel kod versiyonunun üretilmesini sağlar, bu da herhangi bir `AbstractArray` için genel olanıdır. Ancak, belirli dönüş türü hala hem `g` hem de `f` için çıkarılır ve bu, `f` ve `g`'nin çağrıcılarını optimize etmede hala kullanılır.
