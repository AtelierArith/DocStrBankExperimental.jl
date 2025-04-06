# [Package Images](@id pkgimages)

Julia paketi görüntüleri, Julia paketleri için nesne (yerel kod) önbellekleri sağlar. Bunlar, Julia'nın [system image](@ref dev-sysimg) ile benzerlik gösterir ve birçok aynı özelliği destekler. Aslında, temel serileştirme formatı aynıdır ve sistem görüntüsü, paket görüntülerinin inşa edildiği temel görüntüdür.

## High-level overview

Paket görüntüleri, hem kod hem de veri içeren paylaşılan kütüphanelerdir. `.ji` önbellek dosyaları gibi, her paket için üretilirler. Veri bölümü, paketteki küresel verileri (paketteki küresel değişkenler) ve paketin tanımladığı yöntemler ve türler hakkında gerekli meta verileri içerir. Kod bölümü, Julia'nın LLVM tabanlı derleyicisinin nihai çıktısını önbelleğe alan yerel nesneleri içerir.

Komut satırı seçeneği `--pkgimages=no`, bu oturum için nesne önbelleğini kapatmak için kullanılabilir. Bunun, önbellek dosyalarının muhtemelen yeniden oluşturulması gerektiği anlamına geldiğini unutmayın. Varsayılan olarak Julia'nın önbelleğe aldığı varyantların üst sınırı için [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@ref JULIA_MAX_NUM_PRECOMPILE_FILES)'e bakın.

!!! note
    Paket görüntüleri yerel paylaşımlı kütüphaneler olarak kendilerini sunarken, bunlar yalnızca bir yaklaşımıdır. Yerel bir programdan bunlara bağlanamazsınız ve bunlar Julia'dan yüklenmelidir.


## Linking

Paket görüntüleri yerel kod içerdiğinden, bunları kullanmadan önce üzerinde bir bağlayıcı çalıştırmamız gerekir. Paket görüntüsü bağlama sürecini ayrıntılı hale getirmek için ortam değişkenini [`JULIA_VERBOSE_LINKING`](@ref JULIA_VERBOSE_LINKING) değerine `true` olarak ayarlayabilirsiniz.

Ayrıca, kullanıcının çalışır bir sistem bağlayıcısının yüklü olduğunu varsayamayız. Bu nedenle, Julia, kutudan çıktığı gibi çalışan bir deneyim sağlamak için LLVM bağlayıcısı LLD ile birlikte gelir. `base/linking.jl` dosyasında, tüm desteklenen platformlarda paket görüntülerini bağlayabilmek için sınırlı bir arayüz uyguluyoruz.

### Quirks

LLD çoklu platform bağlantı aracı olmasına rağmen, platformlar arasında tutarlı bir arayüz sunmamaktadır. Ayrıca, `clang` veya başka bir derleyici sürücüsünden kullanılmak üzere tasarlanmıştır, bu nedenle `llvm-project/clang/lib/Driver/ToolChains`'dan bazı mantıkları yeniden uyguluyoruz. Neyse ki, `lld -flavor` kullanarak lld'yi doğru platforma ayarlamak mümkündür.

#### Windows

`link.exe` ile uğraşmamak için `-flavor gnu` kullanıyoruz, bu da `lld`'yi mingw32 ortamından bir çapraz bağlayıcıya dönüştürüyor. Windows DLL'lerinin bir `_DllMainCRTStartup` fonksiyonu içermesi gerekmektedir ve mingw32 kütüphanelerine olan bağımlılığımızı en aza indirmek için bir stub tanımını kendimiz enjekte ediyoruz.

#### MacOS

macOS'ta dinamik kütüphaneler `-lSystem` ile bağlantı kurmalıdır. Son macOS sürümlerinde, `-lSystem` yalnızca Xcode mevcut olduğunda bağlantı için kullanılabilir. Bu nedenle `-undefined dynamic_lookup` ile bağlantı kuruyoruz.

## [Package images optimized for multiple microarchitectures](@id pkgimgs-multi-versioning)

[multi-versioning](@ref sysimg-multi-versioning) sistem görüntüleri için benzer şekilde, paket görüntüleri çoklu sürümlemeyi destekler. Eğer birleşik bir önbellekle heterojen bir ortamda iseniz, nesne önbelleklerini çoklu sürümlemek için `JULIA_CPU_TARGET=generic` ortam değişkenini ayarlayabilirsiniz.

## Flags that impact package image creation and selection

Bu, önbellek seçimini etkileyen Julia komut satırı bayraklarıdır. Farklı bayraklarla oluşturulan paket görüntüleri reddedilecektir.

  * `-g`, `--debug-info`: Tam kesin eşleşme gereklidir çünkü kod üretimini değiştirir.
  * `--check-bounds`: Tam eşleşme gereklidir çünkü kod üretimini değiştirir.
  * `--inline`: Tam eşleşme gereklidir çünkü kod üretimini değiştirir.
  * `--pkgimages`: Nesne önbellekleme etkin olmadan çalışmaya izin vermek için.
  * `-O`, `--optimize`: Daha düşük optimizasyon seviyesinde üretilen paket görüntülerini reddedin, ancak daha yüksek optimizasyon seviyelerinin yüklenmesine izin verin.
