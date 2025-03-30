# [Code Loading](@id code-loading)

!!! note
    This chapter covers the technical details of package loading. To install packages, use [`Pkg`](@ref Pkg), Julia's built-in package manager, to add packages to your active environment. To use packages already in your active environment, write `import X` or `using X`, as described in the [Modules documentation](@ref modules).


## Definitions

Julia'nın kod yüklemek için iki mekanizması vardır:

1. **Kod dahil etme:** örn. `include("source.jl")`. Dâhil etme, tek bir programı birden fazla kaynak dosyası arasında bölmenizi sağlar. `include("source.jl")` ifadesi, `include` çağrısının gerçekleştiği modülün global kapsamında `source.jl` dosyasının içeriğinin değerlendirilmesine neden olur. `include("source.jl")` birden fazla kez çağrılırsa, `source.jl` birden fazla kez değerlendirilir. Dâhil edilen yol, `source.jl`, `include` çağrısının gerçekleştiği dosyaya göre göreceli olarak yorumlanır. Bu, bir kaynak dosyası alt ağacını taşımayı basit hale getirir. REPL'de, dâhil edilen yollar mevcut çalışma dizinine göre yorumlanır, [`pwd()`](@ref).
2. **Paket yükleme:** örn. `import X` veya `using X`. İçe aktarma mekanizması, bir paketi yüklemenizi sağlar; yani, bir modül içinde sarılmış bağımsız, yeniden kullanılabilir bir Julia kodu koleksiyonu ve sonuçta elde edilen modül, içe aktaran modül içinde `X` adıyla kullanılabilir hale gelir. Aynı `X` paketi, aynı Julia oturumunda birden fazla kez içe aktarılırsa, yalnızca ilk seferde yüklenir; sonraki içe aktarmalarda, içe aktaran modül aynı modüle bir referans alır. Ancak, `import X` farklı bağlamlarda farklı paketler yükleyebilir: `X`, ana projede `X` adında bir paketi ifade edebilir, ancak her bağımlılıkta da `X` adında farklı paketlere atıfta bulunabilir. Bununla ilgili daha fazla bilgi aşağıda.

Kod dahil etme oldukça basit ve açıktır: verilen kaynak dosyayı çağıranın bağlamında değerlendirir. Paket yükleme, kod dahil etmenin üzerine inşa edilmiştir ve bir [different purpose](@ref modules) hizmet eder. Bu bölümün geri kalanı, paket yüklemenin davranışına ve mekaniklerine odaklanmaktadır.

Bir *paket*, diğer Julia projeleri tarafından yeniden kullanılabilecek işlevsellik sağlayan standart bir düzenle kaynak ağacıdır. Bir paket, `import X` veya `using X` ifadeleriyle yüklenir. Bu ifadeler ayrıca, paketin kodunu yüklemekten kaynaklanan `X` adlı modülü, import ifadesinin gerçekleştiği modül içinde kullanılabilir hale getirir. `import X` içindeki `X`'in anlamı bağlama bağlıdır: hangi `X` paketinin yükleneceği, ifadenin hangi kod içinde yer aldığına bağlıdır. Bu nedenle, `import X` işlemi iki aşamada gerçekleşir: ilk olarak, bu bağlamda `X` olarak tanımlanan **hangi** paketin olduğu belirlenir; ikinci olarak, o belirli `X` paketinin **nerede** bulunduğu belirlenir.

Bu sorular, [`LOAD_PATH`](@ref) içinde listelenen proje ortamlarında `Project.toml` veya `JuliaProject.toml` gibi proje dosyalarını, `Manifest.toml` veya `JuliaManifest.toml` gibi manifest dosyalarını (veya belirli sürümler için `-v{major}.{minor}.toml` ile sonlandırılmış aynı isimleri) veya kaynak dosyalarının klasörlerini arayarak yanıtlanmaktadır.

## Federation of packages

Çoğu zaman, bir paket yalnızca adıyla benzersiz bir şekilde tanımlanabilir. Ancak, bazen bir proje, aynı adı paylaşan iki farklı paketi kullanması gereken bir durumla karşılaşabilir. Bu durumu, paketlerden birinin adını değiştirerek çözebilseniz de, bunu yapmak zorunda kalmak büyük, paylaşılan bir kod tabanında oldukça yıkıcı olabilir. Bunun yerine, Julia'nın kod yükleme mekanizması, aynı paket adının bir uygulamanın farklı bileşenlerinde farklı paketlere atıfta bulunmasına olanak tanır.

Julia, federated paket yönetimini destekler; bu, birden fazla bağımsız tarafın hem kamu hem de özel paketler ve paket kayıtları sürdürebileceği ve projelerin farklı kayıtlarından hem kamu hem de özel paketlere bağımlı olabileceği anlamına gelir. Çeşitli kayıtlarından paketler, ortak bir araç ve iş akışı seti kullanılarak yüklenir ve yönetilir. Julia ile birlikte gelen `Pkg` paket yöneticisi, projelerinizin bağımlılıklarını yüklemenize ve yönetmenize olanak tanır. Projenizin bağımlı olduğu diğer projeleri tanımlayan proje dosyaları oluşturma ve manipüle etme konusunda yardımcı olur ve projenizin tam bağımlılık grafiğinin kesin sürümlerini anlık görüntüleyen manifest dosyaları oluşturur.

Federasyonun bir sonucu, paket adlandırması için merkezi bir otoritenin olamayacağıdır. Farklı varlıklar, alakasız paketleri ifade etmek için aynı adı kullanabilir. Bu olasılık kaçınılmazdır çünkü bu varlıklar koordine olmaz ve birbirlerinden haberdar olmayabilirler. Merkezi bir adlandırma otoritesinin yokluğunda, tek bir proje, aynı adı taşıyan farklı paketlere bağımlı hale gelebilir. Julia'nın paket yükleme mekanizması, paket adlarının tek bir projenin bağımlılık grafiği içinde bile küresel olarak benzersiz olmasını gerektirmez. Bunun yerine, paketler [universally unique identifiers](https://en.wikipedia.org/wiki/Universally_unique_identifier) (UUID'ler) ile tanımlanır ve her paket oluşturulduğunda atanır. Genellikle, bu biraz hantal 128-bit tanımlayıcılarla doğrudan çalışmanız gerekmeyecek çünkü `Pkg` bunları sizin için oluşturup takip edecektir. Ancak, bu UUID'ler *"X, hangi paketi ifade ediyor?"* sorusunun kesin yanıtını sağlar.

Dağıtılmış adlandırma sorunu biraz soyut olduğundan, konuyu anlamak için somut bir senaryoyu incelemek faydalı olabilir. Diyelim ki `App` adında bir uygulama geliştiriyorsunuz ve bu uygulama iki paketi kullanıyor: `Pub` ve `Priv`. `Priv`, sizin oluşturduğunuz özel bir paketken, `Pub` ise kullandığınız ama kontrol etmediğiniz bir kamu paketidir. `Priv`'i oluşturduğunuzda, `Priv` adında bir kamu paketi yoktu. Ancak daha sonra, alakasız bir paket de `Priv` adıyla yayımlandı ve popüler hale geldi. Aslında, `Pub` paketi de bunu kullanmaya başladı. Bu nedenle, `Pub`'ı en son hata düzeltmeleri ve özellikleri almak için bir sonraki güncellediğinizde, `App` iki farklı `Priv` paketine bağımlı hale gelecektir—sadece güncelleme yapmanız dışında hiçbir eylemde bulunmadan. `App`, sizin özel `Priv` paketine doğrudan bağımlıdır ve `Pub` aracılığıyla yeni kamu `Priv` paketine dolaylı bir bağımlılığa sahiptir. Bu iki `Priv` paketi farklıdır ancak `App`'in doğru bir şekilde çalışmaya devam etmesi için her ikisi de gereklidir, bu nedenle `import Priv` ifadesi, `App`'in kodunda mı yoksa `Pub`'ın kodunda mı geçtiğine bağlı olarak farklı `Priv` paketlerine atıfta bulunmalıdır. Bunu yönetmek için, Julia'nın paket yükleme mekanizması, iki `Priv` paketini UUID'leri ile ayırt eder ve bağlama (import eden modül) göre doğru olanı seçer. Bu ayrımın nasıl çalıştığı, aşağıdaki bölümlerde açıklanan ortamlar tarafından belirlenir.

## Environments

Bir *çevre*, `import X` ve `using X` ifadelerinin çeşitli kod bağlamlarında ne anlama geldiğini ve bu ifadelerin hangi dosyaların yüklenmesine neden olduğunu belirler. Julia, iki tür çevreyi anlar:

1. **Bir proje ortamı**, bir proje dosyası ve isteğe bağlı bir manifest dosyası ile bir dizindir ve *açık bir ortam* oluşturur. Proje dosyası, bir projenin doğrudan bağımlılıklarının adlarını ve kimliklerini belirler. Varsa manifest dosyası, doğrudan ve dolaylı tüm bağımlılıkları, her bağımlılığın kesin sürümlerini ve doğru sürümü bulmak ve yüklemek için yeterli bilgiyi içeren tam bir bağımlılık grafiği sağlar.
2. **Bir paket dizini**, bir dizi paketin kaynak ağaçlarını alt dizinler olarak içeren bir dizindir ve *örtük bir ortam* oluşturur. Eğer `X`, bir paket dizininin alt diziniyse ve `X/src/X.jl` mevcutsa, o zaman paket `X`, paket dizini ortamında mevcuttur ve `X/src/X.jl`, yüklenme dosyasıdır.

Bunlar **yığın bir ortam** oluşturmak için bir araya getirilebilir: tek bir bileşik ortam oluşturmak için üst üste bindirilmiş bir dizi proje ortamı ve paket dizini. Öncelik ve görünürlük kuralları daha sonra hangi paketlerin mevcut olduğunu ve nereden yükleneceğini belirlemek için bir araya gelir. Örneğin, Julia'nın yükleme yolu yığın bir ortam oluşturur.

Bu ortamların her biri farklı bir amaca hizmet eder:

  * Proje ortamları **tekrar üretilebilirlik** sağlar. Bir proje ortamını sürüm kontrolüne—örneğin bir git deposuna—projenin kaynak kodunun geri kalanıyla birlikte kontrol ederek, projenin ve tüm bağımlılıklarının tam durumunu yeniden üretebilirsiniz. Özellikle manifest dosyası, her bağımlılığın tam sürümünü, kaynak ağacının kriptografik hash'i ile tanımlanmış olarak yakalar; bu, `Pkg`'nin doğru sürümleri almasını ve tüm bağımlılıklar için kaydedilen tam kodu çalıştırdığınızdan emin olmasını mümkün kılar.
  * Paket dizinleri, tam olarak dikkatle izlenen bir proje ortamının gereksiz olduğu durumlarda **kolaylık** sağlar. Bir dizi paketi bir yere koymak ve onları doğrudan kullanabilmek istediğinizde, bu dizinler faydalıdır; bu paketler için bir proje ortamı oluşturmanıza gerek kalmaz.
  * Yığın ortamları, **ekleme** araçları için birincil ortama izin verir. Geliştirme araçları içeren bir ortamı yığının sonuna itebilirsiniz, böylece bunlar REPL ve betiklerden erişilebilir, ancak paketlerin içinden erişilemez.

Yüksek seviyede, her ortam kavramsal olarak üç harita tanımlar: kökler, grafik ve yollar. `import X` ifadesinin anlamını çözerken, `X`'in kimliğini belirlemek için kökler ve grafik haritaları kullanılırken, `X`'in kaynak kodunu bulmak için yollar haritası kullanılır. Üç haritanın belirli rolleri şunlardır:

  * **kökler:** `isim::Sembol` ⟶ `uuid::UUID`

    Bir ortamın kök haritası, ortamın ana projeye (yani `Main`'de yüklenebilen) sunduğu tüm üst düzey bağımlılıkların paket adlarını UUID'lere atar. Julia, ana projede `import X` ile karşılaştığında, `X`'in kimliğini `roots[:X]` olarak arar.
  * **graf:** `context::UUID` ⟶ `name::Sembol` ⟶ `uuid::UUID`

    Bir ortamın grafiği, her `context` UUID'si için isimlerden UUID'lere bir harita atayan çok seviyeli bir haritadır; bu, kökler haritasına benzer ancak o `context`'e özeldir. Julia, `context` UUID'sine sahip paketin kodunda `import X` gördüğünde, `X`'in kimliğini `graph[context][:X]` olarak arar. Özellikle, bu, `import X`'in `context`'e bağlı olarak farklı paketlere atıfta bulunabileceği anlamına gelir.
  * **yollar:** `uuid::UUID` × `name::Symbol` ⟶ `path::String`

    Yollar haritası, her paket UUID-adı çiftine, o paketin giriş noktası kaynak dosyasının konumunu atar. `import X` içindeki `X`'in kimliği, ana projeden mi yoksa bir bağımlılıktan mı yüklendiğine bağlı olarak kökler veya grafik aracılığıyla bir UUID'ye çözülündükten sonra, Julia `X`'i edinmek için hangi dosyanın yüklenmesi gerektiğini ortamda `paths[uuid,:X]`'i kontrol ederek belirler. Bu dosyanın dahil edilmesi, `X` adında bir modül tanımlamalıdır. Bu paket yüklendikten sonra, aynı `uuid`'ye çözülerek yapılan herhangi bir sonraki import, zaten yüklenmiş paket modülüne yeni bir bağlama oluşturacaktır.

Her türlü ortam, bu üç haritayı farklı şekilde tanımlar; aşağıdaki bölümlerde detaylandırılmıştır.

!!! note
    Anlayışı kolaylaştırmak için, bu bölümdeki örnekler kökler, grafik ve yollar için tam veri yapıları göstermektedir. Ancak, Julia'nın paket yükleme kodu bunları açıkça oluşturmaz. Bunun yerine, belirli bir paketi yüklemek için ihtiyaç duyduğu kadarını tembel bir şekilde hesaplar.


### Project environments

Bir proje ortamı, `Project.toml` adlı bir proje dosyasını içeren bir dizin tarafından belirlenir ve isteğe bağlı olarak `Manifest.toml` adlı bir manifest dosyası da içerebilir. Bu dosyalar ayrıca `JuliaProject.toml` ve `JuliaManifest.toml` olarak adlandırılabilir; bu durumda `Project.toml` ve `Manifest.toml` göz ardı edilir. Bu, `Project.toml` ve `Manifest.toml` olarak adlandırılan dosyaları önemli bulan diğer araçlarla birlikte var olmayı sağlar. Ancak saf Julia projeleri için `Project.toml` ve `Manifest.toml` adları tercih edilir. Ancak, Julia v1.10.8'den itibaren, `(Julia)Manifest-v{major}.{minor}.toml` belirli bir manifest dosyasını kullanmak için bir format olarak tanınır; yani aynı klasörde, `Manifest-v1.11.toml` v1.11 tarafından kullanılacak ve `Manifest.toml` diğer herhangi bir Julia sürümü tarafından kullanılacaktır.

Proje ortamının kökleri, grafiği ve yolları aşağıdaki gibi tanımlanmıştır:

**Ortamın kök haritası**, proje dosyasının içeriği tarafından belirlenir; özellikle, en üst düzey `name` ve `uuid` girişleri ile `[deps]` bölümü (hepsi isteğe bağlıdır). Daha önce bahsedilen hayali uygulama `App` için aşağıdaki örnek proje dosyasını dikkate alın:

```toml
name = "App"
uuid = "8f986787-14fe-4607-ba5d-fbff2944afa9"

[deps]
Priv = "ba13f791-ae1d-465a-978b-69c3ad90f72b"
Pub  = "c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"
```

Bu proje dosyası, bir Julia sözlüğü ile temsil edilseydi aşağıdaki kök haritasını ima eder:

```julia
roots = Dict(
    :App  => UUID("8f986787-14fe-4607-ba5d-fbff2944afa9"),
    :Priv => UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b"),
    :Pub  => UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"),
)
```

Verilen bu kök haritasında, `App`'in kodunda `import Priv` ifadesi Julia'nın `roots[:Priv]`'i aramasına neden olacaktır; bu da `Priv` paketinin yükleneceği bağlamda `ba13f791-ae1d-465a-978b-69c3ad90f72b` UUID'sini verir. Bu UUID, ana uygulama `import Priv` ifadesini değerlendirdiğinde hangi `Priv` paketinin yükleneceğini ve kullanılacağını tanımlar.

**Bir projenin ortamının bağımlılık grafiği**, mevcutsa manifest dosyasının içeriğiyle belirlenir. Eğer manifest dosyası yoksa, grafik boştur. Bir manifest dosyası, bir projenin doğrudan veya dolaylı bağımlılıkları için her bir stanzayı içerir. Her bağımlılık için dosya, paketin UUID'sini ve bir kaynak ağacı hash'ini veya kaynak koduna giden açık bir yolu listeler. Aşağıdaki `App` için örnek manifest dosyasını dikkate alın:

```toml
[[Priv]] # the private one
deps = ["Pub", "Zebra"]
uuid = "ba13f791-ae1d-465a-978b-69c3ad90f72b"
path = "deps/Priv"

[[Priv]] # the public one
uuid = "2d15fe94-a1f7-436c-a4d8-07a9a496e01c"
git-tree-sha1 = "1bf63d3be994fe83456a03b874b409cfd59a6373"
version = "0.1.5"

[[Pub]]
uuid = "c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"
git-tree-sha1 = "9ebd50e2b0dd1e110e842df3b433cb5869b0dd38"
version = "2.1.4"

  [Pub.deps]
  Priv = "2d15fe94-a1f7-436c-a4d8-07a9a496e01c"
  Zebra = "f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"

[[Zebra]]
uuid = "f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"
git-tree-sha1 = "e808e36a5d7173974b90a15a353b564f3494092f"
version = "3.4.2"
```

Bu manifest dosyası `App` projesi için olası bir tam bağımlılık grafiğini tanımlar:

  * Uygulamanın kullandığı iki farklı `Priv` adlı paket vardır. Bir özel paket, kök bağımlılık olarak kullanılırken, diğeri `Pub` aracılığıyla dolaylı bir bağımlılık olan bir genel pakettir. Bunlar, farklı UUID'leri ile ayırt edilir ve farklı bağımlılıklara sahiptirler:

      * Özel `Priv`, `Pub` ve `Zebra` paketlerine bağımlıdır.
      * Halka `Priv` hiçbir bağımlılığı yoktur.
  * Uygulama ayrıca, özel `Priv` paketine ve özel `Priv` paketinin bağımlı olduğu aynı `Zebra` paketine bağımlı olan genel `Pub` paketine de bağımlıdır.

Bu bağımlılık grafiği bir sözlük olarak şu şekilde görünmektedir:

```julia
graph = Dict(
    # Priv – the private one:
    UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b") => Dict(
        :Pub   => UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"),
        :Zebra => UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"),
    ),
    # Priv – the public one:
    UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c") => Dict(),
    # Pub:
    UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1") => Dict(
        :Priv  => UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c"),
        :Zebra => UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"),
    ),
    # Zebra:
    UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62") => Dict(),
)
```

Verilen bu bağımlılık `grafiği`, Julia `Pub` paketinde UUID `c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1` olan `import Priv` gördüğünde, bakar:

```julia
graph[UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1")][:Priv]
```

ve `2d15fe94-a1f7-436c-a4d8-07a9a496e01c` alır, bu da `Pub` paketinin bağlamında `import Priv` ifadesinin, uygulamanın doğrudan bağımlı olduğu özel olan yerine, genel `Priv` paketini ifade ettiğini gösterir. Bu, `Priv` adının ana projedeki farklı paketlerden farklı paket bağımlılıklarında referans verebilmesini sağlar ve bu da paket ekosisteminde aynı isimlerin tekrar etmesine olanak tanır.

`import Zebra` if `App` kod tabanında değerlendirilirse ne olur? `Zebra` proje dosyasında görünmediği için, import başarısız olacaktır, oysa `Zebra` manifest dosyasında *vardır*. Dahası, `import Zebra` kamuya açık `Priv` paketinde—UUID'si `2d15fe94-a1f7-436c-a4d8-07a9a496e01c` olan—gerçekleşirse, bu da başarısız olacaktır çünkü o `Priv` paketinin manifest dosyasında beyan edilmiş bağımlılıkları yoktur ve bu nedenle herhangi bir paketi yükleyemez. `Zebra` paketi yalnızca manifest dosyasında açık bir bağımlılık olarak göründüğü paketler tarafından yüklenebilir: `Pub` paketi ve `Priv` paketlerinden biri.

**Bir projenin ortamının yollar haritası**, manifest dosyasından çıkarılır. `X` adındaki `uuid` paketinin yolu, bu kurallara (sırayla) göre belirlenir:

1. Eğer dizindeki proje dosyası `uuid` ile eşleşiyorsa ve adı `X` ise, o zaman ya:

      * Üst düzey bir `path` girişi var, ardından `uuid` bu yola haritalanacak ve proje dosyasını içeren dizine göre yorumlanacaktır.
      * Aksi takdirde, `uuid` proje dosyasını içeren dizine göre `src/X.jl` dosyasına eşlenir.
2. Eğer yukarıdaki durum geçerli değilse ve proje dosyasının karşılık gelen bir manifest dosyası varsa ve manifest `uuid` ile eşleşen bir dize içeriyorsa, o zaman:

      * Eğer bir `path` girişi varsa, o yolu kullanın (manifest dosyasının bulunduğu dizine göre göreceli).
      * Eğer bir `git-tree-sha1` girişi varsa, `uuid` ve `git-tree-sha1`'in deterministik bir hash fonksiyonunu hesaplayın - buna `slug` denir - ve Julia `DEPOT_PATH` global dizisindeki her dizinde `packages/X/$slug` adında bir dizin arayın. Mevcut olan ilk dizini kullanın.

Eğer bu sonuçlardan herhangi biri başarıyla sonuçlanırsa, kaynak kodu giriş noktasına giden yol ya o sonuç olacaktır, ya da o sonucun yanındaki `src/X.jl` ile birlikte olan göreli yol olacaktır; aksi takdirde, `uuid` için bir yol eşlemesi yoktur. `X` yüklenirken, eğer hiçbir kaynak kodu yolu bulunamazsa, arama başarısız olacak ve kullanıcıya uygun paket sürümünü yüklemesi veya başka düzeltici eylemler alması (örneğin, `X`'i bir bağımlılık olarak beyan etmesi) için bir istemde bulunulabilir.

Yukarıdaki örnek manifest dosyasında, ilk `Priv` paketinin yolunu bulmak için—UUID'si `ba13f791-ae1d-465a-978b-69c3ad90f72b` olan—Julia manifest dosyasında onun stanzasını arar, bir `path` girişi olduğunu görür, `App` proje dizinine göre `deps/Priv`'e bakar—varsayalım ki `App` kodu `/home/me/projects/App` içinde yaşıyor—`/home/me/projects/App/deps/Priv`'in var olduğunu görür ve bu nedenle `Priv`'i oradan yükler.

Eğer Julia, UUID'si `2d15fe94-a1f7-436c-a4d8-07a9a496e01c` olan *diğer* `Priv` paketini yüklüyorsa, manifestodaki bölümünü bulur, `path` girişinin olmadığını görür, ancak bir `git-tree-sha1` girişinin olduğunu görür. Ardından, bu UUID/SHA-1 çifti için `slug`'u hesaplar; bu `HDkrT`'dir (bu hesaplamanın tam detayları önemli değildir, ancak tutarlıdır ve belirleyicidir). Bu, bu `Priv` paketinin yolunun `packages/Priv/HDkrT/src/Priv.jl` olacağı anlamına gelir. `DEPOT_PATH` içeriği `["/home/me/.julia", "/usr/local/julia"]` ise, Julia aşağıdaki yolları kontrol edecektir:

1. `/home/me/.julia/packages/Priv/HDkrT`
2. `/usr/local/julia/packages/Priv/HDkrT`

Julia, bulunduğu depoda `packages/Priv/HDKrT/src/Priv.jl` dosyasından kamuya açık `Priv` paketini yüklemeye çalışmak için bunlardan ilki mevcut olanı kullanır.

İşte yukarıda verilen Manifest'te bağımlılık grafiği için sağlanan örnek `App` proje ortamı için olası yollar haritasının bir temsili:

```julia
paths = Dict(
    # Priv – the private one:
    (UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b"), :Priv) =>
        # relative entry-point inside `App` repo:
        "/home/me/projects/App/deps/Priv/src/Priv.jl",
    # Priv – the public one:
    (UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c"), :Priv) =>
        # package installed in the system depot:
        "/usr/local/julia/packages/Priv/HDkr/src/Priv.jl",
    # Pub:
    (UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"), :Pub) =>
        # package installed in the user depot:
        "/home/me/.julia/packages/Pub/oKpw/src/Pub.jl",
    # Zebra:
    (UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"), :Zebra) =>
        # package installed in the system depot:
        "/usr/local/julia/packages/Zebra/me9k/src/Zebra.jl",
)
```

Bu örnek harita, üç farklı paket konumunu içermektedir (birinci ve üçüncü, varsayılan yükleme yolunun bir parçasıdır):

1. Özel `Priv` paketi, `App` deposundaki "[vendored](https://stackoverflow.com/a/35109534)" içindedir.
2. Halka `Priv` ve `Zebra` paketleri sistem deposundadır; burada sistem yöneticisi tarafından kurulan ve yönetilen paketler bulunur. Bu paketler sistemdeki tüm kullanıcılar için mevcuttur.
3. `Pub` paketi, kullanıcı deponuzda bulunmaktadır; burada kullanıcı tarafından yüklenen paketler yaşamaktadır. Bu paketler yalnızca onları yükleyen kullanıcıya açıktır.

### Package directories

Paket dizinleri, ad çakışmalarını yönetme yeteneği olmadan daha basit bir ortam sağlar. Bir paket dizininde, üst düzey paketlerin kümesi, "paket gibi görünen" alt dizinler kümesidir. Bir paket `X`, dizin aşağıdaki "giriş noktası" dosyalarından birini içeriyorsa bir paket dizininde var olur:

  * `X.jl`
  * `X/src/X.jl`
  * `X.jl/src/X.jl`

Bir paket dizinindeki bir paketin hangi bağımlılıkları içe aktarabileceği, paketin bir proje dosyası içerip içermediğine bağlıdır:

  * Eğer bir proje dosyası varsa, yalnızca proje dosyasının `[deps]` bölümünde tanımlanan paketleri içe aktarabilir.
  * Eğer bir proje dosyası yoksa, herhangi bir üst düzey paketi içe aktarabilir—yani `Main` veya REPL'de yüklenebilen aynı paketler.

**Kökler haritası**, paket dizininin içeriğini inceleyerek mevcut olan tüm paketlerin bir listesini oluşturmakla belirlenir. Ayrıca, her bir girişe aşağıdaki gibi bir UUID atanacaktır: `X` klasörü içinde bulunan bir paket için...

1. Eğer `X/Project.toml` mevcutsa ve bir `uuid` girişi varsa, o zaman `uuid` bu değerdir.
2. Eğer `X/Project.toml` mevcutsa ve ancak üst düzey bir UUID girişi yoksa, `uuid`, `X/Project.toml` dosyasının kanonik (gerçek) yolunu hashleyerek oluşturulan sahte bir UUID'dir.
3. Aksi takdirde (`Project.toml` yoksa), o zaman `uuid` tüm sıfırlardan oluşan [nil UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier#Nil_UUID) olacaktır.

**Bir projenin bağımlılık grafi** bir proje dizininde, her paketin alt dizinindeki proje dosyalarının varlığı ve içeriği ile belirlenir. Kurallar şunlardır:

  * Eğer bir paket alt dizininde proje dosyası yoksa, o zaman grafikten çıkarılır ve kodundaki import ifadeleri ana proje ve REPL ile aynı şekilde üst düzey olarak değerlendirilir.
  * Eğer bir paket alt dizininde bir proje dosyası varsa, o zaman UUID'si için grafik girişi proje dosyasının `[deps]` haritasıdır; bu bölüm yoksa boş olarak kabul edilir.

Bir örnek olarak, bir paket dizininin aşağıdaki yapıya ve içeriğe sahip olduğunu varsayalım:

```
Aardvark/
    src/Aardvark.jl:
        import Bobcat
        import Cobra

Bobcat/
    Project.toml:
        [deps]
        Cobra = "4725e24d-f727-424b-bca0-c4307a3456fa"
        Dingo = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Bobcat.jl:
        import Cobra
        import Dingo

Cobra/
    Project.toml:
        uuid = "4725e24d-f727-424b-bca0-c4307a3456fa"
        [deps]
        Dingo = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Cobra.jl:
        import Dingo

Dingo/
    Project.toml:
        uuid = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Dingo.jl:
        # no imports
```

İşte bir sözlük olarak temsil edilen karşılık gelen kök yapısı:

```julia
roots = Dict(
    :Aardvark => UUID("00000000-0000-0000-0000-000000000000"), # no project file, nil UUID
    :Bobcat   => UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf"), # dummy UUID based on path
    :Cobra    => UUID("4725e24d-f727-424b-bca0-c4307a3456fa"), # UUID from project file
    :Dingo    => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"), # UUID from project file
)
```

İşte bir sözlük olarak temsil edilen karşılık gelen grafik yapısı:

```julia
graph = Dict(
    # Bobcat:
    UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf") => Dict(
        :Cobra => UUID("4725e24d-f727-424b-bca0-c4307a3456fa"),
        :Dingo => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"),
    ),
    # Cobra:
    UUID("4725e24d-f727-424b-bca0-c4307a3456fa") => Dict(
        :Dingo => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"),
    ),
    # Dingo:
    UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc") => Dict(),
)
```

Birkaç genel kuralı not etmek gerekir:

1. Bir proje dosyası olmadan bir paket, herhangi bir üst düzey bağımlılığa bağımlı olabilir ve bir paket dizinindeki her paket üst düzeyde mevcut olduğundan, ortamda bulunan tüm paketleri içe aktarabilir.
2. Bir proje dosyası olan bir paket, proje dosyası olmayan bir pakete bağımlı olamaz çünkü proje dosyası olan paketler yalnızca `graph` içindeki paketleri yükleyebilir ve proje dosyası olmayan paketler `graph` içinde görünmez.
3. Bir proje dosyası olan ancak açık bir UUID'ye sahip olmayan bir paket yalnızca proje dosyası olmayan paketler tarafından bağımlı olarak kullanılabilir, çünkü bu paketlere atanan sahte UUID'ler tamamen içseldir.

Lütfen aşağıdaki örnekte bu kuralların belirli örneklerini gözlemleyin:

  * `Aardvark`, `Bobcat` veya `Cobra` veya `Dingo`'dan herhangi birini içe aktarabilir; `Bobcat` ve `Cobra`'yı içe aktarır.
  * `Bobcat`, hem `Cobra` hem de `Dingo`'yu içe aktarabilir ve içe aktarır; her ikisi de UUID'lere sahip proje dosyalarına sahiptir ve `Bobcat`'in `[deps]` bölümünde bağımlılıklar olarak belirtilmiştir.
  * `Bobcat` `Aardvark`'a bağımlı olamaz çünkü `Aardvark`'ın bir proje dosyası yok.
  * `Cobra`, `Dingo`'yu içe aktarabilir ve içe aktarır; `Dingo`'nun bir proje dosyası ve UUID'si vardır ve `Cobra`'nın `[deps]` bölümünde bir bağımlılık olarak belirtilmiştir.
  * `Cobra` `Aardvark` veya `Bobcat`'a bağımlı olamaz çünkü ikisinin de gerçek UUID'leri yoktur.
  * `Dingo` hiçbir şey içe aktaramaz çünkü `[deps]` bölümü olmayan bir proje dosyasına sahiptir.

**Yollar haritası** bir paket dizininde basittir: alt dizin adlarını karşılık gelen giriş noktası yollarına eşler. Başka bir deyişle, örnek proje dizinimizin yolu `/home/me/animals` ise, `paths` haritası bu sözlükle temsil edilebilir:

```julia
paths = Dict(
    (UUID("00000000-0000-0000-0000-000000000000"), :Aardvark) =>
        "/home/me/AnimalPackages/Aardvark/src/Aardvark.jl",
    (UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf"), :Bobcat) =>
        "/home/me/AnimalPackages/Bobcat/src/Bobcat.jl",
    (UUID("4725e24d-f727-424b-bca0-c4307a3456fa"), :Cobra) =>
        "/home/me/AnimalPackages/Cobra/src/Cobra.jl",
    (UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"), :Dingo) =>
        "/home/me/AnimalPackages/Dingo/src/Dingo.jl",
)
```

Bir paket dizini ortamındaki tüm paketler, tanım gereği, beklenen giriş noktası dosyalarıyla alt dizinler olduğundan, `paths` haritası girişleri her zaman bu biçimde olur.

### Environment stacks

Üçüncü ve son tür ortam, diğer ortamları birleştirerek birkaçını üst üste koyan bir ortamdır ve her birindeki paketleri tek bir bileşik ortamda kullanılabilir hale getirir. Bu bileşik ortamlar *ortam yığınları* olarak adlandırılır. Julia `LOAD_PATH` globali bir ortam yığını tanımlar—Julia işleminin çalıştığı ortam. Julia işleminizin yalnızca bir proje veya paket dizinindeki paketlere erişmesini istiyorsanız, bunu `LOAD_PATH`'deki tek giriş yapın. Ancak, üzerinde çalıştığınız projenin bağımlılıkları olmasa bile, bazı favori araçlarınıza—standart kütüphaneler, profil oluşturucular, hata ayıklayıcılar, kişisel yardımcı programlar vb.—erişim sağlamak genellikle oldukça faydalıdır. Bu araçları içeren bir ortamı yükleme yoluna ekleyerek, bunlara hemen üst düzey kodda erişim sağlarsınız ve projeye eklemenize gerek kalmaz.

Ortam yığını bileşenlerinin kök, grafik ve yollar veri yapılarının birleştirilmesi mekanizması basittir: bunlar, anahtar çakışması durumunda daha önceki girişleri daha sonraki girişlere tercih ederek sözlükler olarak birleştirilir. Başka bir deyişle, eğer `stack = [env₁, env₂, …]` varsa, o zaman:

```julia
roots = reduce(merge, reverse([roots₁, roots₂, …]))
graph = reduce(merge, reverse([graph₁, graph₂, …]))
paths = reduce(merge, reverse([paths₁, paths₂, …]))
```

Alt simgeli `rootsᵢ`, `graphᵢ` ve `pathsᵢ` değişkenleri, `stack` içinde bulunan alt simgeli ortamlar `envᵢ` ile ilişkilidir. `reverse` burada, `merge`'in argüman sözlüklerindeki anahtarlar arasında çakışmalar olduğunda son argümanı ilk argümandan daha fazla tercih etmesinden dolayı mevcuttur. Bu tasarımın birkaç dikkate değer özelliği vardır:

1. *birincil ortam*—yani bir yığın içindeki ilk ortam—sadık bir şekilde yığın ortamına gömülmüştür. Bir yığın içindeki ilk ortamın tam bağımlılık grafiği, tüm bağımlılıkların aynı sürümlerini de içerecek şekilde yığın ortamında eksiksiz bir şekilde yer alması garanti edilmektedir.
2. Paketler, birincil olmayan ortamlarda, kendi ortamları tamamen uyumlu olsa bile, bağımlılıklarının uyumsuz sürümlerini kullanabilir. Bu, bağımlılıklarından birinin, yığın içindeki daha önceki bir ortamda (graf veya yol, ya da her ikisi tarafından) gölgelenmesi durumunda meydana gelebilir.

Proje üzerinde çalıştığınız bir projenin ana ortamı genellikle birincil ortam olduğundan, yığın içindeki sonraki ortamlar ek araçlar içerdiğinden, bu doğru bir denge: geliştirme araçlarınızı bozmak ama projeyi çalışır durumda tutmak daha iyidir. Böyle uyumsuzluklar meydana geldiğinde, genellikle ana projeyle uyumlu olan sürümlere geliştirme araçlarınızı güncellemek istersiniz.

### [Package Extensions](@id man-extensions)

Bir "uzantı" paketi, belirli bir dizi diğer paketin (onun "tetikleyicileri") mevcut Julia oturumunda yüklendiğinde otomatik olarak yüklenen bir modüldür. Uzantılar, proje dosyasındaki `[extensions]` bölümünde tanımlanır. Bir uzantının tetikleyicileri, proje dosyasının `[weakdeps]` (ve muhtemelen, ancak nadiren `[deps]`) bölümünde listelenen paketlerin bir alt kümesidir. Bu paketler, diğer paketler gibi uyumluluk girişlerine sahip olabilir.

```toml
name = "MyPackage"

[compat]
ExtDep = "1.0"
OtherExtDep = "1.0"

[weakdeps]
ExtDep = "c9a23..." # uuid
OtherExtDep = "862e..." # uuid

[extensions]
BarExt = ["ExtDep", "OtherExtDep"]
FooExt = "ExtDep"
...
```

`extensions` altındaki anahtarlar uzantıların adlarıdır. Sağ taraftaki tüm paketler (o uzantının tetikleyicileri) yüklendiğinde yüklenirler. Bir uzantının yalnızca bir tetikleyicisi varsa, tetikleyicilerin listesi kısalık için sadece bir dize olarak yazılabilir. Uzantının giriş noktası ya `ext/FooExt.jl` ya da `ext/FooExt/FooExt.jl` şeklindedir, burada uzantı `FooExt`'dir. Bir uzantının içeriği genellikle şu şekilde yapılandırılmıştır:

```
module FooExt

# Load main package and triggers
using MyPackage, ExtDep

# Extend functionality in main package with types from the triggers
MyPackage.func(x::ExtDep.SomeStruct) = ...

end
```

Bir uzantıya sahip bir paket bir ortama eklendiğinde, `weakdeps` ve `extensions` bölümleri, o paketin manifest dosyasındaki bölümde saklanır. Bir paketin bağımlılık arama kuralları, "ebeveyn" paketiyle aynı olup, listelenen tetikleyiciler de bağımlılık olarak dikkate alınır.

### [Package/Environment Preferences](@id preferences)

Tercihler, bir ortam içindeki paket davranışını etkileyen meta verilerin sözlükleridir. Tercih sistemi, derleme zamanında tercihleri okuma desteği sunar; bu, kod yükleme zamanında, Julia'nın seçtiği ön derleme dosyalarının mevcut ortamla aynı tercihlerle oluşturulduğundan emin olmamız gerektiği anlamına gelir. Tercihleri değiştirmek için kamu API'si [Preferences.jl](https://github.com/JuliaPackaging/Preferences.jl) paketinde bulunmaktadır. Tercihler, mevcut aktif projenin yanındaki `(Julia)LocalPreferences.toml` dosyası içinde TOML sözlükleri olarak saklanır. Bir tercih "dışa aktarılmışsa", bunun yerine `(Julia)Project.toml` içinde saklanır. Amaç, paylaşılan projelerin paylaşılan tercihlere sahip olmasına izin vermek, aynı zamanda kullanıcıların kendi ayarlarıyla bu tercihleri LocalPreferences.toml dosyasında geçersiz kılmalarına olanak tanımaktır; bu dosya, isminin ima ettiği gibi .gitignore edilmelidir.

Derleme sırasında erişilen tercihler otomatik olarak derleme zamanı tercihleri olarak işaretlenir ve bu tercihlerde kaydedilen herhangi bir değişiklik, Julia derleyicisinin o modül için önceden derlenmiş dosyaların (`.ji` ve ilgili `.so`, `.dll` veya `.dylib` dosyaları) önbelleğini yeniden derlemesine neden olacaktır. Bu, derleme sırasında tüm derleme zamanı tercihlerinin hash'ini seri hale getirerek yapılır ve ardından uygun dosyaları yüklemek için mevcut ortamla bu hash karşılaştırılır.

Tercihler, depo genel varsayılanları ile ayarlanabilir; eğer Foo paketi küresel ortamınızda yüklüyse ve tercihler ayarlanmışsa, bu tercihler küresel ortamınız `LOAD_PATH`'ınızın bir parçası olduğu sürece geçerli olacaktır. Ortam yığınındaki daha üstteki ortamlardaki tercihler, yükleme yolundaki daha yakın girişler tarafından geçersiz kılınır ve bu, şu anda aktif olan projeyle sona erer. Bu, depo genel tercih varsayılanlarının var olmasına olanak tanır; aktif projeler bu miras alınan tercihleri birleştirebilir veya hatta tamamen geçersiz kılabilir. Birleştirmeyi sağlamak veya engellemek için tercihleri ayarlamanın tam ayrıntıları için `Preferences.set_preferences!()` doküman dizesine bakın.

## Conclusion

Federated paket yönetimi ve kesin yazılım yeniden üretilebilirliği, bir paket sisteminde zor ama değerli hedeflerdir. Bu hedeflerin birleşimi, çoğu dinamik dilin sahip olduğundan daha karmaşık bir paket yükleme mekanizması ile sonuçlanır, ancak aynı zamanda statik dillerle daha yaygın olarak ilişkilendirilen ölçeklenebilirlik ve yeniden üretilebilirlik sağlar. Genellikle, Julia kullanıcıları, bu etkileşimlerin kesin bir anlayışına ihtiyaç duymadan projelerini yönetmek için yerleşik paket yöneticisini kullanabilmelidir. `Pkg.add("X")` çağrısı, `Pkg.activate("Y")` ile seçilen uygun proje ve manifest dosyalarına ekleyecektir, böylece gelecekteki bir `import X` çağrısı, daha fazla düşünmeye gerek kalmadan `X`'i yükleyecektir.
