# Profiling

`Profile` modülü, geliştiricilerin kodlarının performansını artırmalarına yardımcı olacak araçlar sağlar. Kullanıldığında, çalışan kod üzerinde ölçümler alır ve bireysel satırlarda ne kadar zaman harcandığını anlamanıza yardımcı olan çıktılar üretir. En yaygın kullanım, optimizasyon hedefleri olarak "darboğazları" tanımlamaktır.

`Profil` olarak bilinen bir "örnekleme" veya [statistical profiler](https://en.wikipedia.org/wiki/Profiling_(computer_programming)) uygular. Herhangi bir görevin yürütülmesi sırasında periyodik olarak bir geri izleme alarak çalışır. Her geri izleme, o anda çalışan işlevi ve satır numarasını, ayrıca bu satıra ulaşan işlev çağrılarının tam zincirini yakalar ve dolayısıyla yürütmenin mevcut durumunun bir "anlık görüntüsü"dür.

Eğer çalıştırma sürenizin büyük bir kısmı belirli bir kod satırını yürütmekle geçiyorsa, bu satır tüm geri izleme setinde sıkça görünecektir. Diğer bir deyişle, belirli bir satırın "maliyeti" - ya da aslında bu satıra kadar ve bu satırı da içeren fonksiyon çağrıları dizisinin maliyeti - tüm geri izleme setinde ne sıklıkla göründüğü ile orantılıdır.

Bir örnekleme profilleyici, tam satır satır kapsama sağlamaz, çünkü geri izlemeler belirli aralıklarla gerçekleşir (varsayılan olarak, Unix sistemlerinde 1 ms ve Windows'ta 10 ms, ancak gerçek zamanlama işletim sistemi yüküne bağlıdır). Ayrıca, aşağıda daha fazla tartışıldığı gibi, örnekler tüm yürütme noktalarının seyrek bir alt kümesinde toplandığı için, bir örnekleme profilleyicisi tarafından toplanan veriler istatistiksel gürültüye tabidir.

Bu sınırlamalara rağmen, örnekleme profilleyicilerinin önemli güçlü yönleri vardır:

  * Kodunuzda zaman ölçümleri almak için herhangi bir değişiklik yapmanıza gerek yoktur.
  * Julia'nın temel koduna ve hatta (isteğe bağlı olarak) C ve Fortran kütüphanelerine profil çıkarabilir.
  * "nadir" çalıştırarak çok az bir performans aşımı vardır; profil alırken, kodunuz neredeyse yerel hızda çalışabilir.

Bu nedenlerden ötürü, herhangi bir alternatif düşünmeden önce yerleşik örnekleme profilini kullanmayı denemeniz önerilir.

## Basic usage

Tabii, basit bir test durumu ile çalışalım:

```julia-repl
julia> function myfunc()
           A = rand(200, 200, 400)
           maximum(A)
       end
```

Profiling yapmayı düşündüğünüz kodu en az bir kez çalıştırmak iyi bir fikirdir (Julia'nın JIT derleyicisini profil etmek istemiyorsanız):

```julia-repl
julia> myfunc() # run once to force compilation
```

Artık bu fonksiyonu profil çıkarmaya hazırız:

```julia-repl
julia> using Profile

julia> @profile myfunc()
```

Profiling sonuçlarını görmek için birkaç grafik tarayıcı vardır. Bir "aile" görselleştiricisi [FlameGraphs.jl](https://github.com/timholy/FlameGraphs.jl) üzerine kuruludur ve her aile üyesi farklı bir kullanıcı arayüzü sunar:

  * [VS Code](https://www.julia-vscode.org/) tam profil görselleştirme için yerleşik destek ile tam bir IDE'dir.
  * [ProfileView.jl](https://github.com/timholy/ProfileView.jl) GTK tabanlı bağımsız bir görselleştiricidir.
  * [ProfileVega.jl](https://github.com/davidanthoff/ProfileVega.jl) VegaLight kullanır ve Jupyter defterleriyle iyi bir şekilde entegre olur.
  * [StatProfilerHTML.jl](https://github.com/tkluck/StatProfilerHTML.jl) HTML üretir ve bazı ek özetler sunar, ayrıca Jupyter defterleriyle de iyi bir şekilde entegre olur.
  * [ProfileSVG.jl](https://github.com/timholy/ProfileSVG.jl) SVG'yi render eder.
  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl) grafikler, alev grafikleri ve daha fazlasını incelemek için yerel bir web sitesi sunar.
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl) bir HTML canvas tabanlı profil görüntüleyici UI'dır, [Julia VS Code extension](https://www.julia-vscode.org/) tarafından kullanılmaktadır, ancak etkileşimli HTML dosyaları da oluşturabilir.

Tamamen bağımsız bir profil görselleştirme yaklaşımı [PProf.jl](https://github.com/vchuravy/PProf.jl) olup, harici `pprof` aracını kullanmaktadır.

Burada, standart kütüphaneyle birlikte gelen metin tabanlı görüntüleme yöntemini kullanacağız:

```julia-repl
julia> Profile.print()
80 ./event.jl:73; (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
 80 ./REPL.jl:97; macro expansion
  80 ./REPL.jl:66; eval_user_input(::Any, ::Base.REPL.REPLBackend)
   80 ./boot.jl:235; eval(::Module, ::Any)
    80 ./<missing>:?; anonymous
     80 ./profile.jl:23; macro expansion
      52 ./REPL[1]:2; myfunc()
       38 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type{B...
        38 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr{F...
       14 ./random.jl:278; rand
        14 ./random.jl:277; rand
         14 ./random.jl:366; rand
          14 ./random.jl:369; rand
      28 ./REPL[1]:3; myfunc()
       28 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinear,...
        3  ./reduce.jl:426; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
        25 ./reduce.jl:428; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
```

Herhangi bir satır, kodda belirli bir yeri (satır numarası) temsil eder. Girinti, işlev çağrılarının iç içe geçmiş sırasını göstermek için kullanılır; daha fazla girintili satırlar, çağrıların sırasının daha derininde yer alır. Her satırda, ilk "alan" bu satırda veya bu satır tarafından yürütülen herhangi bir işlevde alınan geri izleme (örnek) sayısını gösterir. İkinci alan dosya adı ve satır numarası, üçüncü alan ise işlev adıdır. Belirli satır numaralarının, Julia'nın kodu değiştikçe değişebileceğini unutmayın; bu örneği takip etmek istiyorsanız, en iyisi bu örneği kendiniz çalıştırmaktır.

Bu örnekte, en üst düzey işlevin `event.jl` dosyasında olduğunu görebiliriz. Bu, Julia'yı başlattığınızda REPL'yi çalıştıran işlevdir. `REPL.jl` dosyasının 97. satırını incelediğinizde, `eval_user_input()` işlevinin çağrıldığı yeri göreceksiniz. Bu, REPL'de yazdığınız şeyleri değerlendiren işlevdir ve etkileşimli çalıştığımız için bu işlevler `@profile myfunc()` girdiğimizde çağrıldı. Bir sonraki satır, [`@profile`](@ref) makrosunda gerçekleştirilen eylemleri yansıtır.

İlk satır, `event.jl` dosyasının 73. satırında 80 geri izleme alındığını gösteriyor, ancak bu satırın kendi başına "pahalı" olduğu anlamına gelmiyor: üçüncü satır, bu 80 geri izlemenin aslında `eval_user_input` çağrısı içinde tetiklendiğini ortaya koyuyor ve bu şekilde devam ediyor. Gerçekten zaman alan işlemleri bulmak için çağrı zincirine daha derinlemesine bakmamız gerekiyor.

Bu çıktıda "önemli" olan ilk satır şudur:

```
52 ./REPL[1]:2; myfunc()
```

`REPL`, tanımının `myfunc`'ı REPL'de tanımladığımızı, bir dosyaya koymak yerine; eğer bir dosya kullanmış olsaydık, bu dosya adını gösterirdi. `[1]`, `myfunc` fonksiyonunun bu REPL oturumunda değerlendirilen ilk ifade olduğunu gösterir. `myfunc()`'ın 2. satırında `rand` çağrısı bulunmaktadır ve bu satırda 52 (80'den) geri izleme gerçekleşmiştir. Bunun altında, `dSFMT.jl` içinde `dsfmt_fill_array_close_open!` çağrısını görebilirsiniz.

Biraz daha aşağıda, şunu görüyorsunuz:

```
28 ./REPL[1]:3; myfunc()
```

`myfunc`'in 3. satırında `maximum` çağrısı bulunmaktadır ve burada 80'den 28 (28) geri izleme alınmıştır. Bunun altında, bu tür girdi verileri için `maximum` fonksiyonundaki zaman alıcı işlemleri gerçekleştiren `base/reduce.jl` içindeki belirli yerleri görebilirsiniz.

Genel olarak, rastgele sayıların üretilmesinin maksimum elemanı bulmaktan yaklaşık iki kat daha pahalı olduğunu kısmen sonuçlandırabiliriz. Bu sonuca olan güvenimizi artırmak için daha fazla örnek toplayabiliriz:

```julia-repl
julia> @profile (for i = 1:100; myfunc(); end)

julia> Profile.print()
[....]
 3821 ./REPL[1]:2; myfunc()
  3511 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type...
   3511 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr...
  310  ./random.jl:278; rand
   [....]
 2893 ./REPL[1]:3; myfunc()
  2893 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinea...
   [....]
```

Genel olarak, bir çizgide toplanmış `N` örneğiniz varsa, diğer gürültü kaynakları (örneğin, bilgisayarın diğer görevlerle meşgul olması gibi) hariç, `sqrt(N)` mertebesinde bir belirsizlik bekleyebilirsiniz. Bu kuralın en büyük istisnası, nadiren çalışan ancak oldukça maliyetli olma eğiliminde olan çöp toplama işlevidir. (Julia'nın çöp toplayıcısı C dilinde yazıldığı için, bu tür olaylar aşağıda açıklanan `C=true` çıktı modu kullanılarak veya [ProfileView.jl](https://github.com/timholy/ProfileView.jl) kullanılarak tespit edilebilir.)

Bu, varsayılan "ağaç" dökümünü gösterir; alternatif olarak, iç içe geçmelerinden bağımsız olarak sayıları biriktiren "düz" döküm vardır:

```julia-repl
julia> Profile.print(format=:flat)
 Count File          Line Function
  6714 ./<missing>     -1 anonymous
  6714 ./REPL.jl       66 eval_user_input(::Any, ::Base.REPL.REPLBackend)
  6714 ./REPL.jl       97 macro expansion
  3821 ./REPL[1]        2 myfunc()
  2893 ./REPL[1]        3 myfunc()
  6714 ./REPL[7]        1 macro expansion
  6714 ./boot.jl      235 eval(::Module, ::Any)
  3511 ./dSFMT.jl      84 dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_s...
  6714 ./event.jl      73 (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
  6714 ./profile.jl    23 macro expansion
  3511 ./random.jl    431 rand!(::MersenneTwister, ::Array{Float64,3}, ::In...
   310 ./random.jl    277 rand
   310 ./random.jl    278 rand
   310 ./random.jl    366 rand
   310 ./random.jl    369 rand
  2893 ./reduce.jl    270 _mapreduce(::Base.#identity, ::Base.#scalarmax, :...
     5 ./reduce.jl    420 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
   253 ./reduce.jl    426 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
  2592 ./reduce.jl    428 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
    43 ./reduce.jl    429 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
```

Eğer kodunuzda özyineleme (recursion) varsa, potansiyel olarak kafa karıştırıcı bir nokta, bir "çocuk" fonksiyondaki bir satırın toplam geri izleme (backtrace) sayısından daha fazla sayım (count) biriktirebileceğidir. Aşağıdaki fonksiyon tanımlarını düşünün:

```julia
dumbsum(n::Integer) = n == 1 ? 1 : 1 + dumbsum(n-1)
dumbsum3() = dumbsum(3)
```

Eğer `dumbsum3`'ü profil çıkartacak olsaydınız ve `dumbsum(1)` çalışırken bir geri izleme almış olsaydınız, geri izleme şu şekilde görünürdü:

```julia
dumbsum3
    dumbsum(3)
        dumbsum(2)
            dumbsum(1)
```

Sonuç olarak, bu çocuk fonksiyonu 3 sayım alır, oysa ebeveyn yalnızca bir alır. "Ağaç" temsili bunu çok daha net hale getirir ve bu nedenle (başka nedenlerin yanı sıra) sonuçları görmenin muhtemelen en yararlı yoludur.

## Accumulation and clearing

[`@profile`](@ref) bir tamponda birikir; eğer `4d61726b646f776e2e436f64652822222c20224070726f66696c652229_40726566` altında birden fazla kod parçası çalıştırırsanız, [`Profile.print()`](@ref) size birleştirilmiş sonuçları gösterecektir. Bu çok faydalı olabilir, ancak bazen taze bir başlangıç yapmak istersiniz; bunu [`Profile.clear()`](@ref) ile yapabilirsiniz.

## Options for controlling the display of profile results

[`Profile.print`](@ref) daha önce tanımladığımızdan daha fazla seçeneğe sahiptir. Tam beyanı görelim:

```julia
function print(io::IO = stdout, data = fetch(); kwargs...)
```

Öncelikle iki konum argümanını, daha sonra anahtar kelime argümanlarını tartışalım:

  * `io` – Sonuçları bir tamponda, örneğin bir dosyada kaydetmenizi sağlar, ancak varsayılan olarak `stdout`'a (konsola) yazdırır.
  * `data` – Analiz etmek istediğiniz verileri içerir; varsayılan olarak bu, [`Profile.fetch()`](@ref)'dan elde edilir, bu da önceden tahsis edilmiş bir tamponun geri izlerini çeker. Örneğin, profili profillemek istiyorsanız, şöyle diyebilirsiniz:

    ```julia
    data = copy(Profile.fetch())
    Profile.clear()
    @profile Profile.print(stdout, data) # Prints the previous results
    Profile.print()                      # Prints results from Profile.print()
    ```

Anahtar kelime argümanları herhangi bir kombinasyon olabilir:

  * `format` – Yukarıda tanıtıldığı gibi, geri izlerin ağaç yapısını gösteren (varsayılan, `:tree`) veya göstermeyen (`:flat`) girinti ile yazılıp yazılmayacağını belirler.
  * `C` – Eğer `true` ise, C ve Fortran kodlarından geri izler gösterilir (normalde hariç tutulurlar). `Profile.print(C = true)` ile tanıtım örneğini çalıştırmayı deneyin. Bu, bir darboğazın Julia kodundan mı yoksa C kodundan mı kaynaklandığını belirlemede son derece yardımcı olabilir; `C = true` ayarı ayrıca daha uzun profil dökümleri pahasına iç içe geçmenin yorumlanabilirliğini artırır.
  * `combine` – Bazı kod satırları birden fazla işlem içerir; örneğin, `s += A[i]` hem bir dizi referansı (`A[i]`) hem de bir toplama işlemi içerir. Bunlar, üretilen makine kodunda farklı satırlara karşılık gelir ve bu nedenle bu satırda geri izleme sırasında yakalanan iki veya daha fazla farklı adres olabilir. `combine = true` bunları bir araya getirir ve muhtemelen genellikle istediğiniz şeydir, ancak her benzersiz talimat işaretçisi için ayrı bir çıktı oluşturmak isterseniz `combine = false` kullanabilirsiniz.
  * `maxdepth` – `:tree` formatında `maxdepth`'ten daha yüksek bir derinlikteki çerçeveleri sınırlar.
  * `sortedby` – `:flat` formatında sıralama düzenini kontrol eder. `:filefuncline` (varsayılan) kaynak satırına göre sıralarken, `:count` toplanan örnek sayısına göre sıralar.
  * `noisefloor` – Örneklerin sezgisel gürültü tabanının altında kalan çerçeveleri sınırlar (yalnızca `:tree` formatına uygulanır). Bunun için denemek üzere önerilen bir değer 2.0'dır (varsayılan 0'dır). Bu parametre, `n <= noisefloor * √N` olan örnekleri gizler; burada `n`, bu satırdaki örnek sayısını ve `N`, çağrılan için örnek sayısını temsil eder.
  * `mincount` – `mincount` sayısıdan az tekrar eden çerçeveleri sınırlar.

File/function names are sometimes truncated (with `...`), and indentation is truncated with a `+n` at the beginning, where `n` is the number of extra spaces that would have been inserted, had there been room. If you want a complete profile of deeply-nested code, often a good idea is to save to a file using a wide `displaysize` in an [`IOContext`](@ref):

```julia
open("/tmp/prof.txt", "w") do s
    Profile.print(IOContext(s, :displaysize => (24, 500)))
end
```

## Configuration

[`@profile`](@ref) sadece geri izleri toplar ve analiz, [`Profile.print()`](@ref) çağrıldığında gerçekleşir. Uzun süreli bir hesaplama için, geri izleri depolamak için önceden tahsis edilmiş tamponun dolması tamamen mümkündür. Eğer bu olursa, geri izler durur ama hesaplamanız devam eder. Sonuç olarak, bazı önemli profil verilerini kaçırabilirsiniz (bu olduğunda bir uyarı alırsınız).

Bu şekilde ilgili parametreleri elde edebilir ve yapılandırabilirsiniz:

```julia
Profile.init() # returns the current settings
Profile.init(n = 10^7, delay = 0.01)
```

`n`, toplam saklayabileceğiniz talimat işaretleyicilerinin sayısını ifade eder ve varsayılan değeri `10^6`'dır. Eğer tipik bir geri izleme 20 talimat işaretleyicisi ise, 50000 geri izleme toplayabilirsiniz ki bu da %1'den daha az bir istatistiksel belirsizlik önerir. Bu, çoğu uygulama için yeterli olabilir.

Sonuç olarak, Julia'nın istenen hesaplamaları gerçekleştirmek için anlık görüntüler arasında geçen süreyi ayarlayan `delay`'i, saniye cinsinden, değiştirmeniz daha olasıdır. Çok uzun süren bir iş, sık sık geri izlemelere ihtiyaç duymayabilir. Varsayılan ayar `delay = 0.001`'dir. Elbette, gecikmeyi azaltabileceğiniz gibi artırabilirsiniz; ancak, gecikme, bir geri izleme almak için gereken süreye (~30 mikro saniye yazarın dizüstü bilgisayarında) benzer hale geldiğinde profil oluşturmanın ek yükü artar.

## Memory allocation analysis

Performansı artırmanın en yaygın tekniklerinden biri bellek tahsisini azaltmaktır. Julia, bunu ölçmek için birkaç araç sunar:

### `@time`

Ayrılmanın toplam miktarı [`@time`](@ref), [`@allocated`](@ref) ve [`@allocations`](@ref) ile ölçülebilir ve ayrılmaya neden olan belirli satırlar, bu satırların neden olduğu bellek temizleme maliyeti aracılığıyla profil oluşturma ile sıklıkla çıkarılabilir. Ancak bazen, her bir kod satırının ayırdığı bellek miktarını doğrudan ölçmek daha verimli olabilir.

### GC Logging

[`@time`](@ref) ifadesi, bir ifadenin değerlendirilmesi süresince bellek kullanımı ve çöp toplama hakkında yüksek düzeyde istatistikler kaydederken, çöp toplayıcının ne sıklıkla çalıştığını, her seferinde ne kadar süre çalıştığını ve her seferinde ne kadar çöp topladığını anlamak için her çöp toplama olayını kaydetmek faydalı olabilir. Bu, [`GC.enable_logging(true)`](@ref) ile etkinleştirilebilir; bu, Julia'nın her çöp toplama gerçekleştiğinde stderr'ye kaydetmesini sağlar.

### [Allocation Profiler](@id allocation-profiler)

!!! compat "Julia 1.8"
    Bu işlevsellik en az Julia 1.8 gerektirir.


Ayrım profili, çalışırken her bir ayrımın yığın izini, türünü ve boyutunu kaydeder. [`Profile.Allocs.@profile`](@ref) ile çağrılabilir.

Bu tahsisatlarla ilgili bilgiler, `Alloc` nesnelerinin bir dizisi olarak, bir `AllocResults` nesnesi içinde döndürülmektedir. Bunları görselleştirmenin en iyi yolu şu anda [PProf.jl](https://github.com/JuliaPerf/PProf.jl) ve [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl) paketleridir; bu paketler, en fazla tahsisat yapan çağrı yığınlarını görselleştirebilir.

Ayrım profili önemli bir yük getirmektedir, bu nedenle bazı tahsisatları atlayarak hızlandırmak için bir `sample_rate` argümanı geçirilebilir. `sample_rate=1.0` geçmek her şeyi kaydedecek (bu yavaştır); `sample_rate=0.1` yalnızca tahsisatların %10'unu kaydedecek (daha hızlı) vb.

!!! compat "Julia 1.11"
    Eski Julia sürümleri, tüm durumlarda türleri yakalayamazdı. Eski Julia sürümlerinde, `Profile.Allocs.UnknownType` türünde bir tahsis görüyorsanız, bu, profilin hangi tür nesnenin tahsis edildiğini bilmediği anlamına gelir. Bu, esasen tahsisin derleyici tarafından üretilen oluşturulmuş koddan geldiği durumlarda meydana geldi. Daha fazla bilgi için [issue #43688](https://github.com/JuliaLang/julia/issues/43688) adresine bakın.

    Julia 1.11'den itibaren, tüm tahsislerin bir türü bildirilmelidir.


Bu aracı nasıl kullanacağınızla ilgili daha fazla bilgi için lütfen 2022 JuliaCon'dan aşağıdaki konuşmaya bakın: https://www.youtube.com/watch?v=BFvpwC8hEWQ

##### Allocation Profiler Example

Bu basit örnekte, alloc profilini görselleştirmek için PProf kullanıyoruz. Bunun yerine başka bir görselleştirme aracı da kullanabilirsiniz. Profili topluyoruz (bir örnekleme oranı belirterek), ardından bunu görselleştiriyoruz.

```julia
using Profile, PProf
Profile.Allocs.clear()
Profile.Allocs.@profile sample_rate=0.0001 my_function()
PProf.Allocs.pprof()
```

İşte örnekleme oranını nasıl ayarlayabileceğimizi gösteren daha derinlemesine bir örnek. Hedeflenmesi gereken iyi bir örnek sayısı yaklaşık 1 - 10 bin civarındadır. Çok fazla olursa, profil görselleştirici aşırı yüklenebilir ve profil oluşturma yavaşlayabilir. Çok az olursa, temsil edici bir örneğiniz olmaz.

```julia-repl
julia> import Profile

julia> @time my_function()  # Estimate allocations from a (second-run) of the function
  0.110018 seconds (1.50 M allocations: 58.725 MiB, 17.17% gc time)
500000

julia> Profile.Allocs.clear()

julia> Profile.Allocs.@profile sample_rate=0.001 begin   # 1.5 M * 0.001 = ~1.5K allocs.
           my_function()
       end
500000

julia> prof = Profile.Allocs.fetch();  # If you want, you can also manually inspect the results.

julia> length(prof.allocs)  # Confirm we have expected number of allocations.
1515

julia> using PProf  # Now, visualize with an external tool, like PProf or ProfileCanvas.

julia> PProf.Allocs.pprof(prof; from_c=false)  # You can optionally pass in a previously fetched profile result.
Analyzing 1515 allocation samples... 100%|████████████████████████████████| Time: 0:00:00
Main binary filename not available.
Serving web UI on http://localhost:62261
"alloc-profile.pb.gz"
```

Sonra profili http://localhost:62261 adresine giderek görüntüleyebilirsiniz ve profil diske kaydedilmiştir. Daha fazla seçenek için PProf paketine bakın.

##### Allocation Profiling Tips

Yukarıda belirtildiği gibi, profilinizde yaklaşık 1-10 bin örnek hedefleyin.

Not edin ki, *tüm tahsislerin* alanında eşit şekilde örnekleme yapıyoruz ve örneklerimizi tahsisin boyutuna göre ağırlıklandırmıyoruz. Bu nedenle, belirli bir tahsis profili, programınızdaki çoğu baytın nerede tahsis edildiğine dair temsilci bir profil vermeyebilir, eğer `sample_rate=1` ayarlamadıysanız.

Ayrımlar, kullanıcıların doğrudan nesneler oluşturmasından gelebilir, ancak aynı zamanda çalışma zamanından da gelebilir veya tür belirsizliğini ele almak için derlenmiş koda eklenebilir. "Kaynak kodu" görünümüne bakmak, bunları izole etmek için faydalı olabilir ve ardından [`Cthulhu.jl`](https://github.com/JuliaDebug/Cthulhu.jl) gibi diğer harici araçlar, ayrımın nedenini belirlemek için yararlı olabilir.

##### Allocation Profile Visualization Tools

Şu anda tümü Tahsis Profilleri görüntüleyebilen birkaç profil oluşturma görselleştirme aracı bulunmaktadır. Bildiğimiz bazı ana araçların küçük bir listesi:

  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl)
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl)
  * VSCode'un yerleşik profil görselleştiricisi (`@profview_allocs`) [belgeler gerekli]
  * REPL'de sonuçları doğrudan görüntüleme

      * Sonuçları [`Profile.Allocs.fetch()`](@ref) aracılığıyla REPL'de inceleyebilirsiniz; her tahsisin yığın izini ve türünü görüntülemek için.

#### Line-by-Line Allocation Tracking

Bir alternatif ölçüm yöntemi, Julia'yı `--track-allocation=<setting>` komut satırı seçeneği ile başlatmaktır; burada `none` (varsayılan, tahsisat ölçme), `user` (Julia'nın çekirdek kodu hariç her yerde bellek tahsisini ölçme) veya `all` (her Julia kodu satırında bellek tahsisini ölçme) seçeneklerinden birini seçebilirsiniz. Tahsisat, derlenmiş kodun her satırı için ölçülür. Julia'dan çıktığınızda, birikimli sonuçlar, kaynak dosyanın bulunduğu aynı dizinde, dosya adının sonuna `.mem` eklenmiş metin dosyalarına yazılır. Her satır, tahsis edilen toplam byte sayısını listeler. [`Coverage` package](https://github.com/JuliaCI/Coverage.jl) bazı temel analiz araçlarını içerir; örneğin, tahsis edilen byte sayısına göre satırları sıralamak için.

Sonuçları yorumlarken birkaç önemli detay vardır. `user` ayarında, REPL'den doğrudan çağrılan herhangi bir fonksiyonun ilk satırı, REPL kodunun kendisinde gerçekleşen olaylar nedeniyle tahsisat gösterecektir. Daha da önemlisi, JIT derlemesi de tahsisat sayımlarına eklenir, çünkü Julia'nın derleyicisinin çoğu Julia'da yazılmıştır (ve derleme genellikle bellek tahsisi gerektirir). Önerilen prosedür, analiz etmek istediğiniz tüm komutları çalıştırarak derlemeyi zorlamaktır, ardından tüm tahsisat sayaçlarını sıfırlamak için [`Profile.clear_malloc_data()`](@ref) komutunu çağırmaktır. Son olarak, istenen komutları çalıştırın ve `.mem` dosyalarının oluşturulmasını tetiklemek için Julia'dan çıkın.

!!! note
    `--track-allocation` kod üretimini tahsisatları kaydedecek şekilde değiştirir, bu nedenle tahsisatlar, seçenek olmadan gerçekleşenlerden farklı olabilir. Bunun yerine [allocation profiler](@ref allocation-profiler) kullanmanızı öneririz.


## External Profiling

Şu anda Julia, dış profil oluşturma araçları olarak `Intel VTune`, `OProfile` ve `perf`'i desteklemektedir.

Seçtiğiniz araca bağlı olarak, `Make.user` dosyasında `USE_INTEL_JITEVENTS`, `USE_OPROFILE_JITEVENTS` ve `USE_PERF_JITEVENTS` değerlerini 1 olarak ayarlayın. Birden fazla bayrak desteklenmektedir.

Julia'yı çalıştırmadan önce ortam değişkenini [`ENABLE_JITPROFILING`](@ref ENABLE_JITPROFILING) 1 olarak ayarlayın.

Artık bu araçları kullanmanın birçok yolu var! Örneğin, `OProfile` ile basit bir kayıt deneyebilirsiniz:

```
>ENABLE_JITPROFILING=1 sudo operf -Vdebug ./julia test/fastmath.jl
>opreport -l `which ./julia`
```

Veya `perf` ile benzer şekilde:

```
$ ENABLE_JITPROFILING=1 perf record -o /tmp/perf.data --call-graph dwarf -k 1 ./julia /test/fastmath.jl
$ perf inject --jit --input /tmp/perf.data --output /tmp/perf-jit.data
$ perf report --call-graph -G -i /tmp/perf-jit.data
```

Programınız hakkında ölçebileceğiniz daha birçok ilginç şey var. Kapsamlı bir liste için lütfen [Linux perf examples page](https://www.brendangregg.com/perf.html) adresini okuyun.

Herhangi bir yürütme için `perf.data` dosyasını kaydeden perf, küçük programlar için bile oldukça büyük hale gelebilir. Ayrıca perf LLVM modülü, `~/.debug/jit` içinde geçici olarak hata ayıklama nesneleri kaydeder, bu nedenle o klasörü sık sık temizlemeyi unutmayın.
