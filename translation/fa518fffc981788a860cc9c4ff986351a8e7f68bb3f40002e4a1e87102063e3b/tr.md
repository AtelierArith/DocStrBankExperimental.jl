# [Modules](@id modules)

Julia'da modüller, kodu tutarlı birimlere organize etmeye yardımcı olur. Söz dizimi olarak `module NameOfModule ... end` içinde sınırlıdırlar ve aşağıdaki özelliklere sahiptirler:

1. Modüller, her biri yeni bir global kapsam tanıtan ayrı ad alanlarıdır. Bu, aynı ismin farklı işlevler veya global değişkenler için çelişki olmadan kullanılmasına olanak tanıdığı için faydalıdır, yeter ki bunlar ayrı modüllerde olsun.
2. Modüller, ayrıntılı ad alanı yönetimi için olanaklar sunar: her biri `export` ettiği ve `public` olarak işaretlediği bir isimler seti tanımlar ve `using` ve `import` ile diğer modüllerden isimler alabilir (bunları aşağıda açıklıyoruz).
3. Modüller daha hızlı yükleme için önceden derlenebilir ve çalışma zamanı başlatması için kod içerebilir.

Genellikle, daha büyük Julia paketlerinde modül kodunun dosyalara düzenlendiğini göreceksiniz, örn.

```julia
module SomeModule

# export, public, using, import statements are usually here; we discuss these below

include("file1.jl")
include("file2.jl")

end
```

Dosyalar ve dosya adları genellikle modüllerle ilgisizdir; modüller yalnızca modül ifadeleriyle ilişkilidir. Bir modül başına birden fazla dosya ve bir dosya başına birden fazla modül olabilir. `include`, kaynak dosyanın içeriğinin dahil eden modülün global kapsamında değerlendirilmiş gibi davranır. Bu bölümde, kısa ve basit örnekler kullandığımız için `include` kullanmayacağız.

Önerilen stil, modülün gövdesini içe doğru kaydırmamaktır, çünkü bu genellikle tüm dosyaların içe kaydırılmasına yol açar. Ayrıca, modül adları için (tıpkı türler gibi) `UpperCamelCase` kullanmak yaygındır ve benzer şekilde adlandırılmış bir tanımlayıcı içeriyorsa, ad çakışmalarını önlemek için çoğul formunu kullanmak yaygındır. Örneğin,

```julia
module FastThings

struct FastThing
    ...
end

end
```

## [Namespace management](@id namespace-management)

Ad alan yönetimi, bir modüldeki isimlerin diğer modüllerde kullanılabilir hale getirilmesi için dilin sunduğu olanakları ifade eder. İlgili kavramları ve işlevselliği aşağıda ayrıntılı olarak tartışıyoruz.

### Qualified names

Fonksiyonlar, değişkenler ve `sin`, `ARGS` ve `UnitRange` gibi türler, her zaman bir modüle, *ebeveyn modül* denilen bir modüle aittir. Bu modül, örneğin [`parentmodule`](@ref) ile etkileşimli olarak bulunabilir.

```jldoctest
julia> parentmodule(UnitRange)
Base
```

Birisi bu isimlere ana modülünün önüne modülünü ekleyerek, örneğin `Base.UnitRange`, dışarıdan da atıfta bulunabilir. Bu bir *nitelikli isim* olarak adlandırılır. Ana modül, `Base.Math.sin` gibi bir dizi alt modül aracılığıyla erişilebilir, burada `Base.Math` *modül yolu* olarak adlandırılır. Sözdizimsel belirsizlikler nedeniyle, yalnızca semboller içeren bir ismi nitelendirmek, iki nokta eklemeyi gerektirir; örneğin `Base.:+`. Küçük bir sayıdaki operatörler ayrıca parantez gerektirir; örneğin `Base.:(==)`.

Eğer bir isim nitelikli ise, o zaman her zaman *erişilebilir*dir ve bir fonksiyon durumunda, nitelikli ismi fonksiyon adı olarak kullanarak ona yöntemler de eklenebilir.

Bir modül içinde, bir değişken adı `global x` olarak ilan edilerek "rezerv" edilebilir, bu da ona bir değer atamadan yapılır. Bu, yükleme zamanından sonra başlatılan küresel değişkenler için isim çakışmalarını önler. `M.x = y` sözdizimi, başka bir modülde bir küresel değişkene atama yapmak için çalışmaz; küresel atama her zaman modül yerelidir.

### Export lists

İsimler (fonksiyonlar, türler, global değişkenler ve sabitler anlamında) bir modülün *ihracat listesine* `export` ile eklenebilir: bunlar, modülü `using` ile kullandığınızda içe aktarılan sembollerdir. Genellikle, kaynak kodunu okuyanların kolayca bulabilmesi için modül tanımının en üstünde veya yakınında yer alırlar, örneğin

```jldoctest module_manual
julia> module NiceStuff
       export nice, DOG
       struct Dog end      # singleton type, not exported
       const DOG = Dog()   # named instance, exported
       nice(x) = "nice $x" # function, exported
       end;

```

ama bu sadece bir stil önerisi — bir modül, rastgele yerlerde birden fazla `export` ifadesine sahip olabilir.

API (uygulama programlama arayüzü) parçası olan isimleri dışa aktarmak yaygındır. Yukarıdaki kodda, dışa aktarma listesi kullanıcıların `nice` ve `DOG` kullanmalarını önermektedir. Ancak, nitelikli isimler her zaman tanımlayıcıları erişilebilir kıldığından, bu sadece API'leri düzenlemek için bir seçenektir: diğer dillerin aksine, Julia'nın modül iç yapılarını gerçekten gizlemek için olanakları yoktur.

Ayrıca, bazı modüller hiç isim dışa aktarmaz. Bu genellikle, API'lerinde `türev` gibi yaygın kelimeler kullandıklarında yapılır; bu, diğer modüllerin dışa aktarma listeleriyle kolayca çakışabilir. Aşağıda isim çakışmalarını nasıl yöneteceğimizi göreceğiz.

Bir ismi kamuya açık olarak işaretlemek için, `using NiceStuff` kullananların ad alanına aktarmadan `export` yerine `public` kullanılabilir. Bu, kamuya açık adı(ları) kamu API'sinin bir parçası olarak işaretler, ancak herhangi bir ad alanı etkisi yoktur. `public` anahtar kelimesi yalnızca Julia 1.11 ve üzeri sürümlerde mevcuttur. Julia 1.10 ve alt sürümlerle uyumluluğu korumak için, `@compat` makrosunu [Compat](https://github.com/JuliaLang/Compat.jl) paketinden kullanın.

### Standalone `using` and `import`

Etkileşimli kullanım için, bir modülü yüklemenin en yaygın yolu `using ModuleName`'dir. Bu [loads](@ref code-loading) `ModuleName` ile ilişkili kodu yükler ve getirir.

1. modül adı
2. ve ihracat listesinin unsurlarını çevresindeki küresel ad alanına.

Teknik olarak, `using ModuleName` ifadesi, `ModuleName` adında bir modülün ihtiyaç duyulduğunda isimleri çözmek için mevcut olacağı anlamına gelir. Mevcut modülde tanımı olmayan bir global değişkenle karşılaşıldığında, sistem bunu `ModuleName` tarafından dışa aktarılan değişkenler arasında arayacak ve orada bulunursa kullanacaktır. Bu, mevcut modül içindeki o global değişkenin tüm kullanımlarının `ModuleName` içindeki o değişkenin tanımına karşılık geleceği anlamına gelir.

Bir paketten bir modülü yüklemek için `using ModuleName` ifadesi kullanılabilir. Yerel olarak tanımlanmış bir modülden bir modül yüklemek için modül adından önce bir nokta eklenmelidir, örneğin `using .ModuleName`.

Devam etmek için örneğimize,

```jldoctest module_manual
julia> using .NiceStuff
```

yukarıdaki kodu yükleyecek, `NiceStuff` (modül adı), `DOG` ve `nice`'i kullanılabilir hale getirecektir. `Dog` dışa aktarma listesinde yer almaz, ancak adı modül yolu ile nitelendirilirse (burada sadece modül adı) `NiceStuff.Dog` olarak erişilebilir.

Önemli olarak, **`using ModuleName` dışa aktarma listelerinin önemli olduğu tek biçimdir**.

Buna karşılık,

```jldoctest module_manual
julia> import .NiceStuff
```

sadece modül adını kapsam içine alır. Kullanıcılar içeriğine erişmek için `NiceStuff.DOG`, `NiceStuff.Dog` ve `NiceStuff.nice` kullanmak zorundadır. Genellikle, `import ModuleName`, kullanıcının ad alanını temiz tutmak istediği durumlarda kullanılır. Bir sonraki bölümde göreceğimiz gibi `import .NiceStuff`, `using .NiceStuff: NiceStuff` ile eşdeğerdir.

Birden fazla `using` ve `import` ifadesini aynı türde, virgülle ayrılmış bir ifadede birleştirebilirsiniz, örneğin:

```jldoctest module_manual
julia> using LinearAlgebra, Random
```

### `using` and `import` with specific identifiers, and adding methods

`using ModuleName:` veya `import ModuleName:` ifadesinden sonra virgülle ayrılmış bir isimler listesi geldiğinde, modül yüklenir, ancak *yalnızca o belirli isimler ad alanına* bu ifade ile getirilir. Örneğin,

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG
```

`nice` ve `DOG` isimlerini içe aktaracağım.

Önemli olarak, `NiceStuff` modül adı *isim alanında* yer almayacaktır. Eğer erişilebilir olmasını istiyorsanız, onu açıkça listelemeniz gerekir, şöyle:

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG, NiceStuff
```

İki veya daha fazla paket/modül bir ismi dışa aktardığında ve bu isim her bir pakette aynı şeye referans vermediğinde, ve paketler `using` ile açık bir isim listesi olmadan yüklendiğinde, o ismi nitelik olmadan referans vermek bir hata olur. Bu nedenle, bağımlılıklarının ve Julia'nın gelecekteki sürümleriyle ileriye dönük uyumlu olması amaçlanan kodların, örneğin, yayımlanan paketlerde, her bir yüklü paketten kullandığı isimleri listelemesi önerilir; örneğin, `using Foo: Foo, f` yerine `using Foo` kullanmak.

Julia'nın iki formu, görünüşte aynı şey için vardır çünkü yalnızca `import ModuleName: f` yöntemi, `f`'ye *modül yolu olmadan* yöntem eklemeye izin verir. Yani, aşağıdaki örnek bir hata verecektir:

```jldoctest module_manual
julia> using .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
ERROR: invalid method definition in Main: function NiceStuff.nice must be explicitly imported to be extended
Stacktrace:
 [1] top-level scope
   @ none:0
 [2] top-level scope
   @ none:1

```

Bu hata, yalnızca kullanmayı amaçladığınız diğer modüllerdeki fonksiyonlara yanlışlıkla yöntem eklenmesini engeller.

Bununla başa çıkmanın iki yolu vardır. Fonksiyon adlarını her zaman bir modül yolu ile nitelendirebilirsiniz:

```jldoctest module_manual
julia> using .NiceStuff

julia> struct Cat end

julia> NiceStuff.nice(::Cat) = "nice 😸"

```

Alternatif olarak, belirli bir fonksiyon adını `import` edebilirsiniz:

```jldoctest module_manual
julia> import .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
nice (generic function with 2 methods)
```

Hangisini seçeceğiniz bir stil meselesidir. İlk form, başka bir modüldeki bir işleve bir yöntem eklediğinizi açıkça belirtir (unutmayın, ithalatlar ve yöntem tanımı ayrı dosyalarda olabilir), ikinci form ise daha kısadır, bu da birden fazla yöntem tanımlıyorsanız özellikle kullanışlıdır.

Bir değişken `using` veya `import` ile görünür hale getirildiğinde, bir modül aynı isimle kendi değişkenini oluşturamaz. İçe aktarılan değişkenler salt okunurdur; bir küresel değişkene atama yapmak her zaman mevcut modül tarafından sahip olunan bir değişkeni etkiler veya aksi takdirde bir hata oluşturur.

### Renaming with `as`

Bir `import` veya `using` ile kapsam içine alınan bir tanımlayıcı, `as` anahtar kelimesi ile yeniden adlandırılabilir. Bu, isim çakışmalarını aşmak ve isimleri kısaltmak için yararlıdır. Örneğin, `Base` `read` fonksiyonunu dışa aktarırken, CSV.jl paketi de `CSV.read` sağlar. Eğer CSV okuma işlemini birçok kez gerçekleştireceksek, `CSV.` niteliklerini atlamak pratik olacaktır. Ancak bu durumda, `Base.read` mi yoksa `CSV.read` mi kastettiğimiz belirsiz hale gelir:

```julia-repl
julia> read;

julia> import CSV: read
WARNING: ignoring conflicting import of CSV.read into Main
```

Yeniden adlandırma bir çözüm sunar:

```julia-repl
julia> import CSV: read as rd
```

İçe aktarılan paketler kendileri de yeniden adlandırılabilir:

```julia
import BenchmarkTools as BT
```

`as` yalnızca bir tanımlayıcı kapsamına alındığında `using` ile çalışır. Örneğin `using CSV: read as rd` çalışır, ancak `using CSV as C` çalışmaz, çünkü bu, `CSV` içindeki tüm dışa aktarılan adlar üzerinde işlem yapar.

### Mixing multiple `using` and `import` statements

Birden fazla `using` veya `import` ifadesi yukarıdaki formlardan herhangi biri kullanıldığında, etkileri göründükleri sıraya göre birleştirilir. Örneğin,

```jldoctest module_manual
julia> using .NiceStuff         # exported names and the module name

julia> import .NiceStuff: nice  # allows adding methods to unqualified functions

```

`NiceStuff`'ın tüm dışa aktarılan isimlerini ve modül adını kapsam içine alacak ve ayrıca `nice`'e modül adı ile önek eklemeden yöntemler eklemeye de olanak tanıyacaktır.

### Handling name conflicts

Durumu düşünün; iki (veya daha fazla) paket aynı ismi dışa aktarıyorsa, örneğin

```jldoctest module_manual
julia> module A
       export f
       f() = 1
       end
A
julia> module B
       export f
       f() = 2
       end
B
```

`using .A, .B` ifadesi çalışır, ancak `f`'yi çağırmaya çalıştığınızda bir hata alırsınız ve bir ipucu ile karşılaşırsınız.

```jldoctest module_manual
julia> using .A, .B

julia> f
ERROR: UndefVarError: `f` not defined in `Main`
Hint: It looks like two or more modules export different bindings with this name, resulting in ambiguity. Try explicitly importing it from a particular module, or qualifying the name with the module it should come from.
```

Burada, Julia hangi `f`'yi kastettiğinizi belirleyemiyor, bu yüzden bir seçim yapmalısınız. Aşağıdaki çözümler yaygın olarak kullanılmaktadır:

1. Basitçe, `A.f` ve `B.f` gibi nitelikli isimlerle devam edin. Bu, kodunuzun okuyucusuna bağlamı net bir şekilde iletir, özellikle de `f` farklı paketlerde farklı anlamlara sahip oluyorsa. Örneğin, `degree` matematikte, doğal bilimlerde ve günlük hayatta çeşitli kullanımlara sahiptir ve bu anlamların ayrı tutulması gerekir.
2. `as` anahtar kelimesini yukarıda bir veya her iki tanımlayıcıyı yeniden adlandırmak için kullanın, örn.

    ```jldoctest module_manual
    julia> using .A: f as f

    julia> using .B: f as g

    ```

    `B.f`'yi `g` olarak kullanılabilir hale getirecektir. Burada, `f`'yi ad alanına getirecek olan `using A` ifadesini daha önce kullanmadığınızı varsayıyoruz.
3. Söz konusu isimler *anlam* paylaştığında, bir modülün diğerinden bunu içe aktarması veya yalnızca bu tür bir arayüz tanımlama işlevine sahip hafif bir "temel" paket bulundurması yaygındır; bu, diğer paketler tarafından kullanılabilir. Bu tür paket isimlerinin `...Base` ile bitmesi gelenekseldir (bu, Julia'nın `Base` modülüyle ilgili değildir).

### Default top-level definitions and bare modules

Modüller otomatik olarak `using Core`, `using Base` içerir ve [`eval`](@ref) ve [`include`](@ref) fonksiyonlarının tanımlarını içerir; bu fonksiyonlar, o modülün küresel kapsamı içinde ifadeleri/dosyaları değerlendirir.

Eğer bu varsayılan tanımlar istenmiyorsa, modüller [`baremodule`](@ref) anahtar kelimesi kullanılarak tanımlanabilir (not: `Core` hala içe aktarılmaktadır). `baremodule` açısından, standart bir `module` şöyle görünür:

```
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```

Eğer `Core` bile istenmiyorsa, hiçbir şey içermeyen ve hiç isim tanımlamayan bir modül `Module(:YourNameHere, false, false)` ile tanımlanabilir ve içine kod [`@eval`](@ref) veya [`Core.eval`](@ref) ile değerlendirilebilir:

```jldoctest
julia> arithmetic = Module(:arithmetic, false, false)
Main.arithmetic

julia> @eval arithmetic add(x, y) = $(+)(x, y)
add (generic function with 1 method)

julia> arithmetic.add(12, 13)
25
```

### Standard modules

Üç önemli standart modül vardır:

  * [`Core`](@ref) dilin içine "gömülü" tüm işlevselliği içerir.
  * [`Base`](@ref) hemen hemen tüm durumlarda yararlı olan temel işlevselliği içerir.
  * [`Main`](@ref) en üst düzey modül ve Julia başlatıldığında mevcut modüldür.

!!! note "Standard library modules"
    Varsayılan olarak Julia, bazı standart kütüphane modülleri ile birlikte gelir. Bunlar, normal Julia paketleri gibi davranır, ancak bunları açıkça yüklemenize gerek yoktur. Örneğin, bazı birim testleri yapmak istiyorsanız, `Test` standart kütüphanesini aşağıdaki gibi yükleyebilirsiniz:

    ```julia
    using Test
    ```


## Submodules and relative paths

Modüller *alt modüller* içerebilir, aynı `module ... end` sözdizimini kullanarak iç içe geçebilirler. Bu, karmaşık kod tabanlarını düzenlemek için yararlı olabilecek ayrı ad alanları tanıtmak için kullanılabilir. Her `module` kendi [scope](@ref scope-of-variables)'ini tanıttığı için, alt modüller otomatik olarak ebeveynlerinden isim “miras almazlar”.

Alt modüllerin, kapsayıcı ana modül (ve onun) içindeki diğer modüllere *göreceli modül nitelikleri* kullanarak `using` ve `import` ifadeleriyle atıfta bulunması önerilir. Göreceli bir modül niteliği, mevcut modülü temsil eden bir nokta (`.`) ile başlar ve her bir ardışık `.` mevcut modülün üst modülüne işaret eder. Gerekirse modüllerle devam edilmeli ve nihayetinde erişilecek gerçek isim, hepsi `.` ile ayrılarak belirtilmelidir.

Aşağıdaki örneği düşünün; burada `SubA` alt modülü bir fonksiyon tanımlar ve bu fonksiyon daha sonra "kardeş" modülünde genişletilir:

```jldoctest module_manual
julia> module ParentModule
       module SubA
       export add_D  # exported interface
       const D = 3
       add_D(x) = x + D
       end
       using .SubA  # brings `add_D` into the namespace
       export add_D # export it from ParentModule too
       module SubB
       import ..SubA: add_D # relative path for a “sibling” module
       struct Infinity end
       add_D(x::Infinity) = x
       end
       end;

```

Paketlerde kod görebilirsiniz, bu da benzer bir durumda kullanır.

```jldoctest module_manual
julia> import .ParentModule.SubA: add_D

```

Ancak bu, [code loading](@ref code-loading) üzerinden çalışır ve bu nedenle yalnızca `ParentModule` bir paketteyse çalışır. Göreceli yolları kullanmak daha iyidir.

Tanım sıralamasının, değerleri değerlendirirken de önemli olduğunu unutmayın. Dikkate alın.

```julia
module TestPackage

export x, y

x = 0

module Sub
using ..TestPackage
z = y # ERROR: UndefVarError: `y` not defined in `Main`
end

y = 1

end
```

`Sub` tanımından önce `TestPackage.y` kullanmaya çalışıyor, bu yüzden bir değeri yok.

Benzer nedenlerden dolayı, döngüsel bir sıralama kullanamazsınız:

```julia
module A

module B
using ..C # ERROR: UndefVarError: `C` not defined in `Main.A`
end

module C
using ..B
end

end
```

## Module initialization and precompilation

Büyük modüller, bir modüldeki tüm ifadeleri yürütmek genellikle büyük miktarda kod derlemeyi içerdiğinden, yüklenmesi birkaç saniye sürebilir. Julia, bu süreyi azaltmak için modülün önceden derlenmiş önbelleklerini oluşturur.

Önceden derlenmiş modül dosyaları (bazen "önbellek dosyaları" olarak adlandırılır) `import` veya `using` bir modülü yüklediğinde otomatik olarak oluşturulur ve kullanılır. Eğer önbellek dosyası(ları) henüz mevcut değilse, modül derlenecek ve gelecekteki yeniden kullanım için kaydedilecektir. Ayrıca, modülü yüklemeden bu dosyaları oluşturmak için [`Base.compilecache(Base.identify_package("modulename"))`](@ref) komutunu manuel olarak çağırabilirsiniz. Ortaya çıkan önbellek dosyaları `DEPOT_PATH[1]`'in `compiled` alt klasöründe saklanacaktır. Sisteminizle ilgili hiçbir şey değişmezse, bu tür önbellek dosyaları `import` veya `using` ile modülü yüklediğinizde kullanılacaktır.

Ön derleme önbellek dosyaları, modüllerin, türlerin, yöntemlerin ve sabitlerin tanımlarını saklar. Ayrıca yöntem özel uzmanlıklarını ve bunlar için üretilen kodu da saklayabilir, ancak bu genellikle geliştiricinin açık [`precompile`](@ref) direktifleri eklemesini veya paket derlemesi sırasında derlemeyi zorlayan iş yüklerini çalıştırmasını gerektirir.

Ancak, modülün bağımlılıklarını güncellerseniz veya kaynak kodunu değiştirirseniz, modül `using` veya `import` ile otomatik olarak yeniden derlenir. Bağımlılıklar, modülün içe aktardığı modüller, Julia derlemesi, dahil ettiği dosyalar veya modül dosyasında [`include_dependency(path)`](@ref) ile belirtilen açık bağımlılıklardır.

`include` ile yüklenen dosya bağımlılıkları için bir değişiklik, dosya boyutunun (`fsize`) veya içeriğin (bir hash'e yoğunlaştırılmış) değişip değişmediğini inceleyerek belirlenir. `include_dependency` ile yüklenen dosya bağımlılıkları için bir değişiklik, değişiklik zamanının (`mtime`) değişmediğini veya en yakın saniyeye yuvarlanmış değişiklik zamanına eşit olup olmadığını inceleyerek belirlenir (alt saniye hassasiyetiyle mtime'ı kopyalayamayan sistemleri dikkate almak için). Ayrıca, `require` içindeki arama mantığı tarafından seçilen dosya yolunun, önceden derleme dosyasını oluşturan yol ile eşleşip eşleşmediğini de dikkate alır. Ayrıca, mevcut işleme zaten yüklenmiş olan bağımlılık setini de dikkate alır ve bu modülleri yeniden derlemeyecek, dosyaları değişse veya kaybolsa bile, çalışan sistem ile önceden derleme önbelleği arasında uyumsuzluk yaratmamak için. Son olarak, herhangi bir [compile-time preferences](@ref preferences) içindeki değişiklikleri de dikkate alır.

Eğer bir modülün *önceden derlenmesi için güvenli olmadığını* biliyorsanız (örneğin, aşağıda açıklanan nedenlerden biri için), modül dosyasına `__precompile__(false)` eklemelisiniz (genellikle en üstte yer alır). Bu, `Base.compilecache`'in bir hata fırlatmasına neden olacak ve `using` / `import` komutlarının modülü doğrudan mevcut işleme yüklemesini sağlayacak ve önceden derleme ve önbellekleme işlemlerini atlayacaktır. Bu ayrıca, modülün başka bir önceden derlenmiş modül tarafından içe aktarılmasını da engeller.

Belirli davranışların, artımlı paylaşılan kütüphanelerin oluşturulmasında dikkat gerektirebileceğini bilmeniz gerekebilir; bu, modülünüzü yazarken dikkatli olmanızı gerektirebilir. Örneğin, dış durum korunmaz. Bunu accommodate etmek için, *çalışma zamanı* sırasında gerçekleşmesi gereken herhangi bir başlatma adımını, *derleme zamanı* sırasında gerçekleşebilecek adımlardan açıkça ayırın. Bu amaçla, Julia, modülünüzde çalışma zamanı sırasında gerçekleşmesi gereken herhangi bir başlatma adımını yürüten bir `__init__()` fonksiyonu tanımlamanıza izin verir. Bu fonksiyon, derleme sırasında (`--output-*`) çağrılmayacaktır. Etkili bir şekilde, bu fonksiyonun kodun ömrü boyunca tam olarak bir kez çalıştırılacağını varsayabilirsiniz. Gerekirse, elbette manuel olarak çağırabilirsiniz, ancak varsayılan olarak bu fonksiyonun yerel makine için durum hesaplamasıyla ilgilendiğini varsaymak gerekir; bu durum, derlenmiş görüntüde yakalanması gerekmeyen – veya hatta yakalanmaması gereken – bir durumdur. Modül bir işleme yüklendikten sonra çağrılacaktır; bu, artımlı bir derlemeye yükleniyorsa (`--output-incremental=yes`) bile geçerlidir, ancak tam bir derleme sürecine yükleniyorsa geçerli değildir.

Özellikle, bir modülde bir `function __init__()` tanımlarsanız, Julia modül yüklendikten hemen sonra (örneğin, `import`, `using` veya `require` ile) çalışma zamanında *ilk* kez `__init__()` çağrılacaktır (yani, `__init__` yalnızca bir kez çağrılır ve yalnızca modüldeki tüm ifadeler yürütüldükten sonra). Modül tamamen içe aktarıldıktan sonra çağrıldığı için, herhangi bir alt modül veya diğer içe aktarılan modüllerin `__init__` fonksiyonları, kapsayıcı modülün `__init__`'inden *önce* çağrılır.

`__init__`'in iki tipik kullanımı, dış C kütüphanelerinin çalışma zamanı başlatma işlevlerini çağırmak ve dış kütüphaneler tarafından döndürülen işaretçileri içeren global sabitleri başlatmaktır. Örneğin, çalışma zamanında `foo_init()` başlatma işlevini çağırmamızı gerektiren bir C kütüphanesi `libfoo`'yu çağırdığımızı varsayalım. Ayrıca, `libfoo` tarafından tanımlanan `void *foo_data()` işlevinin döndürdüğü değeri tutan bir global sabit `foo_data_ptr` tanımlamak istiyoruz - bu sabit, işaretçi adresi her çalıştırmada değişeceği için çalışma zamanında (derleme zamanında değil) başlatılmalıdır. Bunu, modülünüzde aşağıdaki `__init__` işlevini tanımlayarak başarabilirsiniz:

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```

Dikkat edin ki, `__init__` gibi bir fonksiyon içinde bir global tanımlamak tamamen mümkündür; bu, dinamik bir dil kullanmanın avantajlarından biridir. Ancak, bunu global kapsamda bir sabit haline getirerek, türün derleyiciye bilindiğini garanti edebilir ve daha iyi optimize edilmiş kod üretmesine izin verebiliriz. Açıkça, `foo_data_ptr`'a bağlı olan modülünüzdeki diğer herhangi bir global de `__init__` içinde başlatılmalıdır.

[`ccall`](@ref) tarafından üretilmeyen çoğu Julia nesnesini içeren sabitlerin `__init__` içine yerleştirilmesine gerek yoktur: tanımları önceden derlenebilir ve önbellekli modül görüntüsünden yüklenebilir. Bu, diziler gibi karmaşık yığın tahsisli nesneleri içerir. Ancak, ham bir işaretçi değeri döndüren herhangi bir rutin, ön derlemenin çalışması için çalışma zamanında çağrılmalıdır ([`Ptr`](@ref) nesneleri, [`isbits`](@ref) nesnesinin içinde gizlenmedikçe null işaretçilerine dönüşecektir). Bu, Julia fonksiyonlarının döndürdüğü değerleri de içerir: [`@cfunction`](@ref) ve [`pointer`](@ref).

Sözlük ve küme türleri, ya da genel olarak `hash(key)` yönteminin çıktısına bağlı olan herhangi bir şey, daha karmaşık bir durumdur. Anahtarların sayılar, dizeler, semboller, aralıklar, `Expr` veya bu türlerin (diziler, demetler, kümeler, çiftler vb. aracılığıyla) bileşimleri olduğu yaygın durumda, önceden derlenmeleri güvenlidir. Ancak, `Function` veya `DataType` gibi birkaç başka anahtar türü ve `hash` yöntemini tanımlamadığınız genel kullanıcı tanımlı türler için, varsayılan `hash` yöntemi nesnenin bellek adresine (bu aracılığıyla `objectid`) bağlıdır ve bu nedenle her çalıştırmada değişebilir. Bu anahtar türlerinden birine sahipseniz veya emin değilseniz, güvenli olmak için bu sözlüğü `__init__` fonksiyonunuzdan başlatabilirsiniz. Alternatif olarak, derleme zamanında güvenli bir şekilde başlatılacak şekilde özel olarak işlenen [`IdDict`](@ref) sözlük türünü kullanabilirsiniz.

Önceden derleme kullanırken, derleme aşaması ile yürütme aşaması arasındaki ayrımı net bir şekilde anlamak önemlidir. Bu modda, Julia'nın, derlenmiş kod üreten bağımsız bir yorumlayıcı değil, keyfi Julia kodunun yürütülmesine izin veren bir derleyici olduğu çok daha belirgin hale gelecektir.

Diğer bilinen potansiyel arıza senaryoları şunlardır:

1. Küresel sayaçlar (örneğin, nesneleri benzersiz bir şekilde tanımlamaya çalışmak için). Aşağıdaki kod parçasını dikkate alın:

    ```julia
    mutable struct UniquedById
        myid::Int
        let counter = 0
            UniquedById() = new(counter += 1)
        end
    end
    ```

    bu kodun amacı her örneğe benzersiz bir kimlik vermek olsa da, sayaç değeri derlemenin sonunda kaydedilir. Bu artımlı derlenmiş modülün sonraki tüm kullanımları, o aynı sayaç değerinden başlayacaktır.

    `objectid` (bellek işaretçisini hashleyerek çalışan) benzer sorunlara sahiptir (aşağıdaki `Dict` kullanımı notlarına bakın).

    Bir alternatif, [`@__MODULE__`](@ref) değerini yakalamak için bir makro kullanmak ve bunu mevcut `counter` değeriyle birlikte saklamaktır, ancak bu global duruma bağımlı olmamak için kodu yeniden tasarlamak daha iyi olabilir.
2. Birleşik koleksiyonlar (örneğin `Dict` ve `Set`) `__init__` içinde yeniden hash'lenmelidir. (Gelecekte, bir başlatıcı işlevi kaydetmek için bir mekanizma sağlanabilir.)
3. Derleyim zamanı yan etkilerine bağlı olarak yükleme zamanı boyunca devam eden. Örnekler arasında: diğer Julia modüllerindeki dizileri veya diğer değişkenleri değiştirmek; açık dosyalara veya cihazlara tutamaklar korumak; diğer sistem kaynaklarına (bellek dahil) işaretçiler depolamak;
4. Küresel durumu başka bir modülden doğrudan referans alarak, arama yolu aracılığıyla değil, "kopyalarını" kazara oluşturma. Örneğin, (küresel kapsamda):

    ```julia
    #mystdout = Base.stdout #= will not work correctly, since this will copy Base.stdout into this module =#
    # instead use accessor functions:
    getstdout() = Base.stdout #= best option =#
    # or move the assignment into the runtime:
    __init__() = global mystdout = Base.stdout #= also works =#
    ```

Kodun önceden derlenmesi sırasında kullanıcının diğer yanlış davranış durumlarından kaçınmasına yardımcı olmak için yapılabilecek işlemler üzerinde birkaç ek kısıtlama bulunmaktadır:

1. [`eval`](@ref) çağrısı, başka bir modülde yan etki yaratmak için yapılmaktadır. Bu, artan ön derleme bayrağı ayarlandığında bir uyarının da yayımlanmasına neden olacaktır.
2. `__init__()` başladıktan sonra yerel kapsamdan `global const` ifadeleri (bunun için bir hata ekleme planları için bkz. sorun #12010)
3. Bir modülü değiştirmek, artımlı ön derleme sırasında bir çalışma zamanı hatasıdır.

Dikkate almanız gereken birkaç başka nokta:

1. Kaynak dosyalarında yapılan değişikliklerden sonra ( `Pkg.update` dahil) hiçbir kod yeniden yüklemesi / önbellek geçersiz kılma işlemi yapılmaz ve `Pkg.rm` sonrasında hiçbir temizlik yapılmaz.
2. Yeniden şekillendirilmiş bir dizinin bellek paylaşım davranışı ön derleme tarafından göz ardı edilir (her görünüm kendi kopyasını alır).
3. Dosya sisteminin derleme zamanı ve çalışma zamanı arasında değişmeden kalmasını beklemek, örneğin [`@__FILE__`](@ref)/`source_path()` ile çalışma zamanında kaynakları bulmak veya BinDeps `@checked_lib` makrosu. Bazen bu kaçınılmazdır. Ancak, mümkün olduğunda, kaynakları derleme zamanında modüle kopyalamak iyi bir uygulama olabilir, böylece çalışma zamanında bulunmaları gerekmez.
4. `WeakRef` nesneleri ve sonlandırıcılar şu anda serileştirici tarafından düzgün bir şekilde işlenmiyor (bu, yaklaşan bir sürümde düzeltilecektir).
5. Genellikle, `Method`, `MethodInstance`, `MethodTable`, `TypeMapLevel`, `TypeMapEntry` gibi içsel meta veri nesnelerinin örneklerine referansları yakalamaktan kaçınmak en iyisidir. Çünkü bu, serileştiriciyi karıştırabilir ve istediğiniz sonuca ulaşmanıza yol açmayabilir. Bunu yapmak zorunda değilsiniz, ancak sistemin bunların bazılarını kopyalamaya çalışacağını ve diğerlerinin tekil bir örneğini oluşturmaya çalışacağını kabul etmeye hazır olmalısınız.

Modül geliştirme sırasında artımlı ön derlemeyi kapatmak bazen faydalı olabilir. Komut satırı bayrağı `--compiled-modules={yes|no|existing}` modül ön derlemesini açıp kapatmanıza olanak tanır. Julia `--compiled-modules=no` ile başlatıldığında, derleme önbelleğindeki serileştirilmiş modüller, modülleri ve modül bağımlılıklarını yüklerken göz ardı edilir. Bazı durumlarda, mevcut ön derlenmiş modülleri yüklemek isteyebilirsiniz, ancak yenilerini oluşturmak istemezsiniz. Bu, Julia'yı `--compiled-modules=existing` ile başlatarak yapılabilir. Daha ayrıntılı kontrol, yalnızca ön derleme sırasında yerel kod depolamasını etkileyen `--pkgimages={yes|no|existing}` ile mümkündür. `Base.compilecache` hala manuel olarak çağrılabilir. Bu komut satırı bayrağının durumu, paketleri yüklerken, güncellerken ve açıkça inşa ederken otomatik ön derleme tetiklemeyi devre dışı bırakmak için `Pkg.build`'e iletilir.

Ayrıca, ortam değişkenleri ile bazı ön derleme hatalarını hata ayıklayabilirsiniz. `JULIA_VERBOSE_LINKING=true` ayarını yapmak, derlenmiş yerel kodun paylaşılan kütüphanelerinin bağlantısındaki hataları çözmeye yardımcı olabilir. Julia kılavuzunun **Geliştirici Belgeleri** bölümüne bakın; burada "Paket Görüntüleri" altında Julia'nın iç yapısını belgeleyen bölümde daha fazla ayrıntı bulacaksınız.
