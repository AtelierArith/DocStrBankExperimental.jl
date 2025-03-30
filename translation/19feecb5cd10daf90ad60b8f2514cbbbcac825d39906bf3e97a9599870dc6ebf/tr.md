# Sanitizer support

[Sanitizers](https://github.com/google/sanitizers) özel Julia derlemelerinde Julia'nın dahili C/C++ kodundaki belirli hata türlerini tespit etmeyi kolaylaştırmak için kullanılabilir.

## Address Sanitizer: easy build

Bir Julia kaynak kontrolünden, Julia ve LLVM'de adres sanitizasyonunu destekleyen bir sürümü aşağıdaki gibi oluşturabilmelisiniz:

```sh
$ mkdir /tmp/julia
$ contrib/asan/build.sh /tmp/julia/
```

Burada `/tmp/julia`'yı bir derleme dizini olarak seçtik, ancak istediğiniz herhangi birini seçebilirsiniz. Derleme tamamlandıktan sonra, test etmek istediğiniz iş yükünü `/tmp/julia/julia` ile çalıştırın. Bellek hataları hatalara yol açacaktır.

Eğer özelleştirme veya daha fazla ayrıntı gerekiyorsa, aşağıdaki belgeleri inceleyin.

## General considerations

Clang'in sanitizatörlerini kullanmak, elbette Clang kullanmanızı gerektirir (`USECLANG=1`), ancak başka bir durum daha var: Çoğu sanitizatör, ana derleyici tarafından sağlanan bir çalışma zamanı kütüphanesi gerektirir; oysa Julia'nın JIT tarafından üretilen enstrümante kod, bu kütüphaneden gelen işlevselliğe dayanır. Bu, ana derleyicinizin LLVM sürümünün, Julia içinde kullanılan LLVM kütüphanesinin sürümüyle eşleşmesi gerektiği anlamına gelir.

Kolay bir çözüm, `BUILD_LLVM_CLANG=1` ile inşa ederek eşleşen bir araç zinciri sağlamak için özel bir inşa klasörüne sahip olmaktır. Daha sonra, `CC` ve `CXX` değişkenlerini geçersiz kılarken `USECLANG=1` belirterek bu araç zincirine başka bir inşa klasöründen atıfta bulunabilirsiniz.

Sanitizerlar, `RTLD_DEEPBIND` kullanılarak açılan bir paylaşımlı kütüphane tespit edildiğinde hata verir (ref: [google/sanitizers#611](https://github.com/google/sanitizers/issues/611)). Varsayılan olarak [libblastrampoline](https://github.com/staticfloat/libblastrampoline) `RTLD_DEEPBIND` kullanır, bu nedenle bir sanitizer kullanırken ortam değişkenini `LBT_USE_RTLD_DEEPBIND=0` olarak ayarlamamız gerekiyor.

Bir dezenfektanı kullanmak için `SANITIZE=1` ayarını yapın ve ardından kullanmak istediğiniz dezenfektan için uygun bayrağı ekleyin.

macOS'ta, bunun çalışması için bazı ek bayraklar gerekebilir. Toplamda, aşağıdaki `SANITIZE_*` bayraklarından bir veya daha fazlası ile birlikte şöyle görünebilir:

```
make -C deps USE_BINARYBUILDER_LLVM=0 LLVM_VER=svn stage-llvm

make -C src SANITIZE=1 USECLANG=1 \
    CC=~+/deps/scratch/llvm-svn/build_Release/bin/clang \
    CXX=~+/deps/scratch/llvm-svn/build_Release/bin/clang++ \
    CPPFLAGS="-isysroot $(xcode-select -p)/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk" \
    CXXFLAGS="-isystem $(xcode-select -p)/Toolchains/XcodeDefault.xctoolchain/usr/include/c++/v1"
```

(veya bunları her seferinde hatırlamanıza gerek kalmaması için `Make.user` dosyanıza koyun).

## Address Sanitizer (ASAN)

Bellek hatalarını tespit etmek veya hata ayıklamak için Clang'in [address sanitizer (ASAN)](https://clang.llvm.org/docs/AddressSanitizer.html) aracını kullanabilirsiniz. `SANITIZE_ADDRESS=1` ile derleme yaparak Julia derleyicisi ve onun ürettiği kod için ASAN'ı etkinleştirirsiniz. Ayrıca, LLVM kütüphanesini de temizlemek için `LLVM_SANITIZE=1` belirtebilirsiniz. Bu seçeneklerin yüksek performans ve bellek maliyeti olduğunu unutmayın. Örneğin, Julia ve LLVM için ASAN kullanmak `testall1`'in 8-10 kat daha uzun sürmesine ve 20 kat daha fazla bellek kullanmasına neden olur (bu, aşağıda açıklanan seçenekleri kullanarak sırasıyla 3 ve 4 katına düşürülebilir).

Varsayılan olarak, Julia `allow_user_segv_handler=1` ASAN bayrağını ayarlar; bu, sinyal iletiminin düzgün çalışması için gereklidir. Diğer seçenekleri `ASAN_OPTIONS` ortam bayrağını kullanarak tanımlayabilirsiniz; bu durumda, daha önce belirtilen varsayılan seçeneği tekrar etmeniz gerekecektir. Örneğin, bellek kullanımı `fast_unwind_on_malloc=0` ve `malloc_context_size=2` belirterek azaltılabilir, bu da geri izleme doğruluğundan fedakarlık etmek anlamına gelir. Şu anda, Julia ayrıca `detect_leaks=0` ayarını da yapar, ancak bu gelecekte kaldırılmalıdır.

### Example setup

#### Step 1: Install toolchain

Checkout a Git worktree (or create out-of-tree build directory) at `$TOOLCHAIN_WORKTREE` and create a config file `$TOOLCHAIN_WORKTREE/Make.user` with

```
USE_BINARYBUILDER_LLVM=1
BUILD_LLVM_CLANG=1
```

Çalıştır:

```sh
cd $TOOLCHAIN_WORKTREE
make -C deps install-llvm install-clang install-llvm-tools
```

to install toolchain binaries in `$TOOLCHAIN_WORKTREE/usr/tools`

#### Step 2: Build Julia with ASAN

`$BUILD_WORKTREE`'de bir Git worktree kontrol edin (veya ağaç dışı bir yapı dizini oluşturun) ve bir yapı dosyası oluşturun `$BUILD_WORKTREE/Make.user` ile

```
TOOLCHAIN=$(TOOLCHAIN_WORKTREE)/usr/tools

# use our new toolchain
USECLANG=1
override CC=$(TOOLCHAIN)/clang
override CXX=$(TOOLCHAIN)/clang++
export ASAN_SYMBOLIZER_PATH=$(TOOLCHAIN)/llvm-symbolizer

USE_BINARYBUILDER_LLVM=1

override SANITIZE=1
override SANITIZE_ADDRESS=1

# make the GC use regular malloc/frees, which are hooked by ASAN
override WITH_GC_DEBUG_ENV=1

# default to a debug build for better line number reporting
override JULIA_BUILD_MODE=debug

# make ASAN consume less memory
export ASAN_OPTIONS=detect_leaks=0:fast_unwind_on_malloc=0:allow_user_segv_handler=1:malloc_context_size=2

JULIA_PRECOMPILE=1

# tell libblastrampoline to not use RTLD_DEEPBIND
export LBT_USE_RTLD_DEEPBIND=0
```

Çalıştır:

```sh
cd $BUILD_WORKTREE
make debug
```

`julia-debug`'i ASAN ile oluşturmak için.

## Memory Sanitizer (MSAN)

Uninitialized bellek kullanımını tespit etmek için, [memory sanitizer (MSAN)](https://clang.llvm.org/docs/MemorySanitizer.html) kullanabilirsiniz, `SANITIZE_MEMORY=1` ile derleyerek.

## Thread Sanitizer (TSAN)

Veri yarışı ve diğer iş parçacığı ile ilgili sorunları ayıklamak için Clang'ın [thread sanitizer (TSAN)](https://clang.llvm.org/docs/ThreadSanitizer.html) kullanabilirsiniz, `SANITIZE_THREAD=1` ile derleyerek.
