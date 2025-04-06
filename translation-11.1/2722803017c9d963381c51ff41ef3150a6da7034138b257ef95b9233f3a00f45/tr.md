# Ahead of Time Compilation

Bu belge, Julia'daki önceden derleme (AOT) derleme sisteminin tasarımını ve yapısını tanımlamaktadır. Bu sistem, sistem görüntüleri ve paket görüntüleri oluşturulurken kullanılır. Burada açıklanan uygulamanın çoğu `aotcompile.cpp`, `staticdata.c` ve `processor.cpp` dosyalarında bulunmaktadır.

## Introduction

Julia normalde kodu anında derlese de (JIT), kodu önceden derlemek ve elde edilen kodu bir dosyaya kaydetmek mümkündür. Bu, bir dizi neden için faydalı olabilir:

1. Julia sürecini başlatma süresini azaltmak için.
2. JIT derleyicisinde kodu çalıştırmaktan harcanan zamanı azaltmak için (ilk yürütme süresi, TTFX).
3. JIT derleyicisinin kullandığı bellek miktarını azaltmak için.

## High-Level Overview

Aşağıdaki tanımlar, kullanıcının yeni bir AOT modülü derlediği zaman, örneğin `using Foo` yazdığında, içsel olarak gerçekleşen uçtan uca boru hattının mevcut uygulama ayrıntılarının bir anlık görüntüsüdür. Bu ayrıntılar, bunları yönetmenin daha iyi yollarını uyguladıkça zamanla değişme olasılığı taşımaktadır, bu nedenle mevcut uygulamalar aşağıda açıklanan veri akışı ve işlevlerle tam olarak eşleşmeyebilir.

### Compiling Code Images

Öncelikle, yerel koda derlenmesi gereken yöntemlerin tanımlanması gerekir. Bu, yalnızca derlenecek kodun gerçekten çalıştırılmasıyla yapılabilir, çünkü derlenmesi gereken yöntemlerin kümesi, yöntemlere geçirilen argümanların türlerine bağlıdır ve belirli tür kombinasyonlarıyla yapılan yöntem çağrıları, çalışma zamanına kadar bilinmeyebilir. Bu süreçte, derleyicinin gördüğü kesin yöntemler, daha sonraki derleme için izlenir ve bir derleme izi üretilir.

!!! note
    Şu anda görüntüleri derlerken, Julia izleme oluşturmayı AOT derlemesini gerçekleştiren süreçten farklı bir süreçte çalıştırıyor. Bu, ön derleme sırasında bir hata ayıklayıcı kullanmaya çalışırken etkiler yaratabilir. Hata ayıklayıcı ile ön derlemeyi hata ayıklamanın en iyi yolu, rr hata ayıklayıcısını kullanmak, tüm süreç ağacını kaydetmek, ilgili başarısız süreci tanımlamak için `rr ps` komutunu kullanmak ve ardından yalnızca başarısız süreci yeniden oynamak için `rr replay -p PID` komutunu kullanmaktır.


Yöntemler belirlendikten sonra, `jl_create_system_image` fonksiyonuna iletilirler. Bu fonksiyon, yerel kodu bir dosyaya serileştirdiğinde kullanılacak bir dizi veri yapısını kurar ve ardından yöntemlerin dizisi ile `jl_create_native` çağrısını yapar. `jl_create_native`, yöntemler üzerinde kod üretimi yapar ve bir veya daha fazla LLVM modülü üretir. `jl_create_system_image` daha sonra modülden ne tür bir kod üretildiğine dair bazı yararlı bilgileri kaydeder.

Modül(ler) daha sonra `jl_dump_native`'e, `jl_create_system_image` tarafından kaydedilen bilgilerle birlikte iletilir. `jl_dump_native`, modül(ler)i bit kodu, nesne veya montaj dosyalarına serileştirmek için gerekli kodu içerir; bu, Julia'ya geçirilen komut satırı seçeneklerine bağlıdır. Serileştirilmiş kod ve bilgiler daha sonra bir arşiv olarak bir dosyaya yazılır.

Son adım, `jl_dump_native` tarafından üretilen arşivdeki nesne dosyaları üzerinde bir sistem bağlayıcısı çalıştırmaktır. Bu adım tamamlandığında, derlenmiş kodu içeren bir paylaşımlı kütüphane üretilir.

### Loading Code Images

Kod görüntüsü yüklenirken, bağlayıcı tarafından üretilen paylaşılan kütüphane belleğe yüklenir. Sistem görüntü verileri daha sonra paylaşılan kütüphaneden yüklenir. Bu veriler, paylaşılan kütüphaneye derlenen türler, yöntemler ve kod örnekleri hakkında bilgi içerir. Bu veriler, çalışma zamanının durumunu kod görüntüsü derlendiğinde olduğu hale geri yüklemek için kullanılır.

Eğer kod görüntüsü çoklu versiyonlama ile derlenmişse, yükleyici mevcut makinedeki CPU özelliklerine dayanarak her fonksiyonun uygun versiyonunu kullanacaktır.

Sistem görüntüleri için, başka bir kod yüklenmediğinden, çalışma zamanının durumu artık kod görüntüsü derlendiğinde olduğu gibidir. Paket görüntüleri için, ortam kod derlendiğinde değişmiş olabilir, bu nedenle her yöntem, hala geçerli bir kod olup olmadığını belirlemek için küresel yöntem tablosuna karşı kontrol edilmelidir.

## Compiling Methods

### Tracing Compiled Methods

Julia, JIT derleyicisi tarafından derlenen tüm yöntemleri kaydetmek için bir komut satırı bayrağına sahiptir, `--trace-compile=filename`. Bir fonksiyon derlendiğinde ve bu bayrağın bir dosya adı varsa, Julia, çağrıldığı yöntem ve argüman türleri ile birlikte o dosyaya bir ön derleme ifadesi yazdırır. Bu nedenle, daha sonra AOT derleme sürecinde kullanılabilecek bir ön derleme betiği oluşturur. [PrecompileTools](https://julialang.github.io/PrecompileTools.jl/stable/) paketi, bu işlevsellikten yararlanmayı paket geliştiricileri için daha kolay hale getirebilecek araçlar sunmaktadır.

### `jl_create_system_image`

`jl_create_system_image`, Julia'ya özgü tüm meta verileri kaydeder ve bu, çalışma zamanının durumunu daha sonra geri yüklemek için gereklidir. Bu, kod örnekleri, yöntem örnekleri, yöntem tabloları ve tür bilgileri gibi verileri içerir. Bu işlev ayrıca yerel kodu bir dosyaya serileştirmek için gerekli veri yapılarını kurar. Son olarak, kendisine geçirilen yöntemler için yerel kodu içeren bir veya daha fazla LLVM modülü oluşturmak üzere `jl_create_native`'i çağırır. `jl_create_native`, kendisine geçirilen yöntemler üzerinde kod üretimi yapmaktan sorumludur.

### `jl_dump_native`

`jl_dump_native`, yerel kodu içeren LLVM modülünü bir dosyaya serileştirmekten sorumludur. Modülün yanı sıra, `jl_create_system_image` tarafından üretilen sistem görüntüsü verileri bir global değişken olarak derlenir. Bu yöntemin çıktısı, kod ve sistem görüntüsü verilerini içeren bit kodu, nesne ve/veya montaj arşivleridir.

`jl_dump_native`, yerel kod yayarken genellikle daha büyük zaman kayıplarından biridir; bu süreçte zamanın büyük bir kısmı LLVM IR'yi optimize etmekte ve makine kodu yaymakta harcanır. Bu nedenle, bu fonksiyon optimizasyon ve makine kodu yayma adımlarını çoklu iş parçacığı ile gerçekleştirme yeteneğine sahiptir. Bu çoklu iş parçacığı, modülün boyutuna göre parametrelenmiştir, ancak [`JULIA_IMAGE_THREADS`](@ref JULIA_IMAGE_THREADS) ortam değişkenini ayarlayarak açıkça geçersiz kılınabilir. Varsayılan maksimum iş parçacığı sayısı mevcut iş parçacıklarının sayısının yarısıdır, ancak bunu daha düşük bir değere ayarlamak, derleme sırasında zirve bellek kullanımını azaltabilir.

`jl_dump_native`, birden fazla mimari için optimize edilmiş yerel kod üretebilir, Julia yükleyicisi ile entegre edildiğinde. Bu, [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) ortam değişkenini ayarlayarak tetiklenir ve optimizasyon boru hattındaki çoklu versiyonlama geçişi tarafından yönetilir. Bunun çoklu iş parçacığı ile çalışmasını sağlamak için, modül alt modüllere ayrılmadan önce bir anotasyon adımı eklenir ve bu anotasyon adımı, hangi işlevlerin farklı mimariler için kopyalanacağına karar vermek için tüm modül boyunca mevcut olan bilgileri kullanır. Anotasyon yapıldıktan sonra, bireysel iş parçacıkları, kopyalanmış bir işlev tarafından çağrılacak gerekli işlevleri üretecek farklı bir alt modülün garanti edildiğini bilerek, farklı mimariler için kodu paralel olarak üretebilir.

Modülün nasıl serileştirildiğine dair bazı diğer meta veriler de arşivde saklanmaktadır; bunlar arasında modülü serileştirmek için kullanılan iş parçacığı sayısı ve derlenen fonksiyon sayısı bulunmaktadır.

### Static Linking

AOT derleme sürecindeki son adım, `jl_dump_native` tarafından üretilen arşivdeki nesne dosyaları üzerinde bir bağlayıcı çalıştırmaktır. Bu, derlenmiş kodu içeren bir paylaşımlı kütüphane üretir. Bu paylaşımlı kütüphane daha sonra Julia tarafından çalışma zamanının durumunu geri yüklemek için yüklenebilir. Bir sistem görüntüsü derlenirken, nihai paylaşımlı kütüphaneyi üretmek için bir C derleyicisi tarafından kullanılan yerel bağlayıcı kullanılır. Paket görüntüleri için, daha tutarlı bir bağlama arayüzü sağlamak amacıyla LLVM bağlayıcısı LLD kullanılır.

## Loading Code Images

### Loading the Shared Library

Kod görüntüsünü yüklemenin ilk adımı, bağlayıcı tarafından üretilen paylaşılan kütüphaneyi yüklemektir. Bu, paylaşılan kütüphanenin yolunda `jl_dlopen` çağrısı yapılarak gerçekleştirilir. Bu işlev, paylaşılan kütüphaneyi yüklemekten ve kütüphanedeki tüm sembolleri çözmekten sorumludur.

### Loading Native Code

Yükleyici öncelikle derlenmiş yerel kodun, yükleyicinin çalıştığı mimari için geçerli olup olmadığını belirlemelidir. Bu, daha eski CPU'ların tanımadığı talimatları çalıştırmaktan kaçınmak için gereklidir. Bu, mevcut makinedeki CPU özelliklerini, kodun derlendiği CPU özellikleriyle karşılaştırarak yapılır. Çoklu versiyonlama etkinleştirildiğinde, yükleyici mevcut makinedeki CPU özelliklerine dayalı olarak her işlevin uygun versiyonunu seçecektir. Eğer çoklu versiyonlanan özellik setlerinden hiçbiri yoksa, yükleyici bir hata verecektir.

Çoklu versiyonlama geçişinin bir kısmı, modüldeki tüm fonksiyonların bir dizi global dizi oluşturur. Bu süreç çok iş parçacıklı olduğunda, bir dizi dizisi oluşturulur ve yükleyici bunu bu mimari için derlenmiş tüm fonksiyonların bulunduğu tek bir büyük diziye yeniden düzenler. Modüldeki global değişkenler için benzer bir süreç gerçekleşir.

### Setting Up Julia State

Yükleyici, yerel kodu yüklemekten elde edilen global değişkenler ve fonksiyonları kullanarak mevcut süreçte Julia çalışma zamanı çekirdek veri yapılarını kurar. Bu kurulum, Julia çalışma zamanına türler ve yöntemler eklemeyi ve önbelleğe alınmış yerel kodun diğer Julia fonksiyonları ve yorumlayıcı tarafından kullanılabilir hale getirilmesini içerir. Paket görüntüleri için, her yöntem doğrulanmalıdır; yani, global yöntem tablosunun durumu, paket görüntüsünün derlendiği durumla eşleşmelidir. Özellikle, yükleme zamanında mevcut olan yöntemler ile paket görüntüsünün derleme zamanı arasında farklı bir yöntem seti varsa, yöntem geçersiz kılınmalı ve ilk kullanımda yeniden derlenmelidir. Bu, bir paketin önceden derlenip derlenmediğine veya kodun doğrudan yürütülüp yürütülmediğine bakılmaksızın yürütme anlamsalının aynı kalmasını sağlamak için gereklidir. Sistem görüntüleri bu doğrulamayı yapmak zorunda değildir, çünkü yükleme zamanında global yöntem tablosu boştur. Bu nedenle, sistem görüntüleri paket görüntülerine göre daha hızlı yükleme sürelerine sahiptir.
