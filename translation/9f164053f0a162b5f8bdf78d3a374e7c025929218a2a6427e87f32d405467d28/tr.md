# Using Valgrind with Julia

[Valgrind](https://valgrind.org/) bellek hata ayıklama, bellek sızıntısı tespiti ve profil oluşturma aracıdır. Bu bölüm, Julia ile bellek sorunlarını ayıklarken Valgrind kullanırken akılda tutulması gereken şeyleri açıklar.

## General considerations

Varsayılan olarak, Valgrind, çalıştırdığı programlarda kendini değiştiren kod olmadığını varsayar. Bu varsayım çoğu durumda iyi çalışır, ancak `julia` gibi bir anında derleyici için feci şekilde başarısız olur. Bu nedenle, `valgrind`'a `--smc-check=all-non-file` parametresini geçirmek çok önemlidir, aksi takdirde kod çökebilir veya beklenmedik şekilde davranabilir (genellikle ince yollarla).

Bazı durumlarda, Valgrind kullanarak bellek hatalarını daha iyi tespit etmek için `julia`'yı bellek havuzları devre dışı bırakılarak derlemek faydalı olabilir. Derleme zamanı bayrağı `MEMDEBUG`, Julia'da bellek havuzlarını devre dışı bırakır ve `MEMDEBUG2`, FemtoLisp'te bellek havuzlarını devre dışı bırakır. `julia`'yı her iki bayrakla derlemek için, `Make.user` dosyasına aşağıdaki satırı ekleyin:

```make
CFLAGS = -DMEMDEBUG -DMEMDEBUG2
```

Başka bir not: Eğer programınız birden fazla işçi süreci kullanıyorsa, muhtemelen tüm bu işçi süreçlerinin Valgrind altında çalışmasını istersiniz, sadece ana süreç değil. Bunu yapmak için, `valgrind`'a `--trace-children=yes` parametresini geçin.

Başka bir not: `valgrind` kullanıyorsanız `Sistem görüntüsünde uyumlu hedef bulunamıyor` hatası alıyorsanız, sysimage'ı `generic` hedefi ile yeniden inşa etmeyi veya julia'yı `JULIA_CPU_TARGET=generic` ile derlemeyi deneyin.

## Suppressions

Valgrind genellikle çalışırken sahte uyarılar gösterir. Bu tür uyarıların sayısını azaltmak için, Valgrind'a bir [suppressions file](https://valgrind.org/docs/manual/manual-core.html#manual-core.suppress) sağlamak faydalıdır. Örnek bir bastırma dosyası, Julia kaynak dağıtımında `contrib/valgrind-julia.supp` içinde bulunmaktadır.

`julia/` kaynak dizininden aşağıdaki gibi suppressions dosyası kullanılabilir:

```
$ valgrind --smc-check=all-non-file --suppressions=contrib/valgrind-julia.supp ./julia progname.jl
```

Herhangi bir bellek hatası görüntülendiğinde, bunlar ya hata olarak bildirilmelidir ya da ek bastırmalar olarak katkıda bulunulmalıdır. Bazı Valgrind sürümlerinin [shipped with insufficient default suppressions](https://github.com/JuliaLang/julia/issues/8314#issuecomment-55766210) olduğu unutulmamalıdır, bu nedenle herhangi bir hata göndermeden önce dikkate alınması gereken bir şey olabilir.

## Running the Julia test suite under Valgrind

Tamam, tüm Julia test suite'ini Valgrind altında çalıştırmak mümkündür, ancak bu genellikle birkaç saat sürer. Bunu yapmak için, `julia/test/` dizininden aşağıdaki komutu çalıştırın:

```
valgrind --smc-check=all-non-file --trace-children=yes --suppressions=$PWD/../contrib/valgrind-julia.supp ../julia runtests.jl all
```

Eğer "kesin" bellek sızıntılarına dair bir rapor görmek istiyorsanız, `valgrind`'a `--leak-check=full --show-leak-kinds=definite` bayraklarını da geçin.

## Additional spurious warnings

Bu bölüm, bastırma dosyasına eklenemeyen ancak yine de göz ardı edilmesi güvenli olan Valgrind uyarılarını kapsar.

### Unhandled rr system calls

Valgrind, herhangi bir [system calls that are specific to rr](https://github.com/rr-debugger/rr/blob/master/src/preload/rrcalls.h), [Record and Replay Framework](https://rr-project.org/) ile karşılaşırsa bir uyarı verecektir. Özellikle, julia'nın rr altında çalışıp çalışmadığını tespit etmeye çalıştığında bir `1008` sistem çağrısı ile ilgili bir uyarı gösterilecektir:

```
--xxxxxx-- WARNING: unhandled amd64-linux syscall: 1008
--xxxxxx-- You may be able to write your own handler.
--xxxxxx-- Read the file README_MISSING_SYSCALL_OR_IOCTL.
--xxxxxx-- Nevertheless we consider this a bug.  Please report
--xxxxxx-- it at http://valgrind.org/support/bug_reports.html.
```

Bu sorunu [has been reported](https://bugs.kde.org/show_bug.cgi?id=446401) Valgrind geliştiricilerine iletin, çünkü bunu talep ettiler.

## Caveats

Valgrind şu anda [does not support multiple rounding modes](https://bugs.kde.org/show_bug.cgi?id=136779), bu nedenle yuvarlama modunu ayarlayan kod, Valgrind altında çalıştırıldığında farklı davranacaktır.

Genel olarak, `--smc-check=all-non-file` ayarını yaptıktan sonra programınızın Valgrind altında farklı davrandığını bulursanız, daha fazla araştırma yaparken `valgrind`'a `--tool=none` geçişini yapmanız faydalı olabilir. Bu, en az Valgrind mekanizmasını etkinleştirecek ancak tam bellek denetleyicisi etkinleştirildiğinde olduğundan çok daha hızlı çalışacaktır.
