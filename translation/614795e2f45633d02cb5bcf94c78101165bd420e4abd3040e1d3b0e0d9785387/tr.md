# [Documentation](@id man-documentation)

## Accessing Documentation

Belgeler REPL'de veya [IJulia](https://github.com/JuliaLang/IJulia.jl) adresinde erişilebilir. Bir fonksiyon veya makronun adını yazıp `?` tuşuna basarak ve `Enter` tuşuna basarak erişebilirsiniz. Örneğin,

```julia
?cos
?@time
?r""
```

belirli işlev, makro veya dize makrosu için belgeleri gösterecektir. Çoğu Julia ortamı, belgeleri doğrudan erişim sağlama yolu sunar:

  * [VS Code](https://www.julia-vscode.org/) bir işlev adının üzerine geldiğinizde belgeleri gösterir. Ayrıca, belgeleri aramak için yan paneldeki Julia panelini de kullanabilirsiniz.
  * [Pluto](https://github.com/fonsp/Pluto.jl)'de sağ alttaki "Canlı Belgeler" panelini açın.
  * [Juno](https://junolab.org) kullanarak `Ctrl-J, Ctrl-D` ile imlecin altındaki nesne için belgeleri görüntüleyecektir.

`Docs.hasdoc(module, name)::Bool` bir ismin bir dokümana sahip olup olmadığını belirtir. `Docs.undocumented_names(module; all)` bir modüldeki belgelenmemiş isimleri döndürür.

## Writing Documentation

Julia, paket geliştiricileri ve kullanıcıların fonksiyonları, türleri ve diğer nesneleri kolayca belgelemelerini sağlamak için yerleşik bir belgeleme sistemi sunar.

Temel sözdizimi basittir: bir nesnenin (fonksiyon, makro, tür veya örnek) hemen önünde yer alan herhangi bir dize, onu belgelemek için yorumlanacaktır (bunlara *belge dizeleri* denir). Bir belge dizesi ile belgelenen nesne arasında boş satır veya yorum bulunmaması gerektiğini unutmayın. İşte temel bir örnek:

```julia
"Tell whether there are too foo items in the array."
foo(xs::Array) = ...
```

Dokümantasyon [Markdown](https://en.wikipedia.org/wiki/Markdown) olarak yorumlanır, bu nedenle metin ile kod örneklerini ayırmak için girintileme ve kod blokları kullanabilirsiniz. Teknik olarak, herhangi bir nesne herhangi bir diğer nesne ile meta veri olarak ilişkilendirilebilir; Markdown varsayılan olarak bulunur, ancak diğer dize makrolarını oluşturup bunları `@doc` makrosuna da geçirebilirsiniz.

!!! note
    Markdown desteği `Markdown` standart kütüphanesinde uygulanmıştır ve desteklenen sözdizimlerinin tam listesi için [documentation](@ref markdown_stdlib) adresine bakabilirsiniz.


Burada daha karmaşık bir örnek var, hala Markdown kullanarak:

````julia
"""
    bar(x[, y])

Compute the Bar index between `x` and `y`.

If `y` is unspecified, compute the Bar index between all pairs of columns of `x`.

# Examples
```julia-repl
julia> bar([1, 2], [1, 2])
1
```
"""
function bar(x, y) ...
````

Yukarıdaki örnekte olduğu gibi, belgeleri yazarken bazı basit kurallara uymanızı öneririz:

1. Her zaman bir işlevin imzasını belgenin en üstünde gösterin, böylece dört boşlukla girintilenmiş olarak Julia kodu olarak yazdırılır.

    Bu, Julia kodunda bulunan imzaya (örneğin `mean(x::AbstractArray)`) benzer veya basitleştirilmiş bir form olabilir. Opsiyonel argümanlar, mümkün olduğunda varsayılan değerleri ile temsil edilmelidir (yani `f(x, y=1)`), gerçek Julia sözdizimini takip ederek. Varsayılan değeri olmayan opsiyonel argümanlar köşeli parantez içinde belirtilmelidir (yani `f(x[, y])` ve `f(x[, y[, z]])`). Alternatif bir çözüm, opsiyonel argümanlar olmadan bir satır, diğer(leri) ile birlikte olan satırları kullanmaktır. Bu çözüm, belirli bir fonksiyonun birkaç ilgili yöntemini belgelemek için de kullanılabilir. Bir fonksiyon birçok anahtar kelime argümanı kabul ediyorsa, imzada yalnızca `<anahtar kelime argümanları>` yer tutucusunu dahil edin (yani `f(x; <anahtar kelime argümanları>)`), ve tam listeyi `# Argümanlar` bölümünde verin (aşağıdaki 4. maddeye bakın).
2. Tekrar yazın.

    Tek satır cümlesi, fonksiyonları belgelerken üçüncü tekil şahıs yerine emir kipi ("Bunu yap", "Şunu döndür") kullanmalıdır. Cümle bir nokta ile bitmelidir. Bir fonksiyonun anlamı kolayca özetlenemiyorsa, onu ayrı bileşen parçalara ayırmak faydalı olabilir (bu, her durumda mutlak bir gereklilik olarak alınmamalıdır).
3. Kendini tekrarlama.

    Fonksiyon adı imza ile verildiğinden, belgeleri "Fonksiyon `bar`..." ile başlatmaya gerek yoktur: doğrudan konuya geçin. Benzer şekilde, imza argümanların türlerini belirtiyorsa, bunları açıklamada belirtmek gereksizdir.
4. Sadece gerçekten gerekli olduğunda bir argüman listesi sağlayın.

    Basit fonksiyonlar için, genellikle argümanların rolünü doğrudan fonksiyonun amacının tanımında belirtmek daha net olur. Bir argüman listesi, zaten başka bir yerde sağlanan bilgileri yalnızca tekrar eder. Ancak, birçok argümanı (özellikle anahtar kelime argümanları) olan karmaşık fonksiyonlar için bir argüman listesi sağlamak iyi bir fikir olabilir. Bu durumda, genel fonksiyon tanımının ardından, `# Argümanlar` başlığı altında, her argüman için bir `-` madde ile ekleyin. Liste, argümanların türlerini ve varsayılan değerlerini (varsa) belirtmelidir:

    ```julia
    """
    ...
    # Arguments
    - `n::Integer`: the number of elements to compute.
    - `dim::Integer=1`: the dimensions along which to perform the computation.
    ...
    """
    ```
5. Lütfen ilgili işlevlere dair ipuçları sağlayın.

    Bazen ilişkili işlevlerin fonksiyonları vardır. Keşfedilebilirliği artırmak için lütfen bunları içeren kısa bir listeyi `Ayrıca bakınız` paragrafında sağlayın.

    ```
    See also [`bar!`](@ref), [`baz`](@ref), [`baaz`](@ref).
    ```
6. Include any code examples in an `# Examples` section.

    Examples should, whenever possible, be written as *doctests*. A *doctest* is a fenced code block (see [Code blocks](@ref)) starting with ````` ```jldoctest````` and contains any number of `julia>` prompts together with inputs and expected outputs that mimic the Julia REPL.

    !!! note
        Doctests, [`Documenter.jl`](https://github.com/JuliaDocs/Documenter.jl) ile etkinleştirilmiştir. Daha ayrıntılı belgeler için Documenter's [manual](https://juliadocs.github.io/Documenter.jl/) adresine bakın.


    Örneğin, aşağıdaki docstring'de bir `a` değişkeni tanımlanmış ve beklenen sonuç, bir Julia REPL'inde yazdırıldığı gibi, sonrasında görünmektedir:

    ````julia
    """
    Some nice documentation here.

    # Examples
    ```jldoctest
    julia> a = [1 2; 3 4]
    2×2 Array{Int64,2}:
     1  2
     3  4
    ```
    """
    ````

    !!! warning
        `rand` ve diğer RNG ile ilgili fonksiyonların doctest'lerde kullanılmaması gerekir, çünkü farklı Julia oturumları sırasında tutarlı çıktılar üretmeyeceklerdir. Rastgele sayı üretimi ile ilgili bazı işlevsellikleri göstermek istiyorsanız, bir seçenek kendi RNG nesnenizi açıkça oluşturmak ve tohumlamaktır (bkz. [`Random`](@ref Random-Numbers)) ve bunu test ettiğiniz fonksiyonlara iletmektir.

        İşletim sistemi kelime boyutu ([`Int32`](@ref) veya [`Int64`](@ref)) ve yol ayırıcı farklılıkları (`/` veya `\`) bazı doctest'lerin tekrarlanabilirliğini de etkileyecektir.

        Not edin ki, boşluklar doctest'inizde önemlidir! Bir dizinin güzel yazdırılmasının çıktısını yanlış hizalarsanız, doctest başarısız olacaktır.


    `make -C doc doctest=true` komutunu çalıştırarak Julia Kılavuzu ve API belgelerindeki tüm doctest'leri çalıştırabilirsiniz; bu, örneğinizin çalıştığından emin olmanızı sağlar.

    Çıktı sonucunun kesildiğini belirtmek için, kontrolün durması gereken satırda `[...]` yazabilirsiniz. Bu, bir istisnanın atıldığını gösteren doctest'te, julia kodunun satırlarına kalıcı olmayan referanslar içeren bir yığın izini gizlemek için yararlıdır, örneğin:

    ````julia
    ```jldoctest
    julia> div(1, 0)
    ERROR: DivideError: integer division error
    [...]
    ```
    ````

    Örnekler test edilemezse, bunlar üretilen belgelerde doğru bir şekilde vurgulanması için ````` ```julia````` ile başlayan fenced kod blokları içinde yazılmalıdır.

    !!! tip
        Mümkün olduğunda örnekler **kendi başına** ve **çalıştırılabilir** olmalıdır, böylece okuyucular bunları denemek için herhangi bir bağımlılık eklemek zorunda kalmazlar.
7. Kodu ve denklemleri tanımlamak için ters tırnak (`) kullanın.

    Julia tanımlayıcıları ve kod alıntıları her zaman vurgulamayı sağlamak için ters tırnaklar ``` ` ``` arasında görünmelidir. LaTeX sözdizimindeki denklemler çift ters tırnak arasında yerleştirilebilir ``` `` ```. LaTeX kaçış dizeleri yerine Unicode karakterleri kullanılmalıdır, yani ``` ``α = 1`` ``` yerine ``` ``\\alpha = 1`` ```.
8. Place the starting and ending `"""` characters on lines by themselves.

    Bu, yazın:

    ```julia
    """
    ...

    ...
    """
    f(x, y) = ...
    ```

    tercih yerine:

    ```julia
    """...

    ..."""
    f(x, y) = ...
    ```

    Bu, docstring'lerin nerede başladığını ve bittiğini daha net hale getiriyor.
9. Saygı gösterin, çevreleyen kodda kullanılan satır uzunluğu sınırına.

    Docstring'lar, kodla aynı araçlar kullanılarak düzenlenir. Bu nedenle, aynı kurallar geçerli olmalıdır. Satırların en fazla 92 karakter genişliğinde olması önerilir.
10. Provide information allowing custom types to implement the function in an `# Implementation` section. These implementation details are intended for developers rather than users, explaining e.g. which functions should be overridden and which functions automatically use appropriate fallbacks. Such details are best kept separate from the main description of the function's behavior.
11. Uzun docstring'ler için, belgeleri `# Genişletilmiş yardım` başlığı ile ayırmayı düşünün. Tipik yardım modu yalnızca başlığın üzerindeki materyali gösterecektir; tam yardıma erişmek için ifadenin başına '?' ekleyebilirsiniz (yani, "?foo" yerine "??foo").

## Functions & Methods

Julia'da fonksiyonlar birden fazla uygulamaya sahip olabilir, bunlara yöntem denir. Genel fonksiyonların tek bir amaca sahip olması iyi bir uygulama olsa da, Julia gerektiğinde yöntemlerin bireysel olarak belgelenmesine izin verir. Genel olarak, yalnızca en genel yöntem belgelenmelidir veya hatta fonksiyonun kendisi (yani `function bar end` ile oluşturulan nesne). Belirli yöntemler yalnızca davranışları daha genel olanlardan farklıysa belgelenmelidir. Her durumda, başka yerlerde sağlanan bilgileri tekrarlamamalıdırlar. Örneğin:

```julia
"""
    *(x, y, z...)

Multiplication operator. `x * y * z *...` calls this function with multiple
arguments, i.e. `*(x, y, z...)`.
"""
function *(x, y, z...)
    # ... [implementation sold separately] ...
end

"""
    *(x::AbstractString, y::AbstractString, z::AbstractString...)

When applied to strings, concatenates them.
"""
function *(x::AbstractString, y::AbstractString, z::AbstractString...)
    # ... [insert secret sauce here] ...
end

help?> *
search: * .*

  *(x, y, z...)

  Multiplication operator. x * y * z *... calls this function with multiple
  arguments, i.e. *(x,y,z...).

  *(x::AbstractString, y::AbstractString, z::AbstractString...)

  When applied to strings, concatenates them.
```

Genel bir işlev için belgeleri alırken, her bir yöntem için meta veriler `catdoc` işlevi ile birleştirilir; bu, özel türler için elbette geçersiz kılınabilir.

## Advanced Usage

`@doc` makrosu, ilk argümanını ikinci argümanıyla, `META` adlı modül bazlı bir sözlükte ilişkilendirir.

Dokümantasyon yazmayı kolaylaştırmak için, ayrıştırıcı `@doc` makro adını özel bir şekilde işler: Eğer `@doc` çağrısının bir argümanı varsa, ancak bir satır sonrasında başka bir ifade görünüyorsa, o ek ifade makroya bir argüman olarak eklenir. Bu nedenle, aşağıdaki sözdizimi `@doc` için 2-argümanlı bir çağrı olarak ayrıştırılır:

```julia
@doc raw"""
...
"""
f(x) = x
```

Bu, `raw""` dize makrosu gibi normal dize literalleri dışında ifadelerin bir docstring olarak kullanılmasını mümkün kılar.

Dokümantasyonu almak için kullanıldığında, `@doc` makrosu (veya eşit şekilde, `doc` fonksiyonu) verilen nesneyle ilgili meta verileri aramak için tüm `META` sözlüklerini tarar ve bunları döndürür. Döndürülen nesne (örneğin bazı Markdown içeriği) varsayılan olarak kendini akıllıca gösterir. Bu tasarım, dokümantasyon sistemini programatik bir şekilde kullanmayı da kolaylaştırır; örneğin, bir fonksiyonun farklı sürümleri arasında dokümantasyonu yeniden kullanmak için:

```julia
@doc "..." foo!
@doc (@doc foo!) foo
```

Ya da Julia'nın metaprogramlama işlevselliği ile kullanmak için:

```julia
for (f, op) in ((:add, :+), (:subtract, :-), (:multiply, :*), (:divide, :/))
    @eval begin
        $f(a, b) = $op(a, b)
    end
end
@doc "`add(a, b)` adds `a` and `b` together" add
@doc "`subtract(a, b)` subtracts `b` from `a`" subtract
```

Belgelemeler, `begin`, `if`, `for`, `let` ve iç yapıcılar gibi üst düzey olmayan bloklarda da `@doc` aracılığıyla belgeleme sistemine eklenmelidir. Örneğin:

```julia
if condition()
    @doc "..."
    f(x) = x
end
```

`f(x)`'e `condition()` `true` olduğunda belge ekleyeceğim. `f(x)` bir bloğun sonunda kapsam dışına çıksa bile, belgesi kalacaktır.

Metaprogramlama kullanarak belgelerin oluşturulmasına yardımcı olmak mümkündür. Docstring içinde dize yerleştirme kullanırken, `$($name)` ile gösterildiği gibi ekstra bir `$` kullanmanız gerekecektir:

```julia
for func in (:day, :dayofmonth)
    name = string(func)
    @eval begin
        @doc """
            $($name)(dt::TimeType) -> Int64

        The day of month of a `Date` or `DateTime` as an `Int64`.
        """ $func(dt::Dates.TimeType)
    end
end
```

### Dynamic documentation

Bazen bir türün bir örneği için uygun belgeler, yalnızca türün kendisine değil, o örneğin alan değerlerine bağlıdır. Bu durumlarda, özel türünüz için `Docs.getdoc` yöntemine bir yöntem ekleyerek belgeleri örnek bazında döndürebilirsiniz. Örneğin,

```julia
struct MyType
    value::Int
end

Docs.getdoc(t::MyType) = "Documentation for MyType with value $(t.value)"

x = MyType(1)
y = MyType(2)
```

`?x` "MyType için 1 değeri ile belgeleri gösterir" `?y` "MyType için 2 değeri ile belgeleri gösterir".

## Syntax Guide

Bu kılavuz, belgelerin eklenebileceği tüm Julia sözdizim yapıları için belgeleri nasıl ekleyeceğinize dair kapsamlı bir genel bakış sunmaktadır.

Aşağıdaki örneklerde `"..."` bir rastgele docstring'i göstermek için kullanılmıştır.

### `$` and `\` characters

`$` ve `\` karakterleri, docstring'lerde de hala dize interpolasyonu veya bir kaçış dizisi başlangıcı olarak işlenir. `raw""` dize makrosu ile `@doc` makrosu, bunları kaçırmak zorunda kalmadan kullanmak için kullanılabilir. Bu, docstring'lerin LaTeX veya Julia kaynak kodu örnekleri içermesi durumunda kullanışlıdır:

````julia
@doc raw"""
```math
\LaTeX
```
"""
function f end
````

### Functions and Methods

```julia
"..."
function f end

"..."
f
```

Fonksiyona `f` docstring `"..."` ekler. İlk versiyon tercih edilen sözdizimidir, ancak her ikisi de eşdeğerdir.

```julia
"..."
f(x) = x

"..."
function f(x)
    return x
end

"..."
f(x)
```

Yöntem `f(::Any)` için docstring `"..."` ekler.

```julia
"..."
f(x, y = 1) = x + y
```

İki `Method`'a, yani `f(::Any)` ve `f(::Any, ::Any)` için `"..."` docstring'i ekler.

### Macros

```julia
"..."
macro m(x) end
```

`@m(::Any)` makro tanımına `"..."` docstring'i ekler.

```julia
"..."
:(@m1)

"..."
macro m2 end
```

Adds docstring `"..."` to the macros named `@m1` and `@m2`.

### Types

```
"..."
abstract type T1 end

"..."
mutable struct T2
    ...
end

"..."
struct T3
    ...
end
```

`T1`, `T2` ve `T3` türlerine `"..."` docstring'ini ekler.

```
"..."
T1

"..."
T2

"..."
T3
```

T1, T2 ve T3 türlerine `"..."` docstring'ini ekler. Önceki sürüm tercih edilen sözdizimidir, ancak her ikisi de eşdeğerdir.

```julia
"..."
struct T
    "x"
    x
    "y"
    y

    @doc "Inner constructor"
    function T()
        new(...)
    end
end
```

`T` tipine `"..."` docstring'i, `T.x` alanına `"x"`, `T.y` alanına `"y"` ve iç yapıcı `T()` için `"Inner constructor"` ekler. `mutable struct` türleri için de geçerlidir.

### Modules

```julia
"..."
module M end

module M

"..."
M

end
```

`M` modülüne `"..."` docstring'i ekler. Docstring'i modülün üstüne eklemek tercih edilen sözdizimidir, ancak her ikisi de eşdeğerdir.

```julia
"..."
baremodule M
# ...
end

baremodule M

import Base: @doc

"..."
f(x) = x

end
```

`baremodule` bir belgelendirme yaparak, ifadenin üstüne bir docstring yerleştirildiğinde otomatik olarak `@doc` modüle dahil edilir. Modül ifadesi belgelenmediğinde bu ithalatlar manuel olarak yapılmalıdır.

### Global Variables

```julia
"..."
const a = 1

"..."
b = 2

"..."
global c = 3
```

`Binding`'lerin `a`, `b` ve `c`'ye `"..."` docstring'i ekler.

`Binding`ler, bir `Modül`de belirli bir `Sembol`e referans saklamak için kullanılır, referans alınan değeri kendisi saklamadan.

!!! note
    Bir `const` tanımı yalnızca başka bir tanımın takma adını tanımlamak için kullanılıyorsa, örneğin `Base` içindeki `div` fonksiyonu ve onun takma adı `÷` durumunda, takma adı belgelemeyin ve bunun yerine gerçek fonksiyonu belgeleyin.

    Eğer takma ad belgelenmişse ve gerçek tanım değilse, o zaman docsystem (`?` modu) gerçek tanım arandığında takma adla ilişkilendirilmiş docstring'i döndürmeyecektir.

    Örneğin şöyle yazmalısın

    ```julia
    "..."
    f(x) = x + 1
    const alias = f
    ```

    tercih yerine

    ```julia
    f(x) = x + 1
    "..."
    const alias = f
    ```


```julia
"..."
sym
```

`sym` ile ilişkili değere `"..."` docstring'i ekler. Ancak, `sym`'in tanımlandığı yerde belgelenmesi tercih edilir.

### Multiple Objects

```julia
"..."
a, b
```

`a` ve `b`'ye her biri belgelenebilir bir ifade olmalıdır, `"..."` docstring'ini ekler. Bu sözdizimi şuna eşdeğerdir:

```julia
"..."
a

"..."
b
```

Bu şekilde birden fazla ifade birlikte belgelenebilir. Bu sözdizimi, `f` ve `f!` gibi iki işlevin ilişkili olduğu durumlarda yararlı olabilir; örneğin, değiştirmeyen ve değiştiren sürümleri.

### Macro-generated code

```julia
"..."
@m expression
```

`@m` ifadesinin genişletilmesiyle oluşturulan ifadeye `"..."` docstring'i ekler. Bu, `@inline`, `@noinline`, `@generated` veya başka herhangi bir makro ile süslenmiş ifadelerin, süslenmemiş ifadelerle aynı şekilde belgelenmesine olanak tanır.

Makro yazarları, yalnızca tek bir ifade üreten makroların otomatik olarak dokümantasyon dizelerini destekleyeceğini unutmamalıdır. Bir makro, birden fazla alt ifade içeren bir blok döndürüyorsa, belgelenmesi gereken alt ifade [`@__doc__`](@ref Core.@__doc__) makrosu kullanılarak işaretlenmelidir.

[`@enum`](@ref) makrosu, [`Enum`](@ref)'ların belgelenmesine olanak tanımak için `@__doc__` kullanır. Tanımını incelemek, `@__doc__`'u doğru bir şekilde nasıl kullanacağınız konusunda bir örnek olarak hizmet etmelidir.

```@docs
Core.@__doc__
```
