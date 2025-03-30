# ARM (Linux)

Julia tamamen ARMv8 (AArch64) işlemcilerini destekler ve ARMv7 ve ARMv6 (AArch32) ile bazı kısıtlamalarla destek sunar. Bu dosya, belirli cihazlar için talimatların yanı sıra derleme için genel yönergeler sağlar.

[known issues](https://github.com/JuliaLang/julia/labels/arm) için ARM için bir liste mevcuttur. Zorluklarla karşılaşırsanız, lütfen `cat /proc/cpuinfo` çıktısını içeren bir sorun oluşturun.

## 32-bit (ARMv6, ARMv7)

Julia, aşağıdaki ARMv6 ve ARMv7 cihazlarının birkaç varyantında başarıyla derlenmiştir:

  * ARMv7 / Cortex A15 Samsung Chromebook'lar Ubuntu Linux altında Crouton ile çalışıyor;
  * [Raspberry Pi](https://www.raspberrypi.org)
  * [Odroid](https://www.hardkernel.com)

Julia, en az `armv6` ve `vfpv2` talimat setlerini gerektirir. `armv7-a` kullanılması önerilir. `armv5` veya yumuşak kayan nokta desteklenmemektedir.

### Raspberry Pi 1 / Raspberry Pi Zero

Eğer Raspberry Pi'de kullanılan ARM CPU türü LLVM tarafından tespit edilmezse, `Make.user` dosyasına aşağıdakileri ekleyerek CPU hedefini açıkça ayarlayın:

```
JULIA_CPU_TARGET=arm1176jzf-s
```

Tamamlamak için, takas dosyası boyutunu artırmanız gerekebilir. Bunu yapmak için, `/etc/dphys-swapfile` dosyasını düzenleyin ve şu satırı değiştirin:

```
CONF_SWAPSIZE=100
```

to:

```
CONF_SWAPSIZE=512
```

swapfile hizmetini yeniden başlatmadan önce:

```
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start
```

### Raspberry Pi 2

Raspberry Pi 2'de kullanılan ARM CPU türü LLVM tarafından tespit edilmez. Aşağıdakileri `Make.user` dosyasına ekleyerek CPU hedefini açıkça ayarlayın:

`JULIA_CPU_TARGET=cortex-a7`

Tam olarak derleyici ve dağıtıma bağlı olarak, desteklenmeyen satır içi montaj nedeniyle bir derleme hatası olabilir. Bu durumda, `Make.user` dosyasına `MCPU=armv7-a` ekleyin.

## AArch64 (ARMv8)

Julia, ARMv8 CPU'lar üzerinde çalışması ve geliştirilmesi bekleniyor. Genel [build instructions](https://github.com/JuliaLang/julia/blob/master/README.md) izlenmelidir. Julia'nın kendisini inşa etmek için yaklaşık 8GB RAM veya takas alanının etkinleştirilmesi bekleniyor.

### Known issues

Julia v1.10'dan itibaren, [JITLink](https://llvm.org/docs/JITLink.html) bu mimaride tüm işletim sistemleri için LLVM 15 veya daha yeni sürümlere bağlanırken otomatik olarak etkinleştirilmiştir. [bug in LLVM memory manager](https://github.com/llvm/llvm-project/issues/63236) nedeniyle, karmaşık iş yükleri çok fazla bellek haritası oluşturabilir ve bu da Linux'ta `/proc/sys/vm/max_map_count` dosyasında ayarlanan bellek haritaları (`mmap`) limitini aşabilir ve şu hatayı almanıza neden olabilir:

```
JIT session error: Cannot allocate memory
```

Bu gerçekleşirse, sistem yöneticinizden bellek eşlemeleri sınırını artırmasını isteyin, örneğin şu komutla

```
sysctl -w vm.max_map_count=262144
```
