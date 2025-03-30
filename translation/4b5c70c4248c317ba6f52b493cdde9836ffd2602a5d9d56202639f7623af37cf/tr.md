# Garbage Collection in Julia

## Introduction

Julia, hareket etmeyen, kısmen eşzamanlı, paralel, nesil ve çoğunlukla kesin bir işaretleme-temizleme toplayıcısına sahiptir (C'den Julia'yı çağırmak isteyen kullanıcılar için muhafazakar yığın taraması arayüzü bir seçenek olarak sağlanmaktadır).

## Allocation

Julia, iki tür ayırıcı kullanır; ayırma isteğinin boyutu hangi türün kullanılacağını belirler. 2k bayta kadar olan nesneler, her bir iş parçacığı için serbest liste havuz ayırıcı üzerinde ayrılırken, 2k bayttan büyük nesneler libc malloc aracılığıyla ayrılır.

Julia'nın havuz ayırıcı, nesneleri farklı boyut sınıflarına ayırır, böylece havuz ayırıcı tarafından yönetilen bir bellek sayfası (64 bit platformlarda 4 işletim sistemi sayfasını kapsar) yalnızca aynı boyut sınıfına ait nesneleri içerir. Havuz ayırıcıdan gelen her bellek sayfası, per iş parçacığı kilitsiz listelerde saklanan bazı sayfa meta verileri ile eşleştirilir. Sayfa meta verileri, sayfanın hiç canlı nesne içerip içermediği, boş slot sayısı ve o sayfada bulunan boş listede ilk ve son nesnelere olan ofsetler gibi bilgileri içerir. Bu meta veriler, toplama aşamasını optimize etmek için kullanılır: hiç canlı nesne içermeyen bir sayfa, örneğin, tarama gerektirmeden işletim sistemine geri verilebilir.

Bir nesne içermeyen bir sayfa işletim sistemine geri dönebilir, ancak ona bağlı olan meta veriler kalıcı olarak tahsis edilir ve verilen sayfadan daha uzun sürebilir. Yukarıda belirtildiği gibi, tahsis edilmiş sayfalar için meta veriler, her bir iş parçacığı için kilitsiz listelerde saklanır. Ancak, boş sayfalar için meta veriler, sayfanın haritalandığı ancak hiç erişilmediği (`page_pool_clean`), sayfanın tembel bir şekilde süzüldüğü ve arka planda bir GC iş parçacığı tarafından madvise edilmesini beklediği (`page_pool_lazily_freed`), veya sayfanın madvise edildiği (`page_pool_freed`) durumuna bağlı olarak üç ayrı kilitsiz listede saklanabilir.

Julia'nın havuz ayırıcı, "katmanlı" bir ayırma disiplini izler. Havuz ayırıcı için bir bellek sayfası talep edildiğinde, Julia:

  * `page_pool_lazily_freed`'den bir sayfa talep etmeyi deneyin; bu, son durdurma-dünya aşamasında boş olan ancak henüz eşzamanlı bir temizleyici GC iş parçacığı tarafından madvise edilmemiş sayfaları içerir.
  * Eğer `page_pool_lazily_freed`'den bir sayfa talep etme işlemi başarısız olursa, daha önceki bir sayfa tahsis talebinde mmap edilen ancak hiç erişilmeyen sayfaları içeren `the page_pool_clean`'den bir sayfa talep etmeye çalışacaktır.
  * Eğer `pool_page_clean` ve `page_pool_lazily_freed`'den bir sayfa talep etme işlemi başarısız olursa, `page_pool_freed`'den bir sayfa talep etmeyi deneyecektir. Bu havuz, zaten eşzamanlı bir temizleyici GC iş parçacığı tarafından madvise edilmiş ve temel sanal adresi geri dönüştürülebilen sayfaları içerir.
  * Eğer yukarıda belirtilen tüm denemelerde başarısız olursa, bir grup sayfayı mmap yapacak, kendisi için bir sayfa alacak ve kalan sayfaları `page_pool_clean` içine ekleyecektir.

![Katmanlı havuz tahsisi diyagramı](./img/gc-tiered-allocation.jpg)

## Marking and Generational Collection

Julia'nın işaretleme aşaması, nesne grafi üzerinde paralel bir yinelemeli derinlik öncelikli arama ile uygulanır. Julia'nın toplayıcısı taşınmaz, bu nedenle nesne yaş bilgisi yalnızca nesnenin bulunduğu bellek bölgesi aracılığıyla belirlenemez, ancak bir şekilde nesne başlığında veya yan bir tabloda kodlanması gerekir. Bir nesnenin başlığının en düşük iki biti, sırasıyla, işaretleme aşamasında bir nesne tarandığında ayarlanan bir işaret bitini ve jenerasyonel toplama için bir yaş bitini depolamak için kullanılır.

Nesil toplama, yapışkan bitler aracılığıyla uygulanır: nesneler yalnızca işaret yığınına itilir ve bu nedenle izlenir, eğer işaret bitleri ayarlanmamışsa. Nesneler en eski nesil seviyesine ulaştığında, "hızlı süpürme" sırasında işaret bitleri sıfırlanmaz, bu da bu nesnelerin sonraki işaret aşamasında izlenmemesine yol açar. Ancak, "tam süpürme" tüm nesnelerin işaret bitlerinin sıfırlanmasına neden olur ve bu da tüm nesnelerin sonraki işaret aşamasında izlenmesine yol açar. Nesneler, her hayatta kalma süpürme aşamasında bir sonraki nesile terfi ettirilir. Mutatör tarafında, alan yazmaları, nesne son nesildeyse ve yazılan alandaki nesne değilse, bir nesnenin adresini her iş parçacığı için hatırlanan bir sete iten bir yazma engeli aracılığıyla kesilir. Bu hatırlanan setteki nesneler daha sonra işaret aşamasında izlenir.

## Sweeping

Julia için nesne havuzlarının temizlenmesi iki kategoriye ayrılabilir: eğer havuz ayarlayıcısı tarafından yönetilen bir sayfa en az bir canlı nesne içeriyorsa, o zaman serbest liste ölü nesnelerin arasından geçirilmelidir; eğer bir sayfa hiç canlı nesne içermiyorsa, o zaman temel fiziksel belleği işletim sistemine geri döndürülebilir, örneğin, Linux'ta madvise sistem çağrıları kullanılarak.

İlk süpürme kategorisi, iş çalma yoluyla paralelleştirilmiştir. İkinci süpürme kategorisi için, `--gcthreads=X,1` bayrağı ile eşzamanlı sayfa süpürme etkinleştirildiğinde, madvise sistem çağrılarını arka planda bir süpürücü iş parçacığında, mutatör iş parçacıklarıyla eşzamanlı olarak gerçekleştiriyoruz. Toplayıcının durdurma-dünya aşamasında, canlı nesne içermeyen havuzda tahsis edilen sayfalar başlangıçta `pool_page_lazily_freed` içine itilir. Arka plan süpürme iş parçacığı daha sonra uyanır ve `pool_page_lazily_freed`'den sayfaları kaldırmaktan, bunlar üzerinde madvise çağrısı yapmaktan ve bunları `pool_page_freed`'e eklemekten sorumludur. Yukarıda açıklandığı gibi, `pool_page_lazily_freed` de mutatör iş parçacıklarıyla paylaşılmaktadır. Bu, tahsis ağırlıklı çok iş parçacıklı iş yüklerinde, mutatör iş parçacıklarının genellikle bir tahsis sırasında (taze mmaped sayfaya erişimden veya madvised sayfaya erişimden kaynaklanan) bir sayfa hatasından kaçınacağı anlamına gelir; çünkü doğrudan `pool_page_lazily_freed`'den bir sayfa tahsis ederken, arka plan süpürücü iş parçacığının bazıları zaten mutatörler tarafından talep edildiğinden daha az sayfayı madvise etmesi gerekir.

## Heuristics

GC sezgileri, çöp toplama işlemleri arasındaki tahsis aralığının boyutunu değiştirerek GC'yi ayarlar.

GC sezgileri, bir toplama işleminden sonra yığın boyutunun ne kadar büyük olduğunu ölçer ve bir sonraki toplama işlemini https://dl.acm.org/doi/10.1145/3563323 adresinde açıklanan algoritmaya göre ayarlar. Özetle, yığın hedefinin canlı yığın ile karekök ilişkisi olması gerektiğini ve ayrıca GC'nin nesneleri ne kadar hızlı serbest bıraktığı ve mutatörlerin ne kadar hızlı tahsis yaptığı ile ölçeklenmesi gerektiğini savunur. Sezgiler, kullanılan sayfa sayısını ve malloc kullanan nesneleri sayarak yığın boyutunu ölçer. Daha önce yığın boyutunu canlı nesneleri sayarak ölçüyorduk, ancak bu, kötü kararlara yol açabilecek parçalanmayı dikkate almıyordu. Bu aynı zamanda, bir süreç genelinde (ne zaman GC yapılacağı) kararlar almak için iş parçacığı yerel bilgilerini (tahsisler) kullandığımız anlamına geliyordu; sayfaları ölçmek, kararın küresel olmasını sağlar.

GC, yığın boyutu maksimum izin verilen boyutun %80'ine ulaştığında tam toplama işlemleri yapacaktır.
