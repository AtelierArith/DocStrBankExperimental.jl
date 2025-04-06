# Julia Functions

Bu belge, fonksiyonların, yöntem tanımlarının ve yöntem tablolarının nasıl çalıştığını açıklayacaktır.

## Method Tables

Herhangi bir işlev Julia'da genel bir işlevdir. Genel bir işlev, kavramsal olarak tek bir işlevdir, ancak birçok tanım veya yöntemden oluşur. Genel bir işlevin yöntemleri bir yöntem tablosunda saklanır. Yöntem tabloları (tip `MethodTable`) `TypeName` ile ilişkilidir. Bir `TypeName`, parametreli türlerin bir ailesini tanımlar. Örneğin, `Complex{Float32}` ve `Complex{Float64}` aynı `Complex` tür adı nesnesini paylaşır.

Tüm nesneler Julia'da potansiyel olarak çağrılabilir, çünkü her nesnenin bir türü vardır ve bu türün de bir `TypeName`'i vardır.

## [Function calls](@id Function-calls)

Verilen `f(x, y)` çağrısı ile aşağıdaki adımlar gerçekleştirilir: ilk olarak, kullanılacak yöntem tablosuna `typeof(f).name.mt` olarak erişilir. İkinci olarak, bir argüman demeti türü oluşturulur, `Tuple{typeof(f), typeof(x), typeof(y)}`. Fonksiyonun kendisinin türü ilk öğe olarak yer alır. Bunun nedeni, türün parametreleri olabileceği ve bu nedenle dağıtımda yer alması gerektiğidir. Bu demet türü yöntem tablosunda aranır.

Bu dağıtım süreci, `jl_apply_generic` tarafından gerçekleştirilir ve iki argüman alır: `f`, `x` ve `y` değerlerinin bir diziye işaretçisi ve değerlerin sayısı (bu durumda 3).

Sistem boyunca, işlevleri ve argüman listelerini yöneten iki tür API vardır: işlevi ve argümanları ayrı ayrı kabul edenler ve tek bir argüman yapısını kabul edenler. İlk tür API'de, "argümanlar" kısmı *işlev* hakkında bilgi içermez, çünkü bu ayrı olarak iletilir. İkinci tür API'de ise, işlev argüman yapısının ilk elemanıdır.

Örneğin, bir çağrı gerçekleştiren aşağıdaki fonksiyon yalnızca bir `args` işaretçisi alır, bu nedenle args dizisinin ilk öğesi çağrılacak fonksiyon olacaktır:

```c
jl_value_t *jl_apply(jl_value_t **args, uint32_t nargs)
```

Bu giriş noktası aynı işlevsellik için fonksiyonu ayrı olarak kabul eder, bu nedenle `args` dizisi fonksiyonu içermez:

```c
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs);
```

## Adding methods

Verilen yukarıdaki dağıtım sürecine göre, yeni bir yöntem eklemek için konsept olarak gerekenler (1) bir demet türü ve (2) yöntemin gövdesi için koddur. `jl_method_def` bu işlemi uygular. İlk argümanın türü ne olursa olsun ilgili yöntem tablosunu çıkarmak için `jl_method_table_for` çağrılır. Bu, dağıtım sırasında karşılık gelen prosedürden çok daha karmaşıktır, çünkü argüman demet türü soyut olabilir. Örneğin, tanımlayabiliriz:

```julia
(::Union{Foo{Int},Foo{Int8}})(x) = 0
```

hangi yöntemlerin aynı yöntem tablosuna ait olacağı için çalışır.

## Creating generic functions

Herhangi bir nesne çağrılabilir olduğundan, genel bir işlev oluşturmak için özel bir şey gerekmiyor. Bu nedenle `jl_new_generic_function` basitçe yeni bir singleton (0 boyut) `Function` alt türü oluşturur ve örneğini döndürür. Bir işlev, hata ayıklama bilgileri ve nesneleri yazdırırken kullanılan bir mnemonik "görüntü adı"na sahip olabilir. Örneğin, `Base.sin`'in adı `sin`dir. Geleneksel olarak, oluşturulan *tipin* adı, işlev adının önüne bir `#` eklenerek aynı olur. Yani `typeof(sin)` `Base.#sin`dir.

## Closures

Bir kapanış, yakalanan değişkenlere karşılık gelen alan adlarına sahip çağrılabilir bir nesnedir. Örneğin, aşağıdaki kod:

```julia
function adder(x)
    return y->x+y
end
```

yaklaşık olarak düşürülmüştür:

```julia
struct ##1{T}
    x::T
end

(_::##1)(y) = _.x + y

function adder(x)
    return ##1(x)
end
```

## Constructors

Bir yapıcı çağrısı, bir tür çağrısıdır. `Type` için yöntem tablosu, tüm yapıcı tanımlarını içerir. `Type`, `UnionAll`, `Union` ve `DataType` türlerinin tümü, özel bir düzenleme aracılığıyla şu anda bir yöntem tablosunu paylaşmaktadır.

## Builtins

`Core` modülünde tanımlanan "builtin" fonksiyonlar şunlardır:

```@eval
function lines(words)
    io = IOBuffer()
    n = 0
    for w in words
        if n+length(w) > 80
            print(io, '\n', w)
            n = length(w)
        elseif n == 0
            print(io, w);
            n += length(w)
        else
            print(io, ' ', w);
            n += length(w)+1
        end
    end
    String(take!(io))
end
import Markdown
[string(n) for n in names(Core;all=true)
    if getfield(Core,n) isa Core.Builtin && nameof(getfield(Core,n)) === n] |>
    lines |>
    s ->  "```\n$s\n```" |>
    Markdown.parse
```

Bunlar, `Function`'ın bir alt türü olan `Builtin` türünün alt türleri olan tüm tekil nesnelerdir. Amaçları, "jlcall" çağrı konvansiyonunu kullanan çalışma zamanında giriş noktalarını açmaktır:

```c
jl_value_t *(jl_value_t*, jl_value_t**, uint32_t)
```

Yer built-in yöntem tabloları boştur. Bunun yerine, doğru işlevi işaret eden bir tek genel yöntem önbellek girişi (`Tuple{Vararg{Any}}`) vardır. Bu bir tür hile ama oldukça iyi çalışıyor.

## Keyword arguments

Anahtar kelime argümanları, kwcall fonksiyonuna yöntemler ekleyerek çalışır. Bu fonksiyon genellikle "anahtar kelime argüman sıralayıcı" veya "anahtar kelime sıralayıcı" olarak adlandırılır ve ardından fonksiyonun iç gövdesini (anonim olarak tanımlanmış) çağırır. Kwsorter fonksiyonundaki her tanım, normal yöntem tablosundaki bazı tanımlarla aynı argümanlara sahiptir, ancak önüne eklenmiş tek bir `NamedTuple` argümanı vardır; bu, geçirilen anahtar kelime argümanlarının adlarını ve değerlerini verir. Kwsorter'ın görevi, anahtar kelime argümanlarını isimlerine göre kanonik konumlarına taşımak ve gerekli varsayılan değer ifadelerini değerlendirmek ve yerine koymaktır. Sonuç, daha sonra başka bir derleyici tarafından üretilen fonksiyona geçirilen normal bir konumsal argüman listesidir.

En kolay yol, bir anahtar kelime argümanı yöntem tanımının nasıl düşürüldüğünü görmek için süreci anlamaktır. Kod:

```julia
function circle(center, radius; color = black, fill::Bool = true, options...)
    # draw
end
```

aslında *üç* yöntem tanımı üretir. İlki, tüm argümanları (anahtar kelime argümanları dahil) konumsal argümanlar olarak kabul eden bir işlevdir ve yöntem gövdesi için kodu içerir. Otomatik olarak oluşturulmuş bir adı vardır:

```julia
function #circle#1(color, fill::Bool, options, circle, center, radius)
    # draw
end
```

İkinci yöntem, hiçbir anahtar kelime argümanı geçilmediği durumu ele alan orijinal `circle` fonksiyonu için sıradan bir tanımdır:

```julia
function circle(center, radius)
    #circle#1(black, true, pairs(NamedTuple()), circle, center, radius)
end
```

Bu, varsayılan değerleri ile birlikte ilk metoda yönlendirir. `pairs`, anahtar-değer çiftleri yinelemesi sağlamak için dinamik argümanların adlandırılmış demetine uygulanır. Metodun dinamik anahtar argümanlarını kabul etmemesi durumunda bu argüman mevcut değildir.

Sonunda kwsorter tanımı var:

```
function (::Core.kwftype(typeof(circle)))(kws, circle, center, radius)
    if haskey(kws, :color)
        color = kws.color
    else
        color = black
    end
    # etc.

    # put remaining kwargs in `options`
    options = structdiff(kws, NamedTuple{(:color, :fill)})

    # if the method doesn't accept rest keywords, throw an error
    # unless `options` is empty

    #circle#1(color, fill, pairs(options), circle, center, radius)
end
```

Fonksiyon `Core.kwftype(t)` alan `t.name.mt.kwsorter`'ı oluşturur (eğer henüz oluşturulmamışsa) ve o fonksiyonun türünü döndürür.

Bu tasarım, anahtar kelime argümanlarını kullanmayan çağrı noktalarının özel bir işleme gerektirmediği özelliğine sahiptir; her şey, sanki dilin bir parçası değilmiş gibi çalışır. Anahtar kelime argümanlarını kullanan çağrı noktaları ise doğrudan çağrılan fonksiyonun kwsorter'ına yönlendirilir. Örneğin, çağrı:

```julia
circle((0, 0), 1.0, color = red; other...)
```

düşürülmüştür:

```julia
kwcall(merge((color = red,), other), circle, (0, 0), 1.0)
```

`kwcall` (aynı zamanda `Core` içinde) bir kwcall imzasını ve dağıtımını belirtir. Anahtar kelime splatting işlemi (şu şekilde yazılır: `other...`) adlandırılmış demet `merge` fonksiyonunu çağırır. Bu fonksiyon, `other`'ın her bir *ögesini* daha da açar ve her birinin iki değer (bir sembol ve bir değer) içermesini bekler. Elbette, tüm splatted argümanların adlandırılmış demetler olması durumunda daha verimli bir uygulama mevcuttur. Orijinal `circle` fonksiyonunun kapalıları işlemek için geçirildiğine dikkat edin.

## [Compiler efficiency issues](@id compiler-efficiency-issues)

Her fonksiyon için yeni bir tür oluşturmak, Julia'nın "varsayılan olarak tüm argümanlar üzerinde özelleştir" tasarımıyla birleştirildiğinde derleyici kaynak kullanımı için potansiyel olarak ciddi sonuçlar doğurur. Gerçekten de, bu tasarımın ilk uygulaması çok daha uzun inşa ve test süreleri, daha yüksek bellek kullanımı ve temel sürümden neredeyse 2 kat daha büyük bir sistem görüntüsü ile sorun yaşadı. Naif bir uygulamada, sorun o kadar kötü ki sistemi neredeyse kullanılamaz hale getiriyor. Tasarımı pratik hale getirmek için birkaç önemli optimizasyon gerekiyordu.

İlk sorun, fonksiyon değerli argümanlar için farklı değerler için aşırı uzmanlaşmadır. Birçok fonksiyon, bir argümanı başka bir yere, örneğin başka bir fonksiyona veya bir depolama konumuna "geçirir". Bu tür fonksiyonların, geçilebilecek her kapanış için uzmanlaşmasına gerek yoktur. Neyse ki, bu durumu ayırt etmek kolaydır; bir fonksiyonun argümanlarından birini *çağırıp çağırmadığını* düşünmek yeterlidir (yani, argüman "baş pozisyonda" bir yerde görünür). Performans açısından kritik olan yüksek dereceli fonksiyonlar, örneğin `map`, kesinlikle argüman fonksiyonunu çağırır ve bu nedenle beklenildiği gibi uzmanlaşmaya devam eder. Bu optimizasyon, `analyze-variables` aşamasında hangi argümanların çağrıldığını kaydederek uygulanır. `cache_method`, `Any` veya `Function` olarak tanımlanmış bir slot'a geçirilen `Function` tür hiyerarşisinde bir argüman gördüğünde, sanki `@nospecialize` notasyonu uygulanmış gibi davranır. Bu sezgi pratikte son derece etkili görünmektedir.

Sonraki sorun, yöntem önbellek hash tablolarının yapısıyla ilgilidir. Ampirik çalışmalar, dinamik olarak dağıtılan çağrıların büyük çoğunluğunun bir veya iki argüman içerdiğini göstermektedir. Bu durum, bu durumların çoğunun yalnızca ilk argümanı dikkate alarak çözülebileceği anlamına gelir. (Not: tek dağıtımın savunucuları bununla hiç şaşırmaz. Ancak, bu argüman "çoklu dağıtım pratikte optimize edilmesi kolaydır" anlamına gelir ve bu nedenle bunu kullanmalıyız, *tek dağıtımı kullanmalıyız* demek değildir!) Bu nedenle, yöntem önbelleği ilk argümanın türünü birincil anahtar olarak kullanır. Ancak, bunun bir işlev çağrısının *ikinci* elemanına karşılık geldiğini unutmayın (ilk eleman işlevin kendisinin türüdür). Genellikle, baş pozisyondaki tür varyasyonu son derece düşüktür - aslında, işlevlerin çoğu parametre içermeyen tekil türlere aittir. Ancak, bu durum yapıcılar için geçerli değildir; burada tek bir yöntem tablosu her tür için yapıcıları tutar. Bu nedenle, `Type` yöntem tablosu, ikinci yerine *ilk* tuple türü elemanını kullanacak şekilde özel olarak işlenmiştir.

Ön uç, tüm kapanışlar için tür bildirimleri oluşturur. Başlangıçta, bu normal tür bildirimleri oluşturarak uygulanmıştı. Ancak, bu son derece büyük sayıda yapıcılar üretti ve bunların hepsi önemsizdi (tüm argümanları [`new`](@ref)'ya iletmekten ibaretti). Yöntemler kısmen sıralı olduğundan, bunların hepsini eklemek O(n²) zaman alır ve etrafta tutacak kadar çokları var. Bu, `struct_type` ifadeleri doğrudan oluşturarak (varsayılan yapıcı oluşturmayı atlayarak) ve kapanış örneklerini oluşturmak için doğrudan `new` kullanarak optimize edildi. En güzel şey değil ama yapmanız gerekeni yaparsınız.

Sonraki sorun, her test durumu için 0-argümanlı bir closure üreten `@test` makrosuydu. Bu gerçekten gerekli değil, çünkü her test durumu yalnızca bir kez yerinde çalıştırılır. Bu nedenle, `@test`'in, test sonucunu (doğru, yanlış veya istisna oluştu) kaydeden ve buna test paketi işleyicisini çağıran bir try-catch bloğuna genişletilmesi için değiştirildi.
