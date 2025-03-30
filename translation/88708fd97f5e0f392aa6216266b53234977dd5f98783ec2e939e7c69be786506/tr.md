# Base.Cartesian

Cartesian modülü, çok boyutlu algoritmalar yazmayı kolaylaştıran makrolar sağlar. Genellikle bu tür algoritmaları [straightforward techniques](https://julialang.org/blog/2016/02/iteration) ile yazabilirsiniz; ancak `Base.Cartesian`'ın hala faydalı veya gerekli olduğu birkaç durum vardır.

## Principles of usage

Kullanımın basit bir örneği:

```julia
@nloops 3 i A begin
    s += @nref 3 A i
end
```

hangi aşağıdaki kodu üretir:

```julia
for i_3 = axes(A, 3)
    for i_2 = axes(A, 2)
        for i_1 = axes(A, 1)
            s += A[i_1, i_2, i_3]
        end
    end
end
```

Genel olarak, Cartesian, bu örnekteki gibi iç içe döngüler gibi tekrarlayan öğeler içeren genel kod yazmanıza olanak tanır. Diğer uygulamalar arasında tekrarlanan ifadeler (örneğin, döngü açma) veya "splat" yapısını (`i...`) kullanmadan değişken sayıda argümanla fonksiyon çağrıları oluşturma yer alır.

## Basic syntax

`@nloops`'un (temel) sözdizimi aşağıdaki gibidir:

  * İlk argüman, döngü sayısını belirten bir tam sayı olmalıdır (*değişken* değil).
  * İkinci argüman, yineleyici değişkeni için kullanılan sembol-ön ekidir. Burada `i` kullandık ve `i_1, i_2, i_3` değişkenleri oluşturuldu.
  * Üçüncü argüman, her bir yineleyici değişkeni için aralığı belirtir. Burada bir değişken (sembol) kullanırsanız, bu `axes(A, dim)` olarak alınır. Daha esnek bir şekilde, aşağıda açıklanan anonim fonksiyon ifade sözdizimini kullanabilirsiniz.
  * Son argüman döngünün gövdesidir. Burada, bu `begin...end` arasında görünen şeydir.

`@nloops`'un bazı ek özellikleri [reference section](@ref dev-cartesian-reference)'de açıklanmıştır.

`@nref`, benzer bir deseni takip eder ve `@nref 3 A i` ifadesinden `A[i_1,i_2,i_3]` üretir. Genel uygulama soldan sağa okumaktır, bu yüzden `@nloops` ifadesi `@nloops 3 i A expr` şeklindedir (örneğin `for i_2 = axes(A, 2)`, burada `i_2` solda ve aralık sağdadır) oysa `@nref` ifadesi `@nref 3 A i` şeklindedir (örneğin `A[i_1,i_2,i_3]`, burada dizi önce gelir).

Eğer Cartesian ile kod geliştiriyorsanız, oluşturulan kodu inceleyerek hata ayıklamanın daha kolay olduğunu görebilirsiniz, `@macroexpand` kullanarak:

```@meta
DocTestSetup = quote
    import Base.Cartesian: @nref
end
```

```jldoctest
julia> @macroexpand @nref 2 A i
:(A[i_1, i_2])
```

```@meta
DocTestSetup = nothing
```

### Supplying the number of expressions

Bu makroların her ikisine de ilk argüman, bir tam sayı olması gereken ifade sayısıdır. Birden fazla boyutta çalışmasını istediğiniz bir fonksiyon yazarken, bu durumu sabit kodlamak istemeyebilirsiniz. Önerilen yaklaşım, bir `@generated function` kullanmaktır. İşte bir örnek:

```julia
@generated function mysum(A::Array{T,N}) where {T,N}
    quote
        s = zero(T)
        @nloops $N i A begin
            s += @nref $N A i
        end
        s
    end
end
```

Doğal olarak, `quote` bloğundan önce ifadeler hazırlayabilir veya hesaplamalar yapabilirsiniz.

### Anonymous-function expressions as macro arguments

Belki de `Cartesian`'ın en güçlü özelliği, anonim fonksiyon ifadeleri sağlamanın ve bunların ayrıştırma zamanında değerlendirilmesinin mümkün olmasıdır. Basit bir örneği ele alalım:

```julia
@nexprs 2 j->(i_j = 1)
```

`@nexprs` `n` ifadeleri üreten bir yapıdır. Bu kod aşağıdaki ifadeleri üretecektir:

```julia
i_1 = 1
i_2 = 1
```

Her üretilen ifadede, "izole" bir `j` (anonim fonksiyonun değişkeni) `1:2` aralığındaki değerlerle değiştirilir. Genel olarak, Cartesian LaTeX benzeri bir sözdizimi kullanır. Bu, `j` indeksinde matematik yapmanıza olanak tanır. İşte bir dizinin adımlarını hesaplayan bir örnek:

```julia
s_1 = 1
@nexprs 3 j->(s_{j+1} = s_j * size(A, j))
```

ifade üretecek

```julia
s_1 = 1
s_2 = s_1 * size(A, 1)
s_3 = s_2 * size(A, 2)
s_4 = s_3 * size(A, 3)
```

Anonim fonksiyon ifadelerinin pratikte birçok kullanımı vardır.

#### [Macro reference](@id dev-cartesian-reference)

```@docs
Base.Cartesian.@nloops
Base.Cartesian.@nref
Base.Cartesian.@nextract
Base.Cartesian.@nexprs
Base.Cartesian.@ncall
Base.Cartesian.@ncallkw
Base.Cartesian.@ntuple
Base.Cartesian.@nall
Base.Cartesian.@nany
Base.Cartesian.@nif
```
