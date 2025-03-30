```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/NEWS.md"
```

# Julia v1.11 Release Notes

## New language features

  * Yeni `Memory` türü, `Array`'e alternatif olarak daha düşük seviyeli bir konteyner sağlar. `Memory`, daha az yük ve daha hızlı bir yapıcıya sahiptir, bu da onu `Array`'in tüm özelliklerine ihtiyaç duymayan durumlar için iyi bir seçim haline getirir (örneğin, çok boyutlu). Artık `Array` türünün çoğu, Julia'da `Memory` üzerine uygulanmıştır ve bu da birkaç işlev (örneğin, `push!`) için önemli hız artışları ve daha sürdürülebilir kodlar sağlamaktadır ([#51319](https://github.com/JuliaLang/julia/issues/51319)).
  * `public` yeni bir anahtar kelimedir. `public` ile işaretlenmiş semboller kamu API'si olarak kabul edilir. `export` ile işaretlenmiş semboller de artık kamu API'si olarak muamele görmektedir. `public` ve `export` arasındaki fark, `public` isimlerinin bir paket/modül ([#50105](https://github.com/JuliaLang/julia/issues/50105)) kullanıldığında mevcut olmamasıdır.
  * `ScopedValue`, dinamik kapsamı görevler arasında miras alarak uygular ([#50958](https://github.com/JuliaLang/julia/issues/50958)).
  * `Manifest.toml` dosyaları artık belirli bir julia sürümü tarafından tercih edilmek üzere `Manifest-v{major}.{minor}.toml` formatında yeniden adlandırılabilir. Yani, aynı klasörde, `Manifest-v1.11.toml` v1.11 tarafından kullanılacak ve `Manifest.toml` diğer tüm julia sürümleri tarafından kullanılacaktır. Bu, aynı anda birden fazla julia sürümü için ortamları yönetmeyi kolaylaştırır ([#43845](https://github.com/JuliaLang/julia/issues/43845)).
  * Unicode 15.1 desteği ([#51799](https://github.com/JuliaLang/julia/issues/51799)).

## Language changes

  * Ön derleme sırasında, `atexit` kancaları artık çıktı dosyasını kaydetmeden önce çalıştırılıyor. Bu, kullanıcıların arka plan durumunu güvenli bir şekilde sona erdirmesine (örneğin, `Timer`'ları kapatmak ve kalp atışı görevlerine bağlantı kesme bildirimleri göndermek) ve program çıkış yapmaya başlamak istediğinde diğer kaynakları temizlemesine olanak tanır.
  * Kod kapsamı ve malloc takibi artık paket ön derleme aşamasında üretilmiyor. Ayrıca, bu modlar sırasında izlenmeyen paketler için artık pkgimage önbellekleri kullanılmaktadır. Bu, kapsama testinin (`julia-actions/julia-runtest` için varsayılan) varsayılan olarak test edilen paket dışındaki tüm diğer paketler için pkgimage önbelleklerini kullanacağı anlamına geliyor, bu da muhtemelen daha hızlı test yürütme süresi anlamına geliyor ([#52123](https://github.com/JuliaLang/julia/issues/52123)).
  * `JULIA_DEPOT_PATH`'te bir yol belirtmek artık boş dizelerin genişletilmesiyle varsayılan kullanıcı deposunun ([#51448](https://github.com/JuliaLang/julia/issues/51448)) hariç tutulmasına neden olmaktadır.
  * Ön derleme önbellek dosyaları artık taşınabilir ve geçerlilikleri artık kaynak dosyalarının `mtime`'ı yerine içerik hash'i ile doğrulanıyor ([#49866](https://github.com/JuliaLang/julia/issues/49866)).
  * Uzantılar artık, bağımlı oldukları diğer uzantıların tüm tetikleyicilerini içeren tetikleyicilere sahip oldukları takdirde diğer uzantılara bağımlı olabilirler (+ en az bir başka tetikleyici). Bu gereksinimi karşılamayan uzantıdan uzantıya bağımlılıklar, uzantı döngülerini önlemek için ön derleme sırasında `Base.get_extension` kullanmalarına engel olunmuştur [#55557](https://github.com/JuliaLang/julia/issues/55557).

## Compiler/Runtime improvements

  * Güncellenmiş GC heuristikleri, bireysel nesneler yerine tahsis edilen sayfaları saymak için güncellendi ([#50144](https://github.com/JuliaLang/julia/issues/50144)).
  * `Base.@assume_effects` üzerinde kod bloklarına not ekleme desteği eklendi ([#52400](https://github.com/JuliaLang/julia/issues/52400)).

## Command-line option changes

  * The entry point for Julia has been standardized to `Main.main(args)`. This must be explicitly opted into using the `@main` macro (see the docstring for further details). When opted-in, and `julia` is invoked to run a script or expression (i.e. using `julia script.jl` or `julia -e expr`), `julia` will subsequently run the `Main.main` function automatically. This is intended to unify script and compilation workflows, where code loading may happen in the compiler and execution of `Main.main` may happen in the resulting executable. For interactive use, there is no semantic difference between defining a `main` function and executing the code directly at the end of the script ([#50974](https://github.com/JuliaLang/julia/issues/50974)).
  * `--compiled-modules` ve `--pkgimages` bayrakları artık `existing` olarak ayarlanabilir, bu da Julia'nın mevcut önbellek dosyalarını yüklemeyi düşünmesine neden olur, ancak yeni dosyalar oluşturmaz ([#50586](https://github.com/JuliaLang/julia/issues/50586), [#52573](https://github.com/JuliaLang/julia/issues/52573)).
  * `--project` argümanı artık, geçilen betik dosyasına göre bir Project.toml dosyasının bulunduğu bir dizin yolu vermek için `@script`'i kabul ediyor. `foo` alt dizini için `--project=@script/foo`. Eğer (yani `--project=@script`) sonrasında bir yol verilmezse, (tıpkı `--project=@.` gibi) dizin ve üst dizinleri bir Project.toml aramak için taranır ([#50864](https://github.com/JuliaLang/julia/issues/50864) ve [#53352](https://github.com/JuliaLang/julia/issues/53352))

## Multi-threading changes

  * `Threads.@threads` now supports the `:greedy` scheduler, intended for non-uniform workloads ([#52096](https://github.com/JuliaLang/julia/issues/52096)).
  * A new public (but unexported) struct `Base.Lockable{T, L<:AbstractLock}` makes it easy to bundle a resource and its lock together ([#52898](https://github.com/JuliaLang/julia/issues/52898)).

## Build system changes

  * Yeni bir `Makefile` var, Julia ve LLVM'yi profil rehberli ve bağlantı zamanı optimizasyonları (PGO ve LTO) stratejilerini kullanarak derlemek için, `contrib/pgo-lto/Makefile`'a bakın ([#45641](https://github.com/JuliaLang/julia/issues/45641)).

## New library functions

  * Üç yeni tür, "notlar" (`Pair{Symbol, Any}` girişleri, örneğin `:lang => "en"` veya `:face => :magenta` gibi) fikri etrafında oluşturulmuştur. Bu notlar, mümkün olduğunda işlemler (örneğin `*` ile string birleştirme) boyunca korunur.

      * `AnnotatedString`, yeni bir `AbstractString` türüdür. Temel bir dizeyi sarar ve dize bölgelerine ek açıklamalar eklenmesine olanak tanır. Bu tür, stil bilgilerini tutmak için yeni `StyledStrings` standart kütüphanesinde yaygın olarak kullanılmaktadır.
      * `AnnotatedChar`, yeni bir `AbstractChar` türüdür. Başka bir karakteri sarar ve ona uygulanan bir dizi notu tutar.
      * `AnnotatedIOBuffer`, yeni bir `IO` türüdür ve bir `IOBuffer`'ı taklit eder, ancak anotasyonlu içerik için özel `read`/`write` yöntemlerine sahiptir. Bu, hem bir tür "string builder" olarak hem de anotasyonlu ve anotasyonsuz içerik arasında bir yapıştırıcı olarak düşünülebilir.
  * `in!(x, s::AbstractSet)` `x` `s` `x` `s` `x` [#45156](https://github.com/JuliaLang/julia/issues/45156), [#51636](https://github.com/JuliaLang/julia/issues/51636).
  * Yeni `Libc.mkfifo` fonksiyonu, Unix platformlarındaki `mkfifo` C fonksiyonunu sarmalar. ([#34587](https://github.com/JuliaLang/julia/issues/34587))
  * `logrange(start, stop; length)` sabit oranlı bir aralık oluşturur, sabit adım yerine. ([#39071](https://github.com/JuliaLang/julia/issues/39071))
  * `copyuntil(out, io, delim)` ve `copyline(out, io)` verileri bir `out::IO` akışına kopyalar ([#48273](https://github.com/JuliaLang/julia/issues/48273)).
  * `eachrsplit(string, pattern)` sağdan sola doğru alt dizeleri ayırır ([#51646](https://github.com/JuliaLang/julia/issues/51646)).
  * `Sys.username()` şu anki kullanıcının kullanıcı adını döndürmek için kullanılabilir ([#51897](https://github.com/JuliaLang/julia/issues/51897)).
  * `Sys.isreadable(), Sys.iswritable()` mevcut kullanıcının okuma ve yazma izinlerine sahip olup olmadığını kontrol etmek için kullanılabilir. ([#53320](https://github.com/JuliaLang/julia/issues/53320)).
  * `GC.logging_enabled()` GC günlüğü kaydının `GC.enable_logging` aracılığıyla etkinleştirilip etkinleştirilmediğini test etmek için kullanılabilir ([#51647](https://github.com/JuliaLang/julia/issues/51647)).
  * `IdSet` artık Base'den dışa aktarılıyor ve kamuya açık olarak kabul ediliyor ([#53262](https://github.com/JuliaLang/julia/issues/53262)).
  * `@time` şimdi, bir `ReentrantLock`'un beklemek zorunda kaldığı herhangi bir kilit çatışmasının sayısını rapor eder, ayrıca bu sayıyı döndüren yeni bir makro `@lock_conflicts` vardır ([#52883](https://github.com/JuliaLang/julia/issues/52883)).
  * Yeni makro `Base.Cartesian.@ncallkw`, `Base.Cartesian.@ncall` ile benzerlik gösterir, ancak fonksiyon çağrısına anahtar kelime argümanları eklemeye olanak tanır ([#51501](https://github.com/JuliaLang/julia/issues/51501)).
  * Yeni fonksiyon `Docs.hasdoc(module, symbol)` bir ismin dokümantasyon dizesine sahip olup olmadığını belirtir ([#52139](https://github.com/JuliaLang/julia/issues/52139)).
  * Yeni fonksiyon `Docs.undocumented_names(module)` bir modülün belgelenmemiş kamu adlarını döndürür ([#52413](https://github.com/JuliaLang/julia/issues/52413)).

## New library features

  * `invmod(n, T)` burada `T` yerel bir tam sayı türüdür ve `n`'nin `T`'nin tanımladığı modüler tam sayı halkasında modüler tersini hesaplar ([#52180](https://github.com/JuliaLang/julia/issues/52180)).
  * `invmod(n)` is an abbreviation for `invmod(n, typeof(n))` for native integer types ([#52180](https://github.com/JuliaLang/julia/issues/52180)).
  * `replace(string, pattern...)` artık bir akışa çıktı yazmak için isteğe bağlı bir `IO` argümanını destekliyor, bu da bir dize döndürmek yerine ([#48625](https://github.com/JuliaLang/julia/issues/48625)).
  * Yeni yöntemler `allequal(f, itr)` ve `allunique(f, itr)` bir predikat fonksiyonu alır ([#47679](https://github.com/JuliaLang/julia/issues/47679)).
  * `sizehint!(s, n)` artık küçültmeyi devre dışı bırakmak için isteğe bağlı bir `shrink` argümanını destekliyor ([#51929](https://github.com/JuliaLang/julia/issues/51929)).
  * `Process` spawn için bir stdout argümanı olarak bir `IOBuffer` geçmek artık beklenildiği gibi çalışıyor, `wait` veya `success` ile senkronize, bu nedenle veri yarışlarını önlemek için orada bir `Base.BufferStream` gerekli değildir ([#52461](https://github.com/JuliaLang/julia/issues/52461)).
  * Bir işlem çıkış yaptıktan sonra, `closewrite` ona geçirilen akışta otomatik olarak çağrılmayacaktır. İçeriğin tamamen yazıldığından emin olmak için bunun yerine işlem üzerinde `wait` çağrısı yapın, ardından veri yarışlarını önlemek için `closewrite`'ı manuel olarak çağırın veya tüm bunların otomatik olarak halledilmesi için `open`'ın geri çağırma biçimini kullanın ([#52461](https://github.com/JuliaLang/julia/issues/52461)).
  * `@timed` artık ek olarak geçen derleme ve yeniden derleme süresini döndürmektedir ([#52889](https://github.com/JuliaLang/julia/issues/52889)).
  * `filter` artık bir `NamedTuple` üzerinde işlem yapabilir ([#50795](https://github.com/JuliaLang/julia/issues/50795)).
  * `Iterators.cycle(iter, n)` runs over `iter` a fixed number of times, instead of forever ([#47354](https://github.com/JuliaLang/julia/issues/47354)).
  * `zero(::AbstractArray)` now applies recursively, so `zero([[1,2],[3,4,5]])` now produces the additive identity `[[0,0],[0,0,0]]` rather than erroring ([#38064](https://github.com/JuliaLang/julia/issues/38064)).
  * `include_dependency(path; track_content=true)` önceden derleme bağımlılığının `mtime` kullanımından, önceden derleme önbelleklerinin taşınabilirliğini geri kazanmak için hashing'e geçiş yapmayı sağlar ([#51798](https://github.com/JuliaLang/julia/issues/51798)).

## Standard library changes

  * Geri dönüş yöntemi `write(::IO, ::AbstractArray)` artık her bir öğe üzerinde `write` çağrısı yapmak yerine, her değerin bellek içindeki temsilini yazar. Örneğin, `write(io, 'a':'b')` artık her karakter için 4 bayt yazar, her karakterin UTF-8 temsilini yazmak yerine. Yeni format, `Array` tarafından kullanılan formatla uyumludur ve verileri geri almak için `read!` kullanılmasını mümkün kılar ([#42593](https://github.com/JuliaLang/julia/issues/42593)).
  * `length` için durumlu iteratörlerin genel olarak tutarlı bir şekilde tanımlanması mümkün değildir. `Stateful` iteratörler için sessizce yanlış sonuçlar alma potansiyeli, `length(::Stateful)` yönteminin silinmesiyle ele alınmıştır. `Stateful`'ın son tür parametresi de kaldırılmıştır. Sorun: ([#47790](https://github.com/JuliaLang/julia/issues/47790)), PR: ([#51747](https://github.com/JuliaLang/julia/issues/51747)).

#### Package Manager

  * Artık Project.toml dosyasındaki `[sources]` bölümünde paketler için "kaynaklar" belirtmek mümkündür. Bu, kaydedilmemiş normal veya test bağımlılıkları eklemek için kullanılabilir.
  * Pkg artık `[compat]` sınırlarına uymaktadır ve `Project.toml` içindeki sınırlarla uyumsuz olan bir Julia ikili sürümü çalıştırıldığında bir hata verir. Pkg, Registry paketleri ile çalışırken her zaman bu uyumu sağlamıştır. Bu değişiklik, çoğunlukla yerel paketleri etkilemektedir.
  * `pkg> add` ve `Pkg.add` artık aktif ortam bir paket (bir `name` ve `uuid` girişi varsa) olduğunda yeni doğrudan bağımlılıklar için uyumluluk girişleri ekleyecektir.
  * Bağımlılıklar artık doğrudan `pkg> add --weak/extra Foo` veya `Pkg.add("Foo", target=:weakdeps/:extras)` biçimleriyle zayıf bağımlılıklar veya ekler olarak eklenebilir.

#### StyledStrings

  * Yeni bir stil yönetimi için daha kapsamlı ve yapılandırılmış bir şekilde kullanılacak standart bir kütüphane ([#49586](https://github.com/JuliaLang/julia/issues/49586)).
  * Yeni `Faces` yapısı, metin stil bilgileri için bir konteyner görevi görür (yazı tipi, renk ve süsleme gibi düşünün) ve stilize edilmiş içerik için kullanışlı, genişletilebilir (`addface!` aracılığıyla) ve özelleştirilebilir (`Faces.toml` ile kullanıcı ve `loadfaces!`) bir yaklaşım sunar. ([#49586](https://github.com/JuliaLang/julia/issues/49586))
  * Yeni `@styled_str` dize makrosu, çeşitli yüzler veya diğer nitelikler uygulayarak bir `AnnotatedString` oluşturmanın pratik bir yolunu sağlar ([#49586](https://github.com/JuliaLang/julia/issues/49586)).

#### Libdl

  * Yeni bir `LazyLibrary` türü, zincirleme tembel kütüphane yüklemeleri oluşturmak için `Libdl`'den dışa aktarılmıştır; bu, esasen JLL'ler içinde kullanılmak üzere tasarlanmıştır ([#50074](https://github.com/JuliaLang/julia/issues/50074)).

#### LinearAlgebra

  * `cbrt(::AbstractMatrix{<:Real})` artık tanımlandı ve gerçek değerli matrislerin küp köklerini döndürür ([#50661](https://github.com/JuliaLang/julia/issues/50661)).
  * `eigvals/eigen(A, bunchkaufman(B))` ve `eigvals/eigen(A, lu(B))`, sırasıyla `B`'nin Bunchkaufman (LDL) ve LU ayrıştırmasını kullanarak, artık `A` ve `B`'nin genel özdeğerlerini (`eigen`: ve özvektörlerini) verimli bir şekilde hesaplamaktadır. Not: İkinci argüman `bunchkaufman` veya `lu`'nun çıktısıdır ([#50471](https://github.com/JuliaLang/julia/issues/50471)).
  * Artık `eigvals/eigen(::Hermitian{<:Tridiagonal})` için özel bir dağıtım mevcut olup, bu bir benzerlik dönüşümü gerçekleştirerek gerçek simetrik bir tridiagonal matris oluşturur ve bunu LAPACK rutinlerini kullanarak çözer ([#49546](https://github.com/JuliaLang/julia/issues/49546)).
  * Yapılandırılmış matrisler artık ya ebeveynin eksenlerini ( `Simetrik` / `Hermitik` / `SoyutÜçgen` / `ÜstHessenberg` ) ya da bantlı matrislerin ana diyagonalinin eksenlerini korur. ([#52480](https://github.com/JuliaLang/julia/issues/52480))
  * `bunchkaufman` ve `bunchkaufman!` artık herhangi bir `AbstractFloat`, `Rational` ve bunların karmaşık varyantları için çalışıyor. `bunchkaufman` artık `Integer` türlerini destekliyor, bu da `Rational{BigInt}`'e içsel bir dönüşüm yaparak mümkün oluyor. Gerçek simetrik veya Hermit matrisinin `BunchKaufman` faktörizasyon nesnesi tarafından verilen diyagonal faktörün inersiyasını hesaplayan yeni `inertia` fonksiyonu eklendi. Karmaşık simetrik matrisler için `inertia`, yalnızca diyagonal faktörün sıfır özdeğerlerinin sayısını hesaplar ([#51487](https://github.com/JuliaLang/julia/issues/51487)).
  * Packages that specialize matrix-matrix `mul!` with a method signature of the form `mul!(::AbstractMatrix, ::MyMatrix, ::AbstractMatrix, ::Number, ::Number)` no longer encounter method ambiguities when interacting with `LinearAlgebra`. Previously, ambiguities used to arise when multiplying a `MyMatrix` with a structured matrix type provided by LinearAlgebra, such as `AbstractTriangular`, which used to necessitate additional methods to resolve such ambiguities. Similar sources of ambiguities have also been removed for matrix-vector `mul!` operations ([#52837](https://github.com/JuliaLang/julia/issues/52837)).
  * `lu` ve `issuccess(::LU)` artık `allowsingular` anahtar argümanını kabul ediyor. `true` olarak ayarlandığında, sıralı eksik U faktörü ile geçerli bir faktorizasyon başarı olarak kabul edilecek ve bir hata fırlatılmayacaktır. Bu tür faktorizasyonlar artık faktörlerin "sıralı eksik" notu ile birlikte yazdırılmasıyla gösterilmektedir; "Başarısız Faktorizasyon" mesajı yazdırılmak yerine ([#52957](https://github.com/JuliaLang/julia/issues/52957)).

#### Random

  * `rand` artık `Tuple` türleri üzerinde örnekleme yapmayı destekliyor ([#35856](https://github.com/JuliaLang/julia/issues/35856), [#50251](https://github.com/JuliaLang/julia/issues/50251)).
  * `rand` artık `Pair` türleri üzerinde örnekleme yapmayı destekliyor ([#28705](https://github.com/JuliaLang/julia/issues/28705)).
  * Negatif tam sayı tohumları artık `Random` tarafından sağlanan RNG'leri tohumlamak için kullanılabilir ([#51416](https://github.com/JuliaLang/julia/issues/51416)).
  * `Random` içindeki tohumlanabilir rastgele sayı üreteçleri artık bir dize ile tohumlanabilir, örneğin `seed!(rng, "rastgele bir tohum")` ([#51527](https://github.com/JuliaLang/julia/issues/51527)).

#### REPL

  * Tab tamamlama ipuçları artık repl'de yazarken daha açık bir metinle gösteriliyor. Devre dışı bırakmak için `Base.active_repl.options.hint_tab_completes = false` komutunu etkileşimli olarak veya startup.jl dosyasında ayarlayın:

    ```
    if VERSION >= v"1.11.0-0"
      atreplinit() do repl
          repl.options.hint_tab_completes = false
      end
    end
    ```

    ([#51229](https://github.com/JuliaLang/julia/issues/51229)).
  * Meta-M, boş bir istemle, önceki non-Main bağlamsal modül ile Main arasında bağlamsal modülü geçiştirir, böylece ileri geri geçiş yapmak basit hale gelir ([#51616](https://github.com/JuliaLang/julia/issues/51616), [#52670](https://github.com/JuliaLang/julia/issues/52670)).

#### Dates

Belgelendirilmemiş `adjust` fonksiyonu artık dışa aktarılmıyor ancak şimdi belgelenmiş durumda ([#53092](https://github.com/JuliaLang/julia/issues/53092)).

#### Statistics

  * İstatistik artık yükseltilebilir bir standart kütüphanedir ([#46501](https://github.com/JuliaLang/julia/issues/46501)).

#### Distributed

  * `pmap` artık varsayılan olarak bir `CachingPool` kullanıyor ([#33892](https://github.com/JuliaLang/julia/issues/33892)).

## Deprecated or removed

  * `Base.map`, `Iterators.map` ve `foreach` tek argümanlı yöntemlerini kaybetti ([#52631](https://github.com/JuliaLang/julia/issues/52631)).

## External dependencies

  * libuv kütüphanesi v1.44.2 sürümünden v1.48.0 sürümüne güncellenmiştir ([#49937](https://github.com/JuliaLang/julia/issues/49937)).
  * `tput` artık terminal yeteneklerini kontrol etmek için çağrılmıyor; bunun yerine saf-Julia terminfo ayrıştırıcısı ile değiştirilmiştir ([#50797](https://github.com/JuliaLang/julia/issues/50797)).
  * Terminal bilgi veritabanı, `terminfo`, artık varsayılan olarak satılmakta olup, sistemde `terminfo` mevcut olmadığında daha iyi bir REPL kullanıcı deneyimi sunmaktadır. Julia, veritabanını satmadan `Makefile` seçeneği `WITH_TERMINFO=0` kullanılarak derlenebilir. ([#55411](https://github.com/JuliaLang/julia/issues/55411))

## Tooling Improvements

  * CI artık tüm PR'lerde sınırlı otomatik yazım hatası tespiti yapmaktadır. Eğer bir PR'yi başarısız bir yazım hatası CI kontrolü ile birleştirirseniz, o dosyaları düzenleyen gelecekteki PR'lerde bildirilen yazım hataları otomatik olarak göz ardı edilecektir ([#51704](https://github.com/JuliaLang/julia/issues/51704)).
