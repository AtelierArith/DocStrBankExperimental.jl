# [Types](@id man-types)

Tip sistemleri geleneksel olarak iki oldukça farklı gruba ayrılmıştır: her program ifadesinin programın yürütülmesinden önce hesaplanabilir bir türü olması gereken statik tip sistemleri ve türler hakkında hiçbir şeyin bilinmediği dinamik tip sistemleri. Dinamik tip sistemlerinde, program tarafından işlenen gerçek değerler mevcut olduğunda, yürütme zamanında türler hakkında bilgi edinilir. Nesne yönelimi, statik olarak tiplenmiş dillerde, kodun derleme zamanında değerlerin kesin türleri bilinmeden yazılmasına izin vererek bazı esneklik sağlar. Farklı türler üzerinde çalışabilen kod yazma yeteneğine çok biçimlilik (polimorfizm) denir. Klasik dinamik olarak tiplenmiş dillerdeki tüm kod polimorfiktir: yalnızca türleri açıkça kontrol ederek veya nesneler çalışma zamanında işlemleri desteklemeyi başaramadığında, herhangi bir değerin türleri kısıtlanır.

Julia'nın tür sistemi dinamiktir, ancak belirli değerlerin belirli türlerde olduğunu belirtme olanağı sunarak statik tür sistemlerinin bazı avantajlarını kazanır. Bu, verimli kod üretiminde büyük bir yardımcı olabilir, ancak daha da önemlisi, işlev argümanlarının türleri üzerinde yöntem dağıtımının dil ile derinlemesine entegre edilmesine olanak tanır. Yöntem dağıtımı [Methods](@ref)'da ayrıntılı olarak incelenmiştir, ancak burada sunulan tür sistemine dayanmaktadır.

Julia'da türler atlanıldığında varsayılan davranış, değerlerin herhangi bir türde olmasına izin vermektir. Bu nedenle, türleri açıkça kullanmadan birçok yararlı Julia fonksiyonu yazmak mümkündür. Ancak, ek bir ifade gücüne ihtiyaç duyulduğunda, daha önce "tütsüz" olan koda kademeli olarak açık tür anotasyonları eklemek kolaydır. Anotasyon eklemenin üç ana amacı vardır: Julia'nın güçlü çoklu dağıtım mekanizmasından yararlanmak, insan okunabilirliğini artırmak ve programcı hatalarını yakalamaktır.

Julia'nın [type systems](https://en.wikipedia.org/wiki/Type_system) lingo'sunda tanımlanması: dinamik, nominatif ve parametrik. Genel türler parametreleştirilebilir ve türler arasındaki hiyerarşik ilişkiler [explicitly declared](https://en.wikipedia.org/wiki/Nominal_type_system) şeklindedir, [implied by compatible structure](https://en.wikipedia.org/wiki/Structural_type_system) yerine. Julia'nın tür sisteminin özellikle belirgin bir özelliği, somut türlerin birbirini alt tür olarak almayacağıdır: tüm somut türler sonludur ve yalnızca soyut türlerin üst türleri olabilir. Bu başlangıçta gereksiz kısıtlayıcı gibi görünse de, birçok faydalı sonucu vardır ve şaşırtıcı derecede az dezavantajı vardır. Davranışı miras alabilmenin, yapıyı miras alabilmekten çok daha önemli olduğu ortaya çıkıyor ve her ikisini miras almak, geleneksel nesne yönelimli dillerde önemli zorluklara neden oluyor. Julia'nın tür sisteminin öncelikle belirtilmesi gereken diğer yüksek düzeydeki yönleri şunlardır:

  * Nesne ve nesne olmayan değerler arasında bir ayrım yoktur: Julia'daki tüm değerler, tek bir, tamamen bağlı bir tür grafiğine ait olan gerçek nesnelerdir; bu grafikteki tüm düğümler türler olarak eşit derecede birinci sınıftır.
  * Anlamlı bir "derleme zamanı tipi" kavramı yoktur: Bir değerin sahip olduğu tek tip, program çalışırken gerçek tipidir. Bu, nesne yönelimli dillerde, statik derleme ile çok biçimliliğin bu ayrımı önemli hale getirdiği durumlarda "çalışma zamanı tipi" olarak adlandırılır.
  * Sadece değerlerin türleri vardır, değişkenler ise yalnızca değerlere bağlı isimlerdir; ancak basitlik açısından "değişkenin türü" demek, "değişkenin referans verdiği değerin türü" anlamında kullanılabilir.
  * Hem soyut hem de somut türler, diğer türlerle parametreleştirilebilir. Ayrıca, sembollerle, [`isbits`](@ref) ifadesinin true döndüğü herhangi bir türün değerleriyle (temelde, C türleri gibi saklanan sayılar ve bool'lar veya diğer nesnelere işaretçi içermeyen `struct`lar) ve bunların demetleriyle de parametreleştirilebilir. Tür parametreleri, referans verilmesi veya kısıtlanması gerekmiyorsa atlanabilir.

Julia'nın tür sistemi güçlü ve ifade edici olacak şekilde tasarlanmıştır, aynı zamanda net, sezgisel ve rahatsız edici olmaktan uzaktır. Birçok Julia programcısı, türleri açıkça kullanan kod yazma ihtiyacı hissetmeyebilir. Ancak, bazı programlama türleri, tanımlı türlerle daha net, daha basit, daha hızlı ve daha sağlam hale gelir.

## Type Declarations

`::` operatörü, programlardaki ifadeler ve değişkenlere tür açıklamaları eklemek için kullanılabilir. Bunu yapmanın iki ana nedeni vardır:

1. Bir doğrulama olarak, programınızın beklediğiniz gibi çalıştığını onaylamaya yardımcı olmak için ve
2. Derleyiciye ek tür bilgisi sağlamak için, bu da bazı durumlarda performansı artırabilir.

Bir değeri hesaplayan bir ifadeye eklendiğinde, `::` operatörü "bir örnektir" şeklinde okunur. Sol taraftaki ifadenin değeri ile sağ taraftaki türün bir örneği olduğunu belirtmek için her yerde kullanılabilir. Sağ taraftaki tür somut olduğunda, sol taraftaki değerin o türü uygulama olarak taşıması gerekir - tüm somut türlerin nihai olduğunu hatırlayın, bu nedenle hiçbir uygulama başka birinin alt türü olamaz. Tür soyut olduğunda, değerin soyut türün alt türü olan somut bir tür tarafından uygulanması yeterlidir. Tür doğrulaması doğru değilse, bir istisna fırlatılır, aksi takdirde sol taraftaki değer döndürülür:

```jldoctest
julia> (1+2)::AbstractFloat
ERROR: TypeError: in typeassert, expected AbstractFloat, got a value of type Int64

julia> (1+2)::Int
3
```

Bu, bir tür iddiasının herhangi bir ifadeye yerinde eklenmesine olanak tanır.

Bir atamanın sol tarafındaki bir değişkene eklendiğinde veya bir `local` bildiriminde yer aldığında, `::` operatörü biraz farklı bir anlam taşır: değişkenin her zaman belirtilen türe sahip olacağını bildirir, bu da C gibi statik olarak tiplenmiş bir dildeki bir tür bildirimine benzer. Değişkene atanan her değer, [`convert`](@ref) kullanılarak bildirilen türe dönüştürülecektir:

```jldoctest
julia> function foo()
           x::Int8 = 100
           x
       end
foo (generic function with 1 method)

julia> x = foo()
100

julia> typeof(x)
Int8
```

Bu özellik, bir değişkene yapılan atamalardan birinin beklenmedik bir şekilde türünü değiştirmesi durumunda ortaya çıkabilecek performans "sorunlarını" önlemek için faydalıdır.

Bu "beyan" davranışı yalnızca belirli bağlamlarda meydana gelir:

```julia
local x::Int8  # in a local declaration
x::Int8 = 10   # as the left-hand side of an assignment
```

ve ve mevcut kapsamın tamamına uygulanır, hatta bildirimden önce bile.

Julia 1.8 itibarıyla, tür bildirimleri artık global kapsamda kullanılabilir; yani, global değişkenlere tür notları eklenerek onlara erişim tür açısından kararlı hale getirilebilir.

```julia
julia> x::Int = 10
10

julia> x = 3.5
ERROR: InexactError: Int64(3.5)

julia> function foo(y)
           global x = 15.8    # throws an error when foo is called
           return x + y
       end
foo (generic function with 1 method)

julia> foo(10)
ERROR: InexactError: Int64(15.8)
```

Fonksiyon tanımlarına da bildirimler eklenebilir:

```julia
function sinc(x)::Float64
    if x == 0
        return 1
    end
    return sin(pi*x)/(pi*x)
end
```

Bu işlevden döndürme, bir değişkenin belirlenmiş türüne atanması gibi davranır: değer her zaman `Float64`'e dönüştürülür.

## [Abstract Types](@id man-abstract-types)

Soyut türler örneklenemez ve yalnızca tür grafiğinde düğüm olarak hizmet ederler, böylece ilişkili somut türlerin kümelerini tanımlarlar: bunlar, onların soyundan gelen somut türlerdir. Örneklenmeleri olmasa da soyut türlerle başlıyoruz çünkü bunlar tür sisteminin belkemiğidir: Julia'nın tür sistemini yalnızca bir nesne uygulamaları koleksiyonu olmaktan daha fazlası yapan kavramsal hiyerarşiyi oluştururlar.

[Integers and Floating-Point Numbers](@ref) içinde, çeşitli somut sayısal değer türlerini tanıttık: [`Int8`](@ref), [`UInt8`](@ref), [`Int16`](@ref), [`UInt16`](@ref), [`Int32`](@ref), [`UInt32`](@ref), [`Int64`](@ref), [`UInt64`](@ref), [`Int128`](@ref), [`UInt128`](@ref), [`Float16`](@ref), [`Float32`](@ref), ve [`Float64`](@ref). Farklı temsil boyutlarına sahip olmalarına rağmen, `Int8`, `Int16`, `Int32`, `Int64` ve `Int128` hepsi işaretli tam sayı türleridir. Benzer şekilde `UInt8`, `UInt16`, `UInt32`, `UInt64` ve `UInt128` hepsi işaretsiz tam sayı türleridir, oysa `Float16`, `Float32` ve `Float64,` tam sayılar yerine kayan nokta türleri olarak farklıdır. Bir kod parçasının anlamlı olması yaygındır; örneğin, yalnızca argümanları bir tür tam sayı olduğunda anlam kazanır, ancak hangi belirli *tür* tam sayı olduğuna gerçekten bağlı değildir. Örneğin, en büyük ortak bölen algoritması tüm türdeki tam sayılar için çalışır, ancak kayan nokta sayıları için çalışmaz. Soyut türler, somut türlerin uyum sağlayabileceği bir bağlam sağlayarak bir tür hiyerarşisinin inşasına olanak tanır. Bu, örneğin, bir algoritmayı belirli bir tam sayı türüne kısıtlamadan, herhangi bir tam sayı türüne kolayca program yapmanıza olanak tanır.

Soyut türler [`abstract type`](@ref) anahtar kelimesi kullanılarak tanımlanır. Soyut bir tür tanımlamak için genel sözdizimleri şunlardır:

```
abstract type «name» end
abstract type «name» <: «supertype» end
```

`abstract type` anahtar kelimesi, adı `«name»` ile verilen yeni bir soyut tür tanıtır. Bu ad, isteğe bağlı olarak [`<:`](@ref) ve zaten var olan bir tür ile takip edilebilir; bu, yeni tanımlanan soyut türün bu "ebeveyn" türün bir alt türü olduğunu belirtir.

Hiçbir süpertip verilmediğinde, varsayılan süpertip `Any`'dir - tüm nesnelerin örnekleri olduğu ve tüm türlerin alt türleri olduğu önceden tanımlanmış soyut bir tür. Tür teorisinde, `Any` genellikle "üst" olarak adlandırılır çünkü tür grafiğinin zirvesindedir. Julia ayrıca tür grafiğinin en alt noktasında yazılan önceden tanımlanmış bir soyut "alt" tür olan `Union{}`'ye sahiptir. Bu, `Any`'nin tam tersidir: hiçbir nesne `Union{}`'nin bir örneği değildir ve tüm türler `Union{}`'nin süpertipleridir.

Julia'nın sayısal hiyerarşisini oluşturan bazı soyut türleri göz önünde bulunduralım:

```julia
abstract type Number end
abstract type Real          <: Number end
abstract type AbstractFloat <: Real end
abstract type Integer       <: Real end
abstract type Signed        <: Integer end
abstract type Unsigned      <: Integer end
```

[`Number`](@ref) türü `Any`'nin doğrudan bir alt türüdür ve [`Real`](@ref) onun çocuğudur. Sırasıyla, `Real`'in iki çocuğu vardır (daha fazlası vardır, ancak burada yalnızca ikisi gösterilmektedir; diğerlerine daha sonra geleceğiz): [`Integer`](@ref) ve [`AbstractFloat`](@ref), dünyayı tam sayıların ve gerçek sayıların temsilleri olarak ayırmaktadır. Gerçek sayıların temsilleri, kayan nokta türlerini içerir, ancak aynı zamanda rasyonel gibi diğer türleri de içerir. `AbstractFloat` yalnızca gerçek sayıların kayan nokta temsillerini içerir. Tam sayılar daha da [`Signed`](@ref) ve [`Unsigned`](@ref) çeşitlerine ayrılır.

`<:` operatörü genel olarak "bir alt türdür" anlamına gelir ve yukarıdaki gibi bildirimlerde kullanıldığında, sağdaki türü yeni bildirilen türün doğrudan üst türü olarak tanımlar. Ayrıca, sol operatörünün sağ operatörünün bir alt türü olduğu durumlarda `true` döndüren bir alt tür operatörü olarak ifadelerde de kullanılabilir:

```jldoctest
julia> Integer <: Number
true

julia> Integer <: AbstractFloat
false
```

Soyut türlerin önemli bir kullanımı, somut türler için varsayılan uygulamalar sağlamaktır. Basit bir örnek vermek gerekirse, düşünün:

```julia
function myplus(x,y)
    x+y
end
```

İlk olarak, yukarıdaki argüman bildirimlerinin `x::Any` ve `y::Any` ile eşdeğer olduğunu belirtmek gerekir. Bu fonksiyon, örneğin `myplus(2,5)` olarak çağrıldığında, dispatcher verilen argümanlarla eşleşen en spesifik `myplus` yöntemini seçer. (Birden fazla dispatch hakkında daha fazla bilgi için [Methods](@ref)'ya bakın.)

Varsayılarak yukarıda belirtilenlerden daha spesifik bir yöntem bulunmadığında, Julia daha sonra yukarıda verilen genel işlev temelinde iki `Int` argümanı için özel olarak `myplus` adında bir yöntem tanımlar ve derler, yani, örtük olarak tanımlar ve derler:

```julia
function myplus(x::Int,y::Int)
    x+y
end
```

ve nihayet, bu belirli yöntemi çağırır.

Bu nedenle, soyut türler programcıların daha sonra birçok somut tür kombinasyonu tarafından varsayılan yöntem olarak kullanılabilecek genel işlevler yazmalarına olanak tanır. Çoklu dağıtım sayesinde, programcı varsayılan veya daha spesifik yöntemin kullanılıp kullanılmayacağı üzerinde tam kontrole sahiptir.

Önemli bir nokta, programcının soyut türlerin argümanlarına sahip bir işleve güvenmesi durumunda performansta bir kayıp olmayacağıdır, çünkü bu işlev, çağrıldığı her somut argüman türü demeti için yeniden derlenir. (Ancak, soyut türlerin kapsayıcıları olan işlev argümanları durumunda bir performans sorunu olabilir; bkz. [Performance Tips](@ref man-performance-abstract-container).)

## Primitive Types

!!! warning
    Mevcut bir ilkel türü yeni bir bileşik türün içine sarmak, kendi ilkel türünüzü tanımlamaktan neredeyse her zaman daha tercih edilir.

    Bu işlevsellik, Julia'nın LLVM'nin desteklediği standart ilkel türleri başlatmasına olanak tanımak için vardır. Tanımlandıktan sonra, daha fazlasını tanımlamak için çok az neden vardır.


Bir ilkel tür, verileri sıradan eski bitlerden oluşan somut bir türdür. İlkel türlerin klasik örnekleri tam sayılar ve kayan nokta değerleridir. Çoğu dilden farklı olarak, Julia kendi ilkel türlerinizi tanımlamanıza izin verir; yalnızca sabit bir yerleşik set sağlamakla kalmaz. Aslında, standart ilkel türlerin hepsi dilin kendisinde tanımlanmıştır:

```julia
primitive type Float16 <: AbstractFloat 16 end
primitive type Float32 <: AbstractFloat 32 end
primitive type Float64 <: AbstractFloat 64 end

primitive type Bool <: Integer 8 end
primitive type Char <: AbstractChar 32 end

primitive type Int8    <: Signed   8 end
primitive type UInt8   <: Unsigned 8 end
primitive type Int16   <: Signed   16 end
primitive type UInt16  <: Unsigned 16 end
primitive type Int32   <: Signed   32 end
primitive type UInt32  <: Unsigned 32 end
primitive type Int64   <: Signed   64 end
primitive type UInt64  <: Unsigned 64 end
primitive type Int128  <: Signed   128 end
primitive type UInt128 <: Unsigned 128 end
```

Temel bir türü tanımlamak için genel sözdizimleri şunlardır:

```
primitive type «name» «bits» end
primitive type «name» <: «supertype» «bits» end
```

Bit sayısı, türün ne kadar depolama alanı gerektirdiğini gösterir ve isim, yeni türe bir ad verir. Bir ilkel tür, isteğe bağlı olarak bir süper türün alt türü olarak tanımlanabilir. Eğer bir süper tür belirtilmezse, türün varsayılan olarak `Any`'yi doğrudan süper türü olarak alır. Yukarıdaki [`Bool`](@ref) ifadesi, dolayısıyla bir boolean değerinin depolamak için sekiz bit aldığını ve [`Integer`](@ref)'yı doğrudan süper türü olarak aldığını belirtir. Şu anda yalnızca 8 bitin katları olan boyutlar desteklenmektedir ve yukarıda kullanılanlardan farklı boyutlarla LLVM hatalarıyla karşılaşma olasılığınız yüksektir. Bu nedenle, boolean değerleri, gerçekte yalnızca bir bit gerektirse de, sekiz bitten daha küçük olarak tanımlanamaz.

[`Bool`](@ref), [`Int8`](@ref) ve [`UInt8`](@ref) türleri, sekiz bitlik bellek parçaları olarak aynı temsillere sahiptir. Ancak Julia'nın tür sistemi nominatif olduğundan, aynı yapıya sahip olmalarına rağmen birbirinin yerine geçemezler. Aralarındaki temel fark, farklı üst türlere sahip olmalarıdır: `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566`'nın doğrudan üst türü [`Integer`](@ref), `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566`'nın üst türü [`Signed`](@ref) ve `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566`'nın üst türü [`Unsigned`](@ref)'dır. `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566`, `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` ve `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566` arasındaki diğer tüm farklar, bu türlerin argüman olarak verildiğinde işlevlerin nasıl tanımlandığı ile ilgilidir. Bu nedenle nominatif bir tür sisteminin gerekli olduğu söylenebilir: eğer yapı türü belirleseydi ve bu da davranışı dikte etseydi, o zaman `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566`'nın `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` veya `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566`'dan farklı bir şekilde davranmasını sağlamak imkansız olurdu.

## Composite Types

[Composite types](https://en.wikipedia.org/wiki/Composite_data_type) çeşitli dillerde kayıtlar, yapılar veya nesneler olarak adlandırılır. Bir bileşik tür, adlandırılmış alanların bir koleksiyonudur; bunun bir örneği tek bir değer olarak ele alınabilir. Birçok dilde, bileşik türler kullanıcı tarafından tanımlanabilen tek türdür ve bunlar Julia'da en yaygın kullanılan kullanıcı tanımlı türdür.

Ana akışkan nesne yönelimli dillerde, C++, Java, Python ve Ruby gibi, bileşik türlerin de onlarla ilişkili adlandırılmış işlevleri vardır ve bu kombinasyona "nesne" denir. Ruby veya Smalltalk gibi daha saf nesne yönelimli dillerde, tüm değerler nesnedir, bileşik olup olmadıklarına bakılmaksızın. C++ ve Java gibi daha az saf nesne yönelimli dillerde ise, tam sayılar ve kayan nokta değerleri gibi bazı değerler nesne değildir, oysa kullanıcı tanımlı bileşik türlerin örnekleri gerçek nesneler olup ilişkili yöntemlere sahiptir. Julia'da, tüm değerler nesnedir, ancak işlevler, üzerinde çalıştıkları nesnelerle birleştirilmez. Bu, Julia'nın bir işlevin hangi yöntemini kullanacağına çoklu dağıtım ile karar vermesi gerektiğinden gereklidir; bu, bir işlevin argümanlarının *tüm* türlerinin bir yöntemi seçerken dikkate alındığı anlamına gelir, yalnızca ilk olan değil (yöntemler ve dağıtım hakkında daha fazla bilgi için [Methods](@ref)'ya bakın). Bu nedenle, işlevlerin yalnızca ilk argümanlarına "ait" olması uygun olmaz. Yöntemleri işlev nesneleri içinde düzenlemek, her nesnenin "içinde" adlandırılmış yöntem torbaları bulundurmaktan çok daha faydalı bir dil tasarımı yönü haline gelir.

Bileşik türler, [`struct`](@ref) anahtar kelimesi ile tanıtılır ve ardından isteğe bağlı olarak `::` operatörü kullanılarak türlerle anotasyon yapılmış bir alan adları bloğu gelir:

```jldoctest footype
julia> struct Foo
           bar
           baz::Int
           qux::Float64
       end
```

Tipler olmayan alanlar varsayılan olarak `Any` türündedir ve dolayısıyla herhangi bir türde değer tutabilirler.

Yeni `Foo` türündeki nesneler, `Foo` türü nesnesini alanları için değerlerle bir fonksiyon gibi uygulayarak oluşturulur:

```jldoctest footype
julia> foo = Foo("Hello, world.", 23, 1.5)
Foo("Hello, world.", 23, 1.5)

julia> typeof(foo)
Foo
```

Bir tür bir fonksiyon gibi uygulandığında buna *yapıcı* denir. İki yapıcı otomatik olarak oluşturulur (bunlara *varsayılan yapıcılar* denir). Biri herhangi bir argümanı kabul eder ve bunları alanların türlerine dönüştürmek için [`convert`](@ref) çağrısını yapar, diğeri ise argümanları tam olarak alan türleriyle eşleşecek şekilde kabul eder. Her ikisinin de oluşturulmasının nedeni, yeni tanımlar eklemeyi kolaylaştırmasıdır; bu, varsayılan bir yapıcıyı istemeden değiştirmeyi önler.

`bar` alanı tür açısından kısıtlanmadığı için herhangi bir değer alabilir. Ancak, `baz` için değer `Int`'e dönüştürülebilir olmalıdır:

```jldoctest footype
julia> Foo((), 23.5, 1)
ERROR: InexactError: Int64(23.5)
Stacktrace:
[...]
```

[`fieldnames`](@ref) fonksiyonunu kullanarak alan adlarının bir listesini bulabilirsiniz.

```jldoctest footype
julia> fieldnames(Foo)
(:bar, :baz, :qux)
```

Bir bileşik nesnenin alan değerlerine geleneksel `foo.bar` notasyonu kullanarak erişebilirsiniz:

```jldoctest footype
julia> foo.bar
"Hello, world."

julia> foo.baz
23

julia> foo.qux
1.5
```

`struct` ile tanımlanan bileşik nesneler *değişmezdir*; inşaattan sonra değiştirilemezler. Bu başlangıçta garip görünebilir, ancak birkaç avantajı vardır:

  * Daha verimli olabilir. Bazı yapılar, dizilere verimli bir şekilde yerleştirilebilir ve bazı durumlarda derleyici, değişmez nesneleri tamamen ayırmaktan kaçınabilir.
  * Tipin yapıcıları tarafından sağlanan değişmezleri ihlal etmek mümkün değildir.
  * Değişmez nesneler kullanan kod, düşünülmesi daha kolay olabilir.

Değiştirilemez bir nesne, alanlar olarak değiştirilebilir nesneler, örneğin diziler içerebilir. İçerideki nesneler değiştirilebilir kalmaya devam eder; yalnızca değiştirilemez nesnenin kendisine ait alanlar farklı nesnelere işaret edecek şekilde değiştirilemez.

Gerekli olduğunda, değiştirilebilir bileşik nesneler [`mutable struct`](@ref) anahtar kelimesi ile tanımlanabilir, bir sonraki bölümde tartışılacaktır.

Eğer bir değişmez yapının tüm alanları ayırt edilemezse (`===`), o zaman bu alanları içeren iki değişmez değer de ayırt edilemez.

```jldoctest
julia> struct X
           a::Int
           b::Float64
       end

julia> X(1, 2) === X(1, 2)
true
```

Composite türlerin örneklerinin nasıl oluşturulduğu hakkında daha fazla şey söylemek mümkündür, ancak bu tartışma hem [Parametric Types](@ref) hem de [Methods](@ref)'ya bağlıdır ve kendi bölümünde ele alınması yeterince önemlidir: [Constructors](@ref man-constructors).

Birçok kullanıcı tanımlı tür `X` için, o türün örneklerinin [broadcasting](@ref Broadcasting) için 0 boyutlu "skalarlar" olarak davranmasını sağlamak amacıyla [`Base.broadcastable(x::X) = Ref(x)`](@ref man-interfaces-broadcasting) adlı bir yöntem tanımlamak isteyebilirsiniz.

## Mutable Composite Types

Eğer bir bileşik tür `struct` yerine `mutable struct` ile tanımlanmışsa, o zaman onun örnekleri değiştirilebilir:

```jldoctest bartype
julia> mutable struct Bar
           baz
           qux::Float64
       end

julia> bar = Bar("Hello", 1.5);

julia> bar.qux = 2.0
2.0

julia> bar.baz = 1//2
1//2
```

An extra interface between the fields and the user can be provided through [Instance Properties](@ref man-instance-properties). This grants more control on what can be accessed and modified using the `bar.baz` notation.

Değişim desteği sağlamak için, bu tür nesneler genellikle yığın üzerinde tahsis edilir ve sabit bellek adreslerine sahiptir. Değiştirilebilir bir nesne, zamanla farklı değerler tutabilen küçük bir konteyner gibidir ve bu nedenle yalnızca adresi ile güvenilir bir şekilde tanımlanabilir. Buna karşılık, değişmez bir türün bir örneği belirli alan değerleri ile ilişkilidir - alan değerleri, nesne hakkında her şeyi anlatır. Bir türü değiştirilebilir yapma kararı verirken, aynı alan değerlerine sahip iki örneğin kimlik açısından aynı kabul edilip edilmeyeceğini veya zamanla bağımsız olarak değişmeleri gerekip gerekmediğini sorun. Eğer aynı kabul edileceklerse, tür muhtemelen değişmez olmalıdır.

Özetlemek gerekirse, Julia'da değişmezliği tanımlayan iki temel özellik vardır:

  * Değiştirilemez bir türün değerini değiştirmek yasaktır.

      * Bit türleri için bu, bir değerin bir kez ayarlandığında bit deseninin asla değişmeyeceği ve bu değerin bir bit türünün kimliği olduğu anlamına gelir.
      * Bileşik türler için bu, alanlarının değerlerinin kimliğinin asla değişmeyeceği anlamına gelir. Alanlar bit türleri olduğunda, bu, bitlerinin asla değişmeyeceği anlamına gelir; değerleri değişken türler olan diziler gibi alanlar için, bu, alanların her zaman aynı değişken değere atıfta bulunacağı anlamına gelir, oysa o değişken değerin içeriği kendisi değiştirilebilir.
  * Değiştirilemez bir türe sahip bir nesne, değiştirilemezliği nedeniyle orijinal nesne ile bir kopya arasında programatik olarak ayırt edilmesini imkansız hale getirdiğinden, derleyici tarafından serbestçe kopyalanabilir.

      * Özellikle, bu, yeterince küçük olan değişmez değerlerin, örneğin tam sayılar ve ondalık sayılar, genellikle işlevlere kayıtlar (veya yığın tahsis edilmiş) aracılığıyla iletildiği anlamına gelir.
      * Değişken değerler, diğer yandan, yığın üzerinde tahsis edilir ve işlevlere yığın üzerinde tahsis edilmiş değerlere işaretçi olarak geçilir, derleyicinin bunun böyle olmadığını kesin olarak bildiği durumlar dışında.

Bir veya daha fazla alanı değiştirilebilir bir yapının, değişmez olduğu bilinen alanları varsa, bu alanları aşağıda gösterildiği gibi `const` kullanarak tanımlayabilirsiniz. Bu, değişmez yapıların bazı, ancak tüm optimizasyonlarını etkinleştirir ve `const` ile işaretlenmiş belirli alanlar üzerinde invariants uygulamak için kullanılabilir.

!!! compat "Julia 1.8"
    `const` değişkenleri, değiştirilebilir yapıların alanlarını işaretlemek için en az Julia 1.8 gerektirir.


```jldoctest baztype
julia> mutable struct Baz
           a::Int
           const b::Float64
       end

julia> baz = Baz(1, 1.5);

julia> baz.a = 2
2

julia> baz.b = 2.0
ERROR: setfield!: const field .b of type Baz cannot be changed
[...]
```

## [Declared Types](@id man-declared-types)

Üç tür (soyut, ilkel, bileşik) önceki bölümlerde tartışılanlar aslında birbirleriyle yakından ilişkilidir. Aynı temel özellikleri paylaşırlar:

  * Açıkça belirtilmişlerdir.
  * Onların isimleri var.
  * Onlar açıkça süper türleri ilan ettiler.
  * Parametreleri olabilir.

Bu paylaşılan özellikler nedeniyle, bu türler aynı kavramın örnekleri olarak içsel olarak `DataType` olarak temsil edilir; bu, bu türlerin herhangi birinin türüdür:

```jldoctest
julia> typeof(Real)
DataType

julia> typeof(Int)
DataType
```

Bir `DataType` soyut veya somut olabilir. Eğer somut ise, belirli bir boyutu, depolama düzeni ve (isteğe bağlı olarak) alan adları vardır. Bu nedenle, bir ilkel tür, sıfırdan büyük boyuta sahip ancak alan adı olmayan bir `DataType`'dır. Bir bileşik tür, alan adlarına sahip olan veya boş (sıfır boyut) olan bir `DataType`'dır.

Sistemdeki her somut değer, bir `DataType` örneğidir.

## Type Unions

Bir tür birliği, argüman türlerinin herhangi birinin tüm örneklerini içeren özel bir soyut türdür ve [`Union`](@ref) anahtar kelimesi kullanılarak oluşturulur:

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 :: IntOrString
1

julia> "Hello!" :: IntOrString
"Hello!"

julia> 1.0 :: IntOrString
ERROR: TypeError: in typeassert, expected Union{Int64, AbstractString}, got a value of type Float64
```

Birçok dilin derleyicileri, türler hakkında düşünmek için dahili bir birleşim yapısına sahiptir; Julia bunu programcıya doğrudan sunar. Julia derleyicisi, `Union` türleri ile birlikte az sayıda tür bulunduğunda verimli kod üretebilir [^1], her olası tür için ayrı dallarda özel kod üreterek.

`Union` türünün özellikle yararlı bir durumu `Union{T, Nothing}`'dır; burada `T` herhangi bir tür olabilir ve [`Nothing`](@ref) tekil türdür ve tek örneği [`nothing`](@ref) nesnesidir. Bu desen, diğer dillerdeki [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type) türlerinin Julia eşdeğeridir. Bir fonksiyon argümanını veya bir alanı `Union{T, Nothing}` olarak tanımlamak, onu ya `T` türünde bir değere ya da değer olmadığını belirtmek için `nothing` olarak ayarlamaya olanak tanır. Daha fazla bilgi için [this FAQ entry](@ref faq-nothing)'e bakın.

## Parametric Types

Julia'nın tür sisteminin önemli ve güçlü bir özelliği parametreli olmasıdır: türler parametreler alabilir, böylece tür bildirimleri aslında yeni türlerin bir ailesini tanıtır - her olası parametre değeri kombinasyonu için bir tane. [generic programming](https://en.wikipedia.org/wiki/Generic_programming) gibi bazı diller, veri yapıları ve bunları manipüle etmek için algoritmaların tam türleri belirtmeden tanımlanmasına izin verir. Örneğin, ML, Haskell, Ada, Eiffel, C++, Java, C#, F# ve Scala gibi dillerde bazı biçimlerde genel programlama mevcuttur, sadece birkaçını saymak gerekirse. Bu dillerden bazıları gerçek parametreli polimorfizmi destekler (örneğin, ML, Haskell, Scala), diğerleri ise genel programlamanın ad-hoc, şablon tabanlı stillerini destekler (örneğin, C++, Java). Farklı dillerdeki birçok genel programlama ve parametreli tür çeşitliliği ile Julia'nın parametreli türlerini diğer dillerle karşılaştırmaya çalışmayacağız, bunun yerine Julia'nın sistemini kendi başına açıklamaya odaklanacağız. Ancak, Julia'nın dinamik olarak türlendirilmiş bir dil olduğunu ve tüm tür kararlarını derleme zamanında vermesi gerekmediğinden, statik parametreli tür sistemlerinde karşılaşılan birçok geleneksel zorluğun nispeten kolay bir şekilde ele alınabileceğini belirtmek gerekir.

Tüm beyan edilen türler ( `DataType` çeşitleri) parametreleştirilebilir ve her durumda aynı sözdizimini kullanır. Bunları şu sırayla tartışacağız: önce parametrik bileşik türler, sonra parametrik soyut türler ve nihayet parametrik ilkel türler.

### [Parametric Composite Types](@id man-parametric-composite-types)

Tip parametreleri, tür adından hemen sonra, süslü parantezler içinde tanıtılır:

```jldoctest pointtype
julia> struct Point{T}
           x::T
           y::T
       end
```

Bu beyan, iki "koordinat" tutan yeni bir parametrik türü, `Point{T}`, tanımlar. T'nin ne olduğunu sorabilirsiniz? İşte parametrik türlerin tam olarak amacı: bu, aslında herhangi bir tür olabilir (veya aslında herhangi bir bit türünün bir değeri olabilir, ancak burada açıkça bir tür olarak kullanılmıştır). `Point{Float64}`, `Point` tanımındaki `T`'yi [`Float64`](@ref) ile değiştirdiğinizde elde edilen somut bir türdür. Böylece, bu tek beyan aslında sınırsız sayıda türü tanımlar: `Point{Float64}`, `Point{AbstractString}`, `Point{Int64}`, vb. Bunların her biri artık kullanılabilir somut bir türdür:

```jldoctest pointtype
julia> Point{Float64}
Point{Float64}

julia> Point{AbstractString}
Point{AbstractString}
```

`Point{Float64}` türü, koordinatları 64-bit kayan nokta değerleri olan bir noktadır, `Point{AbstractString}` türü ise "koordinatları" dize nesneleri olan bir "noktadır" (bkz. [Strings](@ref)).

`Point` kendisi de geçerli bir tür nesnesidir ve `Point{Float64}`, `Point{AbstractString}` vb. gibi tüm örnekleri alt türler olarak içerir:

```jldoctest pointtype
julia> Point{Float64} <: Point
true

julia> Point{AbstractString} <: Point
true
```

Diğer türler elbette bunun alt türleri değildir:

```jldoctest pointtype
julia> Float64 <: Point
false

julia> AbstractString <: Point
false
```

Beton `Point` türleri, `T` değerlerinin farklı olması durumunda birbirinin alt türü asla değildir:

```jldoctest pointtype
julia> Point{Float64} <: Point{Int64}
false

julia> Point{Float64} <: Point{Real}
false
```

!!! warning
    Bu son nokta *çok* önemlidir: `Float64 <: Real` olmasına rağmen `Point{Float64} <: Point{Real}` **YOKTUR**.


Başka bir deyişle, tip teorisi dilinde, Julia'nın tip parametreleri *değişmez*dir, [covariant (or even contravariant)](https://en.wikipedia.org/wiki/Covariance_and_contravariance_%28computer_science%29) olmaktan ziyade. Bunun pratik nedenleri vardır: `Point{Float64}`'in herhangi bir örneği, kavramsal olarak `Point{Real}` örneği gibi olsa da, iki tipin bellek içindeki temsilleri farklıdır:

  * `Point{Float64}` örneği, 64-bit değerlerin hemen yan yana gelmesiyle kompakt ve verimli bir şekilde temsil edilebilir;
  * `Point{Real}` örneği, [`Real`](@ref) örneklerinin herhangi bir çiftini tutabilmelidir. `Real` örnekleri keyfi boyut ve yapıda olabileceğinden, pratikte `Point{Real}` örneği, ayrı ayrı tahsis edilmiş `Real` nesnelerine işaret eden bir çift işaretçi olarak temsil edilmelidir.

`Point{Float64}` nesnelerini anlık değerlerle saklayabilme yeteneğinden kazanılan verimlilik, diziler durumunda muazzam bir şekilde artmaktadır: bir `Array{Float64}`, 64-bit kayan nokta değerlerinin bitişik bir bellek bloğu olarak saklanabilirken, bir `Array{Real}`, bireysel olarak tahsis edilmiş [`Real`](@ref) nesnelerine işaret eden bir işaretçi dizisi olmalıdır – bu nesneler [boxed](https://en.wikipedia.org/wiki/Object_type_%28object-oriented_programming%29#Boxing) 64-bit kayan nokta değerleri olabilir, ancak aynı zamanda `Real` soyut türünün uygulamaları olarak tanımlanan keyfi olarak büyük, karmaşık nesneler de olabilir.

`Point{Float64}` bir `Point{Real}` alt türü olmadığından, aşağıdaki yöntem `Point{Float64}` türündeki argümanlara uygulanamaz:

```julia
function norm(p::Point{Real})
    sqrt(p.x^2 + p.y^2)
end
```

Doğru bir şekilde, `T`'nin [`Real`](@ref) alt türü olduğu `Point{T}` türündeki tüm argümanları kabul eden bir yöntemi tanımlamak için:

```julia
function norm(p::Point{<:Real})
    sqrt(p.x^2 + p.y^2)
end
```

(Eşdeğer olarak, `function norm(p::Point{T} where T<:Real)` veya `function norm(p::Point{T}) where T<:Real` olarak tanımlanabilir; bkz. [UnionAll Types](@ref).)

Daha fazla örnek [Methods](@ref) içinde daha sonra tartışılacaktır.

Bir `Point` nesnesi nasıl oluşturulur? Bileşik türler için özel yapıcılar tanımlamak mümkündür, bu [Constructors](@ref man-constructors) bölümünde ayrıntılı olarak tartışılacaktır, ancak herhangi bir özel yapıcı bildirimi olmaksızın, yeni bileşik nesneler oluşturmanın iki varsayılan yolu vardır; biri tür parametrelerinin açıkça verildiği, diğeri ise nesne yapıcısına verilen argümanlarla ima edildiği bir yoldur.

`Point{Float64}` türü, `T` yerine [`Float64`](@ref) ile tanımlanan `Point` ile eşdeğer bir somut tür olduğundan, uygun bir yapıcı olarak uygulanabilir:

```jldoctest pointtype
julia> p = Point{Float64}(1.0, 2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p)
Point{Float64}
```

Varsayılan yapıcı için, her alan için tam olarak bir argüman sağlanmalıdır:

```jldoctest pointtype
julia> Point{Float64}(1.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]

julia> Point{Float64}(1.0, 2.0, 3.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64, ::Float64, ::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]
```

Sadece parametreli türler için bir varsayılan yapıcı oluşturulur, çünkü onu geçersiz kılmak mümkün değildir. Bu yapıcı, herhangi bir argümanı kabul eder ve bunları alan türlerine dönüştürür.

Birçok durumda, oluşturmak istediğiniz `Point` nesnesinin türünü sağlamak gereksizdir, çünkü yapıcı çağrısındaki argümanların türleri zaten dolaylı olarak tür bilgisi sağlar. Bu nedenle, parametre türü `T`'nin ima edilen değeri belirsiz olmadığında, `Point`'i bir yapıcı olarak da uygulayabilirsiniz:

```jldoctest pointtype
julia> p1 = Point(1.0,2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p1)
Point{Float64}

julia> p2 = Point(1,2)
Point{Int64}(1, 2)

julia> typeof(p2)
Point{Int64}
```

`Point` durumunda, `T` türü yalnızca `Point`'e verilen iki argümanın aynı türde olması durumunda belirsiz bir şekilde ima edilir. Bu durum söz konusu olmadığında, yapıcı [`MethodError`](@ref) ile başarısız olacaktır:

```jldoctest pointtype
julia> Point(1,2.5)
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T
   @ Main none:2

Stacktrace:
[...]
```

Karma yöntemleri, böyle karışık durumları uygun bir şekilde ele almak için tanımlanabilir, ancak bu [Constructors](@ref man-constructors)'te daha sonra tartışılacaktır.

### Parametric Abstract Types

Parametrik soyut tür bildirimleri, çok benzer bir şekilde, soyut türlerin bir koleksiyonunu bildirir:

```jldoctest pointytype
julia> abstract type Pointy{T} end
```

Bu beyan ile `Pointy{T}`, `T`'nin her türü veya tam sayı değeri için ayrı bir soyut türdür. Parametrik bileşik türlerde olduğu gibi, her böyle örnek `Pointy`'nin bir alt türüdür:

```jldoctest pointytype
julia> Pointy{Int64} <: Pointy
true

julia> Pointy{1} <: Pointy
true
```

Parametrik soyut türler, parametrik bileşik türler gibi değişmezdir:

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{Real}
false

julia> Pointy{Real} <: Pointy{Float64}
false
```

`Pointy{<:Gerçek}` notasyonu, Julia'daki *kovaryant* bir türü ifade etmek için kullanılabilirken, `Pointy{>:Int}` *kontravaryant* bir türün analoğu olarak kullanılabilir, ancak teknik olarak bunlar *tür kümelerini* temsil eder (bkz. [UnionAll Types](@ref)).

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{<:Real}
true

julia> Pointy{Real} <: Pointy{>:Int}
true
```

Eski soyut türler, somut türler üzerinde yararlı bir tür hiyerarşisi oluşturmak için hizmet ettiğinden, parametrik soyut türler de parametrik bileşik türler ile ilgili olarak aynı amaca hizmet eder. Örneğin, `Point{T}`'yi `Pointy{T}`'nin bir alt türü olarak aşağıdaki gibi tanımlamış olabiliriz:

```jldoctest pointytype
julia> struct Point{T} <: Pointy{T}
           x::T
           y::T
       end
```

Verilen böyle bir bildirimle, her `T` seçimi için `Point{T}`, `Pointy{T}`'nin bir alt türü olarak kabul edilir:

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Float64}
true

julia> Point{Real} <: Pointy{Real}
true

julia> Point{AbstractString} <: Pointy{AbstractString}
true
```

Bu ilişki de değişmezdir:

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Real}
false

julia> Point{Float64} <: Pointy{<:Real}
true
```

Parametrik soyut türler, örneğin `Pointy`, belirli bir türün özelliklerini tanımlamak için kullanılır. Bu türler, belirli bir türün davranışını ve özelliklerini tanımlarken, aynı zamanda esneklik sağlar. Örneğin, yalnızca bir koordinat gerektiren bir nokta benzeri uygulama oluşturduğumuzda, bu türler, uygulamanın yalnızca belirli bir durumda nasıl çalışacağını tanımlamak için kullanılabilir. 

```jldoctest pointytype
julia> struct DiagPoint{T} <: Pointy{T}
           x::T
       end
```

Artık hem `Point{Float64}` hem de `DiagPoint{Float64}`, `Pointy{Float64}` soyutlamasının uygulamalarıdır ve benzer şekilde `T` türü için her diğer olası seçimde de geçerlidir. Bu, `Point` ve `DiagPoint` için uygulanmış olan tüm `Pointy` nesneleri tarafından paylaşılan ortak bir arayüze programlama yapmayı sağlar. Ancak, bunu tam olarak göstermek mümkün değildir; bununla birlikte, bir sonraki bölümde, [Methods](@ref)'da yöntemler ve dağıtım tanıtılana kadar.

Belirli durumlarda, tür parametrelerinin tüm olası türler üzerinde serbestçe değişmesi mantıklı olmayabilir. Bu tür durumlarda, `T`'nin aralığını şu şekilde kısıtlayabilirsiniz:

```jldoctest realpointytype
julia> abstract type Pointy{T<:Real} end
```

Böyle bir beyan ile, `T` yerine [`Real`](@ref) alt türü olan herhangi bir türü kullanmak kabul edilebilir, ancak `Real` alt türü olmayan türler kullanılamaz:

```jldoctest realpointytype
julia> Pointy{Float64}
Pointy{Float64}

julia> Pointy{Real}
Pointy{Real}

julia> Pointy{AbstractString}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got Type{AbstractString}

julia> Pointy{1}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got a value of type Int64
```

Parametrik bileşik türler için parametreler aynı şekilde kısıtlanabilir:

```julia
struct Point{T<:Real} <: Pointy{T}
    x::T
    y::T
end
```

Gerçek dünya örneği olarak, bu parametreli tür makinelerinin nasıl faydalı olabileceğine dair, Julia'nın [`Rational`](@ref) değişmez türünün gerçek tanımını burada veriyoruz (basitlik açısından yapıcıyı burada atlıyoruz), tam bir tam sayı oranını temsil ediyor:

```julia
struct Rational{T<:Integer} <: Real
    num::T
    den::T
end
```

Sadece tam sayı değerlerinin oranlarını almak mantıklıdır, bu nedenle `T` parametre türü [`Integer`](@ref) alt türü ile sınırlıdır ve tam sayıların oranı, gerçek sayı doğrusunda bir değeri temsil eder, bu nedenle herhangi bir [`Rational`](@ref) [`Real`](@ref) soyutlamasının bir örneğidir.

### Tuple Types

Tuplelar, bir fonksiyonun argümanlarının bir soyutlamasıdır - fonksiyonun kendisi olmadan. Bir fonksiyonun argümanlarının belirgin yönleri, bunların sırası ve türleridir. Bu nedenle, bir tuple türü, her bir parametrenin bir alanın türü olduğu parametreli değişmez bir türe benzer. Örneğin, 2 elemanlı bir tuple türü aşağıdaki değişmez türe benzer:

```julia
struct Tuple2{A,B}
    a::A
    b::B
end
```

Ancak, üç ana fark vardır:

  * Tuple türleri herhangi bir sayıda parametreye sahip olabilir.
  * Tuple türleri parametrelerinde *kovaryant*tır: `Tuple{Int}` `Tuple{Any}`'nin bir alt türüdür. Bu nedenle `Tuple{Any}` soyut bir tür olarak kabul edilir ve tuple türleri yalnızca parametreleri somut olduğunda somut hale gelir.
  * Demetler alan adlarına sahip değildir; alanlara yalnızca indeksle erişilir.

Tuple değerleri parantezler ve virgüller ile yazılır. Bir tuple oluşturulduğunda, talep üzerine uygun bir tuple türü üretilir:

```jldoctest
julia> typeof((1,"foo",2.5))
Tuple{Int64, String, Float64}
```

Kovaryansın sonuçlarını not edin:

```jldoctest
julia> Tuple{Int,AbstractString} <: Tuple{Real,Any}
true

julia> Tuple{Int,AbstractString} <: Tuple{Real,Real}
false

julia> Tuple{Int,AbstractString} <: Tuple{Real,}
false
```

Sezgisel olarak, bu, bir fonksiyonun argümanlarının türünün, fonksiyonun imzasının bir alt türü olmasıyla (imza eşleştiğinde) ilişkilidir.

### Vararg Tuple Types

Bir tuple türünün son parametresi, herhangi bir sayıda son elemanı belirtmek için kullanılan özel değer [`Vararg`](@ref) olabilir:

```jldoctest
julia> mytupletype = Tuple{AbstractString,Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```

Ayrıca `Vararg{T}`, `T` türünden sıfır veya daha fazla öğeye karşılık gelir. Vararg demet türleri, varargs yöntemleri tarafından kabul edilen argümanları temsil etmek için kullanılır (bkz. [Varargs Functions](@ref)).

Özel değer `Vararg{T,N}` (bir tuple türünün son parametresi olarak kullanıldığında) tam olarak `N` adet `T` türünde elemanı ifade eder. `NTuple{N,T}` ise `Tuple{Vararg{T,N}}` için pratik bir takma isimdir, yani tam olarak `N` adet `T` türünde eleman içeren bir tuple türüdür.

### Named Tuple Types

Adlandırılmış demetler, [`NamedTuple`](@ref) türünün örnekleridir ve iki parametreye sahiptir: alan adlarını veren bir sembol demeti ve alan türlerini veren bir demet türü. Kolaylık olması açısından, `NamedTuple` türleri, bu türleri `key::Type` bildirimleri aracılığıyla `struct` benzeri bir sözdizimi ile tanımlamak için [`@NamedTuple`](@ref) makrosu kullanılarak yazdırılır; burada atlanan `::Type`, `::Any` ile karşılık gelir.

```jldoctest
julia> typeof((a=1,b="hello")) # prints in macro form
@NamedTuple{a::Int64, b::String}

julia> NamedTuple{(:a, :b), Tuple{Int64, String}} # long form of the type
@NamedTuple{a::Int64, b::String}
```

`@NamedTuple` makrosunun `begin ... end` biçimi, bildirimlerin birden fazla satıra bölünmesine izin verir (bir yapı bildirimiyle benzer şekilde), ancak aksi takdirde eşdeğerdir:

```jldoctest
julia> @NamedTuple begin
           a::Int
           b::String
       end
@NamedTuple{a::Int64, b::String}
```

Bir `NamedTuple` türü, tek bir demet argümanı kabul eden bir yapıcı olarak kullanılabilir. Oluşturulan `NamedTuple` türü, her iki parametrenin de belirtildiği somut bir tür veya yalnızca alan adlarını belirten bir tür olabilir:

```jldoctest
julia> @NamedTuple{a::Float32,b::String}((1, ""))
(a = 1.0f0, b = "")

julia> NamedTuple{(:a, :b)}((1, ""))
(a = 1, b = "")
```

Eğer alan türleri belirtilmişse, argümanlar dönüştürülür. Aksi takdirde argümanların türleri doğrudan kullanılır.

### Parametric Primitive Types

Temel türler parametrik olarak da tanımlanabilir. Örneğin, işaretçiler, Julia'da şu şekilde tanımlanacak olan temel türler olarak temsil edilir:

```julia
# 32-bit system:
primitive type Ptr{T} 32 end

# 64-bit system:
primitive type Ptr{T} 64 end
```

Bu bildirimlerin tipik parametrik bileşik türlere kıyasla biraz garip olan özelliği, `T` tür parametresinin türün tanımında kullanılmamasıdır – bu sadece soyut bir etiket olup, yalnızca tür parametreleriyle farklılaştırılan, aynı yapıya sahip bir tür ailesini tanımlar. Böylece, `Ptr{Float64}` ve `Ptr{Int64}` farklı türlerdir, her ne kadar aynı temsillere sahip olsalar da. Ve elbette, tüm belirli işaretçi türleri, şemsiye [`Ptr`](@ref) türünün alt türleridir:

```jldoctest
julia> Ptr{Float64} <: Ptr
true

julia> Ptr{Int64} <: Ptr
true
```

## UnionAll Types

Biz, `Ptr` gibi bir parametreli türün tüm örneklerinin süper türü olarak davrandığını söyledik (`Ptr{Int64}` vb.). Bu nasıl çalışıyor? `Ptr` kendisi normal bir veri türü olamaz, çünkü referans verilen verinin türünü bilmeden bu türün bellek işlemleri için açıkça kullanılamaz. Cevap, `Ptr` (veya `Array` gibi diğer parametreli türler) [`UnionAll`](@ref) türü olarak adlandırılan farklı bir türdür. Böyle bir tür, bazı parametrelerin tüm değerleri için türlerin *tekrarlanan birleşimini* ifade eder.

`UnionAll` türleri genellikle `where` anahtar kelimesi kullanılarak yazılır. Örneğin, `Ptr` daha doğru bir şekilde `Ptr{T} where T` olarak yazılabilir; bu, `T` için bazı değerler olan tüm `Ptr{T}` türündeki değerleri ifade eder. Bu bağlamda, `T` parametresi genellikle "tip değişkeni" olarak da adlandırılır, çünkü bu, türler üzerinde değişen bir değişken gibidir. Her `where`, tek bir tip değişkeni tanıtır, bu nedenle bu ifadeler, birden fazla parametreye sahip türler için iç içe geçmiş durumdadır; örneğin `Array{T,N} where N where T`.

`A{B,C}` tür uygulama sözdizimi, `A`'nın bir `UnionAll` türü olmasını gerektirir ve önce `B`'yi `A`'daki en dıştaki tür değişkeninin yerine koyar. Sonuç, `C`'nin daha sonra yerleştirileceği başka bir `UnionAll` türü olmalıdır. Bu nedenle `A{B,C}`, `A{B}{C}` ile eşdeğerdir. Bu, `Array{Float64}` gibi bir türü kısmen başlatmanın mümkün olmasının nedenini açıklar: ilk parametre değeri sabitlenmiştir, ancak ikincisi hala tüm olası değerler üzerinde değişir. Açık `where` sözdizimini kullanarak, parametrelerin herhangi bir alt kümesi sabitlenebilir. Örneğin, tüm 1 boyutlu dizilerin türü `Array{T,1} where T` olarak yazılabilir.

Tip değişkenleri alt tür ilişkileri ile kısıtlanabilir. `Array{T} where T<:Integer`, eleman türü [`Integer`](@ref) olan tüm dizilere atıfta bulunur. `Array{<:Integer}` sözdizimi, `Array{T} where T<:Integer` için pratik bir kısayoldur. Tip değişkenleri hem alt hem de üst sınırları olabilir. `Array{T} where Int<:T<:Number`, `Int` içerebilen [`Number`](@ref) dizilerinin tümüne atıfta bulunur (çünkü `T`, en az `Int` kadar büyük olmalıdır). `where T>:Int` sözdizimi, bir tip değişkeninin yalnızca alt sınırını belirtmek için de çalışır ve `Array{>:Int}`, `Array{T} where T>:Int` ile eşdeğerdir.

`where` ifadeleri iç içe geçtiğinden, tür değişkeni sınırları dıştaki tür değişkenlerine atıfta bulunabilir. Örneğin `Tuple{T,Array{S}} where S<:AbstractArray{T} where T<:Real`, ilk elemanı bazı [`Real`](@ref) olan 2-tuple'ları ve ikinci elemanı ilk tuple elemanının türünü içeren herhangi bir türde dizinin `Array`'ini ifade eder.

`where` anahtar kelimesi, daha karmaşık bir bildirimin içinde iç içe yer alabilir. Örneğin, aşağıdaki bildirimlerle oluşturulan iki türü düşünün:

```jldoctest
julia> const T1 = Array{Array{T, 1} where T, 1}
Vector{Vector} (alias for Array{Array{T, 1} where T, 1})

julia> const T2 = Array{Array{T, 1}, 1} where T
Array{Vector{T}, 1} where T
```

`T1` türü, 1 boyutlu dizilerden oluşan 1 boyutlu bir dizi tanımlar; iç dizilerin her biri aynı türdeki nesnelerden oluşur, ancak bu tür bir iç diziden diğerine değişebilir. Öte yandan, `T2` türü, iç dizilerin hepsinin aynı türde olması gereken 1 boyutlu dizilerden oluşan 1 boyutlu bir dizi tanımlar. `T2` soyut bir türdür; örneğin, `Array{Array{Int,1},1} <: T2` iken, `T1` somut bir türdür. Sonuç olarak, `T1` sıfır argümanlı bir yapıcı ile oluşturulabilir `a=T1()` ancak `T2` oluşturulamaz.

Böyle türleri adlandırmak için, işlev tanımı sözdiziminin kısa biçimine benzer bir sözdizimi vardır:

```julia
Vector{T} = Array{T, 1}
```

Bu, `const Vector = Array{T,1} where T` ile eşdeğerdir. `Vector{Float64}` yazmak, `Array{Float64,1}` yazmakla eşdeğerdir ve şemsiye türü `Vector`, ikinci parametrenin – dizi boyutlarının sayısının – 1 olduğu tüm `Array` nesnelerini içerir, eleman türü ne olursa olsun. Parametrik türlerin her zaman tam olarak belirtilmesi gereken dillerde bu pek yardımcı değildir, ancak Julia'da bu, herhangi bir eleman türündeki tüm bir boyutlu yoğun dizileri içeren soyut tür için sadece `Vector` yazmanıza olanak tanır.

## [Singleton types](@id man-singleton-types)

Değiştirilemez bileşik türler, alanı olmayan *singleton* olarak adlandırılır. Resmi olarak, eğer

1. `T`, değiştirilemez bir bileşik türdür (yani `struct` ile tanımlanmıştır),
2. `a T ise && b T ise` demektir `a === b`,

o zaman `T` bir singleton türüdür.[^2] [`Base.issingletontype`](@ref) bir türün singleton türü olup olmadığını kontrol etmek için kullanılabilir. [Abstract types](@ref man-abstract-types) yapısı gereği singleton türler olamaz.

Tanım gereği, bu türlerin yalnızca bir örneği olabileceği sonucuna varılır:

```jldoctest
julia> struct NoFields
       end

julia> NoFields() === NoFields()
true

julia> Base.issingletontype(NoFields)
true
```

[`===`](@ref) fonksiyonu, oluşturulan `NoFields` örneklerinin aslında bir ve aynı olduğunu doğrular.

Parametrik türler yukarıdaki koşul sağlandığında tekil türler olabilir. Örneğin,

```jldoctest
julia> struct NoFieldsParam{T}
       end

julia> Base.issingletontype(NoFieldsParam) # Can't be a singleton type ...
false

julia> NoFieldsParam{Int}() isa NoFieldsParam # ... because it has ...
true

julia> NoFieldsParam{Bool}() isa NoFieldsParam # ... multiple instances.
true

julia> Base.issingletontype(NoFieldsParam{Int}) # Parametrized, it is a singleton.
true

julia> NoFieldsParam{Int}() === NoFieldsParam{Int}()
true
```

## Types of functions

Her fonksiyonun kendi türü vardır, bu da `Function`'ın bir alt türüdür.

```jldoctest foo41
julia> foo41(x) = x + 1
foo41 (generic function with 1 method)

julia> typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)
```

`typeof(foo41)` ifadesinin kendisi olarak yazdırıldığını not edin. Bu, yalnızca bir yazdırma konvansiyonudur, çünkü bu, diğer herhangi bir değer gibi kullanılabilen birinci sınıf bir nesnedir:

```jldoctest foo41
julia> T = typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)

julia> T <: Function
true
```

Üst düzeyde tanımlanan fonksiyon türleri tekil nesnelerdir. Gerekirse, bunları [`===`](@ref) ile karşılaştırabilirsiniz.

[Closures](@ref man-anonymous-functions) ayrıca genellikle `#<sayı>` ile biten adlarla yazdırılan kendi türlerine sahiptir. Farklı konumlarda tanımlanan işlevler için adlar ve türler ayrıdır, ancak oturumlar arasında aynı şekilde yazdırılacağı garanti edilmez.

```jldoctest; filter = r"[0-9\.]+"
julia> typeof(x -> x + 1)
var"#9#10"
```

Kapatma türleri mutlaka tekil değildir.

```jldoctest
julia> addy(y) = x -> x + y
addy (generic function with 1 method)

julia> typeof(addy(1)) === typeof(addy(2))
true

julia> addy(1) === addy(2)
false

julia> Base.issingletontype(typeof(addy(1)))
false
```

## [`Type{T}` type selectors](@id man-typet-type)

Her tür `T` için, `Type{T}` yalnızca `T` nesnesinin bir örneği olan soyut bir parametrik türdür. [Parametric Methods](@ref) ve [conversions](@ref conversion-and-promotion) konularını tartışana kadar, bu yapının faydasını açıklamak zordur, ancak kısaca, belirli türler üzerinde *değerler* olarak işlev davranışını özelleştirmeye olanak tanır. Bu, bir türün, argümanlarından birinin türüyle ima edilmek yerine, açık bir argüman olarak verildiği durumlarda (özellikle parametrik olanlar) yöntemler yazmak için yararlıdır.

Tanım biraz zor anlaşıldığı için, bazı örneklere bakalım:

```jldoctest
julia> isa(Float64, Type{Float64})
true

julia> isa(Real, Type{Float64})
false

julia> isa(Real, Type{Real})
true

julia> isa(Float64, Type{Real})
false
```

Başka bir deyişle, [`isa(A, Type{B})`](@ref) yalnızca `A` ve `B` aynı nesne olduğunda ve o nesne bir tür olduğunda doğrudur.

Özellikle, parametreli türler [invariant](@ref man-parametric-composite-types) olduğundan, şunları elde ediyoruz:

```jldoctest
julia> struct TypeParamExample{T}
           x::T
       end

julia> TypeParamExample isa Type{TypeParamExample}
true

julia> TypeParamExample{Int} isa Type{TypeParamExample}
false

julia> TypeParamExample{Int} isa Type{TypeParamExample{Int}}
true
```

Parametresiz, `Type` basitçe tüm tür nesnelerinin örnekleri olan soyut bir türdür:

```jldoctest
julia> isa(Type{Float64}, Type)
true

julia> isa(Float64, Type)
true

julia> isa(Real, Type)
true
```

Herhangi bir nesne bir tür değilse, `Type`'ın bir örneği değildir:

```jldoctest
julia> isa(1, Type)
false

julia> isa("foo", Type)
false
```

While `Type` is part of Julia's type hierarchy like any other abstract parametric type, it is not commonly used outside method signatures except in some special cases. Another important use case for `Type` is sharpening field types which would otherwise be captured less precisely, e.g. as [`DataType`](@ref man-declared-types) in the example below where the default constructor could lead to performance problems in code relying on the precise wrapped type (similarly to [abstract type parameters](@ref man-performance-abstract-container)).

```jldoctest
julia> struct WrapType{T}
       value::T
       end

julia> WrapType(Float64) # default constructor, note DataType
WrapType{DataType}(Float64)

julia> WrapType(::Type{T}) where T = WrapType{Type{T}}(T)
WrapType

julia> WrapType(Float64) # sharpened constructor, note more precise Type{Float64}
WrapType{Type{Float64}}(Float64)
```

## Type Aliases

Bazen zaten ifade edilebilir bir tür için yeni bir ad tanıtmak kullanışlıdır. Bu, basit bir atama ifadesi ile yapılabilir. Örneğin, `UInt` ya [`UInt32`](@ref) ya da [`UInt64`](@ref) olarak, sistemdeki işaretçilerin boyutuna uygun olarak takma ad verilmiştir:

```julia-repl
# 32-bit system:
julia> UInt
UInt32

# 64-bit system:
julia> UInt
UInt64
```

Bu, `base/boot.jl` dosyasındaki aşağıdaki kod aracılığıyla gerçekleştirilir:

```julia
if Int === Int64
    const UInt = UInt64
else
    const UInt = UInt32
end
```

Elbette, bu `Int`'in hangi takma adla tanımlandığına bağlıdır - ancak bu, doğru tür olarak önceden tanımlanmıştır - ya [`Int32`](@ref) ya da [`Int64`](@ref).

(Not edin `Int` gibi, `Float` belirli bir boyut için bir tür takma adı olarak mevcut değildir [`AbstractFloat`](@ref). Tam sayı kayıtları ile, `Int`'in boyutu o makinedeki yerel bir işaretçinin boyutunu yansıtırken, kayan nokta kayıt boyutları IEEE-754 standardı tarafından belirtilmiştir.)

Tip adı takma adları parametreli olabilir:

```jldoctest
julia> const Family{T} = Set{T}
Set

julia> Family{Char} === Set{Char}
true
```

## Operations on Types

Julia'daki türler nesne oldukları için, sıradan fonksiyonlar bunlar üzerinde işlem yapabilir. Türlerle çalışmak veya onları keşfetmek için özellikle yararlı olan bazı fonksiyonlar zaten tanıtılmıştır; bunlardan biri, sol operatörünün sağ operatörünün bir alt türü olup olmadığını gösteren `<:` operatörüdür.

[`isa`](@ref) fonksiyonu bir nesnenin belirli bir türde olup olmadığını test eder ve true veya false döner:

```jldoctest
julia> isa(1, Int)
true

julia> isa(1, AbstractFloat)
false
```

[`typeof`](@ref) fonksiyonu, kılavuzda örneklerde zaten kullanılmıştır, argümanının türünü döndürür. Yukarıda belirtildiği gibi, türler nesne olduğundan, onların da türleri vardır ve biz de bu türlerin ne olduğunu sorabiliriz:

```jldoctest
julia> typeof(Rational{Int})
DataType

julia> typeof(Union{Real,String})
Union
```

Ne olursa olsun süreci tekrar edersek? Bir türün türü nedir? Olması gerektiği gibi, türler tümüyle bileşik değerlerdir ve bu nedenle hepsinin `DataType` türü vardır:

```jldoctest
julia> typeof(DataType)
DataType

julia> typeof(Union)
DataType
```

`DataType` kendi türüdür.

Başka bir işlem, bazı türlere uygulanan [`supertype`](@ref) olup, bir türün süper türünü ortaya çıkarır. Sadece beyan edilen türler (`DataType`) belirsiz olmayan süper türlere sahiptir:

```jldoctest
julia> supertype(Float64)
AbstractFloat

julia> supertype(Number)
Any

julia> supertype(AbstractString)
Any

julia> supertype(Any)
Any
```

Eğer [`supertype`](@ref)'yı diğer tür nesnelere (veya tür olmayan nesnelere) uygularsanız, bir [`MethodError`](@ref) hatası oluşur:

```jldoctest; filter = r"Closest candidates.*"s
julia> supertype(Union{Float64,Int64})
ERROR: MethodError: no method matching supertype(::Type{Union{Float64, Int64}})
The function `supertype` exists, but no method is defined for this combination of argument types.

Closest candidates are:
[...]
```

## [Custom pretty-printing](@id man-custom-pretty-printing)

Sıklıkla, bir türün örneklerinin nasıl görüntüleneceğini özelleştirmek istenir. Bu, [`show`](@ref) fonksiyonunu aşırı yükleyerek gerçekleştirilir. Örneğin, karmaşık sayıları kutupsal formda temsil etmek için bir tür tanımlarsak:

```jldoctest polartype
julia> struct Polar{T<:Real} <: Number
           r::T
           Θ::T
       end

julia> Polar(r::Real,Θ::Real) = Polar(promote(r,Θ)...)
Polar
```

Burada, farklı [`Real`](@ref) türünde argümanlar alabilmesi için özel bir yapıcı fonksiyonu ekledik ve bunları ortak bir türe yükselttik (bkz. [Constructors](@ref man-constructors) ve [Conversion and Promotion](@ref conversion-and-promotion)). (Elbette, bunun bir [`Number`](@ref) gibi davranabilmesi için birçok başka yöntemi de tanımlamamız gerekecek, örneğin `+`, `*`, `one`, `zero`, yükseltme kuralları vb.) Varsayılan olarak, bu türün örnekleri oldukça basit bir şekilde, tür adı ve alan değerleri hakkında bilgi gösterir, örneğin `Polar{Float64}(3.0,4.0)`.

Eğer bunu `3.0 * exp(4.0im)` olarak görüntülemek istiyorsak, bir nesneyi belirli bir çıktı nesnesine `io` (bir dosya, terminal, tampon vb. temsil eden; bkz. [Networking and Streams](@ref)) yazdırmak için aşağıdaki yöntemi tanımlamalıyız:

```jldoctest polartype
julia> Base.show(io::IO, z::Polar) = print(io, z.r, " * exp(", z.Θ, "im)")
```

`Polar` nesnelerinin görüntülenmesi üzerinde daha ayrıntılı kontrol mümkündür. Özellikle, bazen REPL ve diğer etkileşimli ortamlarda tek bir nesneyi görüntülemek için kullanılan ayrıntılı çok satırlı yazdırma formatına ve ayrıca [`print`](@ref) için veya nesneyi başka bir nesnenin parçası olarak (örneğin bir dizide) görüntülemek için kullanılan daha kompakt tek satırlı formata ihtiyaç duyulabilir. Varsayılan olarak `show(io, z)` fonksiyonu her iki durumda da çağrılır, ancak `text/plain` MIME türünü ikinci argüman olarak alan `show` fonksiyonunun üç argümanlı bir formunu aşırı yükleyerek bir nesneyi görüntülemek için *farklı* bir çok satırlı format tanımlayabilirsiniz (bkz. [Multimedia I/O](@ref Multimedia-I/O)), örneğin:

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/plain", z::Polar{T}) where{T} =
           print(io, "Polar{$T} complex number:\n   ", z)
```

(Burada `print(..., z)` ifadesi, 2-argümanlı `show(io, z)` metodunu çağıracaktır.) Bu sonuçta:

```jldoctest polartype
julia> Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> [Polar(3, 4.0), Polar(4.0,5.3)]
2-element Vector{Polar{Float64}}:
 3.0 * exp(4.0im)
 4.0 * exp(5.3im)
```

tek satırlık `show(io, z)` biçiminin `Polar` değerlerinin bir dizisi için hala kullanıldığı yer. Teknik olarak, REPL bir satırın sonucunu görüntülemek için `display(z)` çağrısını yapar; bu, varsayılan olarak `show(stdout, MIME("text/plain"), z)`'ye, bu da varsayılan olarak `show(stdout, z)`'ye döner, ancak yeni [`display`](@ref) yöntemleri tanımlamamalısınız, aksi takdirde yeni bir çoklu ortam görüntüleme işleyici tanımlıyorsanız (bkz. [Multimedia I/O](@ref Multimedia-I/O)).

Ayrıca, bu tür ortamların (örneğin IJulia) desteklediği nesnelerin daha zengin bir şekilde görüntülenmesini sağlamak için diğer MIME türleri için de `show` yöntemleri tanımlayabilirsiniz (HTML, resimler vb.). Örneğin, `Polar` nesnelerinin üst simgeler ve italik ile biçimlendirilmiş HTML görüntülemesini şu şekilde tanımlayabiliriz:

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/html", z::Polar{T}) where {T} =
           println(io, "<code>Polar{$T}</code> complex number: ",
                   z.r, " <i>e</i><sup>", z.Θ, " <i>i</i></sup>")
```

Bir `Polar` nesnesi, HTML görüntülemeyi destekleyen bir ortamda otomatik olarak görüntülenecektir, ancak isterseniz HTML çıktısı almak için `show` fonksiyonunu manuel olarak çağırabilirsiniz:

```jldoctest polartype
julia> show(stdout, "text/html", Polar(3.0,4.0))
<code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup>
```

```@raw html
<p>An HTML renderer would display this as: <code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup></p>
```

Bir kural olarak, tek satırlık `show` yöntemi, gösterilen nesneyi oluşturmak için geçerli bir Julia ifadesi yazdırmalıdır. Bu `show` yöntemi, yukarıdaki `Polar` için tek satırlık `show` yöntemimizdeki çarpma operatörü (`*`) gibi infiks operatörleri içeriyorsa, başka bir nesnenin parçası olarak yazdırıldığında doğru bir şekilde ayrıştırılmayabilir. Bunu görmek için, belirli bir `Polar` türü örneğinin karesini alan ifade nesnesini düşünün (bkz. [Program representation](@ref)):

```jldoctest polartype
julia> a = Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> print(:($a^2))
3.0 * exp(4.0im) ^ 2
```

Çünkü `^` operatörünün önceliği `*` operatöründen daha yüksektir (bkz. [Operator Precedence and Associativity](@ref)), bu çıktı `a ^ 2` ifadesini doğru bir şekilde temsil etmez; bu ifade `(3.0 * exp(4.0im)) ^ 2` ile eşit olmalıdır. Bu sorunu çözmek için, yazdırma sırasında ifade nesnesi tarafından dahili olarak çağrılan `Base.show_unquoted(io::IO, z::Polar, indent::Int, precedence::Int)` için özel bir yöntem oluşturmalıyız:

```jldoctest polartype
julia> function Base.show_unquoted(io::IO, z::Polar, ::Int, precedence::Int)
           if Base.operator_precedence(:*) <= precedence
               print(io, "(")
               show(io, z)
               print(io, ")")
           else
               show(io, z)
           end
       end

julia> :($a^2)
:((3.0 * exp(4.0im)) ^ 2)
```

Yukarıda tanımlanan yöntem, çağırma operatörünün önceliği çarpmanın önceliği ile aynı veya daha yüksek olduğunda `show` çağrısının etrafına parantez ekler. Bu kontrol, parantezsiz doğru bir şekilde ayrıştırılan ifadelerin (örneğin `:($a + 2)` ve `:($a == 2)`) yazdırıldığında parantezleri atlamasına olanak tanır:

```jldoctest polartype
julia> :($a + 2)
:(3.0 * exp(4.0im) + 2)

julia> :($a == 2)
:(3.0 * exp(4.0im) == 2)
```

Bazen, `show` yöntemlerinin davranışını bağlamına göre ayarlamak faydalı olabilir. Bu, bağlamsal özelliklerin bir sarmalanmış IO akışı ile birlikte geçilmesine olanak tanıyan [`IOContext`](@ref) türü aracılığıyla gerçekleştirilebilir. Örneğin, `:compact` özelliği `true` olarak ayarlandığında `show` yöntemimizde daha kısa bir temsil oluşturabiliriz; eğer özellik `false` veya yoksa uzun temsile geri döneriz:

```jldoctest polartype
julia> function Base.show(io::IO, z::Polar)
           if get(io, :compact, false)::Bool
               print(io, z.r, "ℯ", z.Θ, "im")
           else
               print(io, z.r, " * exp(", z.Θ, "im)")
           end
       end
```

Bu yeni kompakt temsil, geçirilen IO akışının `:compact` özelliği ayarlanmış bir `IOContext` nesnesi olduğu durumlarda kullanılacaktır. Özellikle, yatay alanın sınırlı olduğu çoklu sütunlara sahip dizileri yazdırırken bu durum geçerlidir:

```jldoctest polartype
julia> show(IOContext(stdout, :compact=>true), Polar(3, 4.0))
3.0ℯ4.0im

julia> [Polar(3, 4.0) Polar(4.0,5.3)]
1×2 Matrix{Polar{Float64}}:
 3.0ℯ4.0im  4.0ℯ5.3im
```

[`IOContext`](@ref) belgesine bakarak yazdırma ayarlarını düzenlemek için kullanılabilecek yaygın özelliklerin bir listesini bulabilirsiniz.

## "Value types"

Julia'da, `true` veya `false` gibi bir *değer* üzerinde dispatch yapamazsınız. Ancak, parametreli türler üzerinde dispatch yapabilirsiniz ve Julia, "sade bit" değerlerini (Türler, Semboller, Tam sayılar, kayan nokta sayıları, demetler vb.) tür parametreleri olarak dahil etmenize izin verir. Yaygın bir örnek, `Array{T,N}` içindeki boyut parametresidir; burada `T` bir türdür (örneğin, [`Float64`](@ref)), ancak `N` sadece bir `Int`'dir.

Kendi özel türlerinizi oluşturabilir ve bunları parametre olarak değerler alacak şekilde kullanarak özel türlerin dağıtımını kontrol edebilirsiniz. Bu fikri açıklamak için, parametreli tür `Val{x}` ve onun yapıcısı `Val(x) = Val{x}()`, daha karmaşık bir hiyerarşiye ihtiyaç duymadığınız durumlar için bu tekniği kullanmanın alışılmış bir yolu olarak tanıtalım.

[`Val`](@ref) olarak tanımlanmıştır:

```jldoctest valtype
julia> struct Val{x}
       end

julia> Val(x) = Val{x}()
Val
```

`Val` uygulamasasında daha fazlası yoktur. Julia'nın standart kütüphanesindeki bazı fonksiyonlar `Val` örneklerini argüman olarak kabul eder ve kendi fonksiyonlarınızı yazmak için de bunu kullanabilirsiniz. Örneğin:

```jldoctest valtype
julia> firstlast(::Val{true}) = "First"
firstlast (generic function with 1 method)

julia> firstlast(::Val{false}) = "Last"
firstlast (generic function with 2 methods)

julia> firstlast(Val(true))
"First"

julia> firstlast(Val(false))
"Last"
```

Julia'da tutarlılık için, çağrı noktasının her zaman bir `Val` *örneği* geçirmesi gerekir, yani `foo(Val(:bar))` kullanın, `foo(Val{:bar})` yerine.

Parametrik "değer" türlerini, özellikle de `Val`'ı yanlış kullanmanın son derece kolay olduğunu belirtmek gerekir; olumsuz durumlarda, kodunuzun performansını çok *kötü* hale getirebilirsiniz. Özellikle, yukarıda gösterildiği gibi gerçek kod yazmak istemezsiniz. `Val`'ın doğru (ve yanlış) kullanımları hakkında daha fazla bilgi için lütfen [the more extensive discussion in the performance tips](@ref man-performance-value-type) okuyun.

[^1]: "Small" is defined by the `max_union_splitting` configuration, which currently defaults to 4.

[^2]: A few popular languages have singleton types, including Haskell, Scala and Ruby.
