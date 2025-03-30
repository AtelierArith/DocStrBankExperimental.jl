# Fixing precompilation hangs due to open tasks or IO

Julia 1.10 veya daha yüksek bir sürümde, aşağıdaki mesajı görebilirsiniz:

![Ön derleme takılması ekran görüntüsü](./img/precompilation_hang.png)

Bu tekrar edebilir. Eğer kendiliğinden çözülme belirtileri olmadan devam ederse, "ön derleme takılması" yaşıyor olabilirsiniz ve bu durumun düzeltilmesi gerekebilir. Geçici olsa bile, kullanıcıların bu uyarıdan rahatsız olmaması için bunu çözmeyi tercih edebilirsiniz. Bu sayfa, bu tür sorunları nasıl analiz edeceğinizi ve düzelteceğinizi anlatmaktadır.

Eğer tavsiyeyi takip eder ve `Ctrl-C` tuşlarına basarsanız, görebilirsiniz

```
^C Interrupted: Exiting precompilation...

  1 dependency had warnings during precompilation:
┌ Test1 [ac89d554-e2ba-40bc-bc5c-de68b658c982]
│  [pid 2745] waiting for IO to finish:
│   Handle type        uv_handle_t->data
│   timer              0x55580decd1e0->0x7f94c3a4c340
```

Bu mesaj iki ana bilgi taşımaktadır:

  * `Test1`'in ön derlemesi sırasında bir takılma meydana geliyor, bu da `Test2`'nin (yüklemeye çalıştığımız paket) bir bağımlılığıdır.
  * `Test1` öncesi derleme sırasında, Julia bir `Timer` nesnesi oluşturdu (Eğer Timer'lar hakkında bilginiz yoksa `?Timer` komutunu kullanabilirsiniz) ve bu hala açık; bu kapanana kadar işlem takılı kalır.

Eğer bu, `timer = Timer(args...)`'ın nasıl oluşturulduğunu anlamanız için yeterli bir ipucuysa, iyi bir çözüm, `timer` sonunda kendi başına bitiyorsa `wait(timer)` eklemek veya zorla kapatmanız gerekiyorsa `close(timer)` eklemektir; bu, modülün sonundaki `end`den önce yapılmalıdır.

Ancak, bu durumların her zaman o kadar basit olmayabileceği durumlar vardır. Genellikle en iyi seçenek, takılmanın Test1'deki koddan mı yoksa Test1'in bağımlılıklarından birinden mi kaynaklandığını belirlemeye başlamak olacaktır:

  * Seçenek 1: `Pkg.add("Aqua")` ve [`Aqua.test_persistent_tasks`](https://juliatesting.github.io/Aqua.jl/dev/#Aqua.test_persistent_tasks-Tuple{Base.PkgId}) kullanın. Bu, soruna neden olan paketi tanımlamanıza yardımcı olmalıdır, ardından [below](@ref pchang_fix) talimatları izlenmelidir. Gerekirse, `PkgId`'yi `Base.PkgId(UUID("..."), "Test1")` olarak oluşturabilirsiniz; burada `...`, `Test1/Project.toml` dosyasındaki `uuid` girişinden gelir.
  * Seçenek 2: takılmanın kaynağını manuel olarak teşhis et.

Manuel teşhis koymak için:

1. `Pkg.geliştir("Test1")`
2. Comment out all the code `include`d or defined in `Test1`, *except* the `using/import` statements.
3. `Test2` kullanmayı (veya `Test1` kullanmayı, bunun da takılacağını varsayarak) tekrar deneyin.

Şimdi bir yol ayrımına geldik: ya

  * askı devam ediyor, bu da [due to one of your dependencies](@ref pchang_deps) olduğunu gösteriyor.
  * askı kaybolur, bu da [due to something in your code](@ref pchang_fix) olduğunu gösterir.

## [Diagnosing and fixing hangs due to a package dependency](@id pchang_deps)

Yarıçaplı bir arama kullanarak sorunlu bağımlılığı belirleyin: bağımlılıklarınızın yarısını yorum satırı haline getirerek başlayın, ardından hangi yarının sorumlu olduğunu izole ettiğinizde, o yarının yarısını yorum satırı haline getirin, vb. (Projeden kaldırmanıza gerek yok, sadece `using`/`import` ifadelerini yorum satırı haline getirin.)

Bir şüpheliyi tanımladıktan sonra (burada `SorunaNedenOlduğunuDüşündüğünüzPaket` olarak adlandıralım), önce o paketi ön derlemeyi deneyin. Eğer ön derleme sırasında da takılıyorsa, sorunu geriye doğru araştırmaya devam edin.

Ancak, muhtemelen `ThePackageYouThinkIsCausingTheProblem` sorunu oluşturduğunu düşündüğünüz paketin ön derlemesini düzgün bir şekilde yapacaktır. Bu, `ThePackageYouThinkIsCausingTheProblem.__init__` fonksiyonunda bir sorun olduğunu gösteriyor; bu fonksiyon `ThePackageYouThinkIsCausingTheProblem`'ın ön derlemesi sırasında çalışmaz, ancak `ThePackageYouThinkIsCausingTheProblem`'ı yükleyen herhangi bir paket içinde *çalışır*. Bu teoriyi test etmek için, minimal bir çalışma örneği (MWE) oluşturun, şöyle bir şey:

```julia
(@v1.10) pkg> generate MWE
  Generating  project MWE:
    MWE\Project.toml
    MWE\src\MWE.jl
```

`MWE.jl` kaynak kodu nerede?

```julia
module MWE
using ThePackageYouThinkIsCausingTheProblem
end
```

ve `ThePackageYouThinkIsCausingTheProblem`'ı MWE'nin bağımlılıklarına eklediniz.

Eğer bu MWE takılmayı yeniden üretiyorsa, suçluyu buldunuz: `ThePackageYouThinkIsCausingTheProblem.__init__` `Timer` nesnesini oluşturuyor olmalı. Eğer zamanlayıcı nesnesi güvenli bir şekilde `close` edilebiliyorsa, bu iyi bir seçenek. Aksi takdirde, en yaygın çözüm, *herhangi bir* paketin önceden derlenirken zamanlayıcı oluşturmaktan kaçınmaktır: ekleyin

```julia
ccall(:jl_generating_output, Cint, ()) == 1 && return nothing
```

`ThePackageYouThinkIsCausingTheProblem.__init__`'in ilk satırı olarak, paketleri ön derlemek amacıyla olan herhangi bir Julia işleminde herhangi bir başlatma yapmaktan kaçınacaktır.

## [Fixing package code to avoid hangs](@id pchang_fix)

Paketinizi önerici kelimeler için arayın (burada "Zamanlayıcı" gibi) ve sorunun nerede yaratıldığını belirlemeye çalışın. Bir yöntem *tanımı* gibi

```julia
maketimer() = Timer(timer -> println("hi"), 0; interval=1)
```

kendisi başlı başına sorunlu değildir: yalnızca `maketimer` modül tanımlanırken çağrılırsa bu soruna neden olabilir. Bu, üst düzey bir ifade gibi bir durumdan kaynaklanıyor olabilir.

```julia
const GLOBAL_TIMER = maketimer()
```

veya [precompile workload](https://github.com/JuliaLang/PrecompileTools.jl) şeklinde gerçekleşebilir.

Eğer neden olan satırları tanımlamakta zorlanıyorsanız, o zaman ikili arama yapmayı düşünün: paketinizin bölümlerini yorum satırı haline getirin (veya tüm dosyaları hariç tutmak için `include` satırları ekleyin) ta ki sorunu kapsamını azaltana kadar.
