# Parallel Computing

Julia bu dört kategoride eşzamanlı ve paralel programlamayı destekler:

1. **Asenkron "görevler", veya korutinler**:

    Julia Görevleri, I/O, olay işleme, üretici-tüketici süreçleri ve benzeri desenler için hesaplamaları askıya alma ve yeniden başlatma olanağı sağlar. Görevler, [`wait`](@ref) ve [`fetch`](@ref) gibi işlemler aracılığıyla senkronize olabilir ve [`Channel`](@ref) aracılığıyla iletişim kurabilir. Kendileri tam olarak paralel hesaplama olmasa da, Julia, [`Task`](@ref)'leri birden fazla iş parçacığında planlamanıza olanak tanır.
2. **Çoklu iş parçacığı**:

    Julia'nın [multi-threading](@ref man-multithreading) birden fazla iş parçacığı veya CPU çekirdeği üzerinde görevleri aynı anda planlama yeteneği sağlar ve bellek paylaşır. Bu genellikle bir PC'de veya tek bir büyük çok çekirdekli sunucuda paralellik elde etmenin en kolay yoludur. Julia'nın çoklu iş parçacığı kullanımı bileşenler halinde birleştirilebilir. Bir çoklu iş parçacıklı fonksiyon başka bir çoklu iş parçacıklı fonksiyonu çağırdığında, Julia tüm iş parçacıklarını mevcut kaynaklar üzerinde küresel olarak planlayacak ve aşırı yüklenmeyecek şekilde çalışacaktır.
3. **Dağıtık hesaplama**:

    Dağıtık hesaplama, ayrı bellek alanlarına sahip birden fazla Julia süreci çalıştırır. Bu süreçler aynı bilgisayarda veya birden fazla bilgisayarda olabilir. [`Distributed`](@ref man-distributed) standart kütüphanesi, bir Julia fonksiyonunun uzaktan yürütülmesi yeteneğini sağlar. Bu temel yapı taşı ile, birçok farklı türde dağıtık hesaplama soyutlamaları oluşturmak mümkündür. [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl) gibi paketler, böyle bir soyutlamanın örneğidir. Öte yandan, [`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) ve [`Elemental.jl`](https://github.com/JuliaParallel/Elemental.jl) mevcut MPI kütüphaneleri ekosistemine erişim sağlar.
4. **GPU hesaplama**:

    Julia GPU derleyicisi, Julia kodunu GPU'larda yerel olarak çalıştırma yeteneği sağlar. GPU'lara yönelik zengin bir Julia paketleri ekosistemi vardır. [JuliaGPU.org](https://juliagpu.org) web sitesi, yetenekler, desteklenen GPU'lar, ilgili paketler ve belgeler hakkında bir liste sunmaktadır.
