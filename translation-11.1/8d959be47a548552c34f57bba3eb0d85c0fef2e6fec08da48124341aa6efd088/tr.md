# [gdb debugging tips](@id gdb-debugging-tips)

## Displaying Julia variables

`gdb` içinde herhangi bir `jl_value_t*` nesnesi `obj`, aşağıdaki gibi görüntülenebilir:

```
(gdb) call jl_(obj)
```

Nesne, `julia` oturumunda görüntülenecek, gdb oturumunda değil. Bu, Julia'nın C kodu tarafından işlenen nesnelerin türlerini ve değerlerini keşfetmek için yararlı bir yoldur.

Benzer şekilde, Julia'nın iç işleyişini (örneğin, `compiler.jl`) hata ayıklıyorsanız, `obj`'yi şu şekilde yazdırabilirsiniz:

```julia
ccall(:jl_, Cvoid, (Any,), obj)
```

Bu, Julia'nın çıktı akışlarının başlatılma sırasından kaynaklanan sorunları aşmanın iyi bir yoludur.

Julia'nın flisp yorumlayıcısı `value_t` nesnelerini kullanır; bunlar `call fl_print(fl_ctx, ios_stdout, obj)` ile görüntülenebilir.

## Useful Julia variables for Inspecting

Birçok değişkenin, tekil nesneler gibi, adreslerinin yazdırılması birçok hata için yararlı olabilir, ancak daha da yararlı olan bir dizi ek değişken vardır (tam liste için `julia.h` dosyasına bakın).

  * (when in `jl_apply_generic`) `mfunc` ve `jl_uncompress_ast(mfunc->def, mfunc->code)` :: çağrı yığını hakkında biraz bilgi edinmek için
  * `jl_lineno` ve `jl_filename` :: bir testte nereden hata ayıklamaya başlayacağınızı (veya bir dosyanın ne kadarının ayrıştırıldığını) anlamak için.
  * `$1` :: gerçekten bir değişken değil, ama son gdb komutunun (örneğin `print`) sonucuna atıfta bulunmak için hala yararlı bir kısayol.
  * `jl_options` :: bazen faydalı, çünkü başarıyla ayrıştırılan tüm komut satırı seçeneklerini listeler.
  * `jl_uv_stderr` :: çünkü kim stdio ile etkileşimde bulunmayı sevmez ki

## Useful Julia functions for Inspecting those variables

  * `jl_print_task_backtraces(0)` :: gdb'nin `thread apply all bt` veya lldb'nin `thread backtrace all` komutuna benzer. Tüm mevcut görevler için geri izleri yazdırırken tüm iş parçacıklarını çalıştırır.
  * `jl_gdblookup($pc)` :: Mevcut işlevi ve satırı bulmak için.
  * `jl_gdblookupinfo($pc)` :: Mevcut yöntem örneği nesnesini aramak için.
  * `jl_gdbdumpcode(mi)` :: REPL düzgün çalışmadığında `code_typed/code_llvm/code_asm`'nin tamamını dökmek için.
  * `jlbacktrace()` :: Hata yığınını stderr'ye dökmek için. Sadece `record_backtrace()` çağrıldıktan sonra kullanılabilir.
  * `jl_dump_llvm_value(Value*)` :: `Value->dump()`'ı gdb'de çağırmak için, burada yerel olarak çalışmıyor. Örneğin, `f->linfo->functionObject`, `f->linfo->specFunctionObject` ve `to_function(f->linfo)`.
  * `jl_dump_llvm_module(Module*)` :: GDB'de yerel olarak çalışmadığı için `Module->dump()`'ı çağırmak için.
  * `Type->dump()` :: sadece lldb'de çalışır. Not: lldb'nin çıktının üzerine istemini yazdırmasını önlemek için `;1` gibi bir şey ekleyin.
  * `jl_eval_string("expr")` :: mevcut durumu değiştirmek veya sembolleri aramak için yan etkileri tetiklemek amacıyla kullanılır.
  * `jl_typeof(jl_value_t*)` :: bir Julia değerinin tür etiketini çıkarmak için (gdb'de önce `macro define jl_typeof jl_typeof` çağırın veya tanımlamak için ilk argüman olarak kısa bir şey seçin, örneğin `ty`)

## Inserting breakpoints for inspection from gdb

`gdb` oturumunuzda `jl_breakpoint` içinde bir kesme noktası ayarlayın şöyle:

```
(gdb) break jl_breakpoint
```

Sonra Julia kodunuzun içine `jl_breakpoint` çağrısını ekleyin.

```julia
ccall(:jl_breakpoint, Cvoid, (Any,), obj)
```

`obj` herhangi bir değişken veya kesme noktasında erişilebilir olmasını istediğiniz bir demet olabilir.

`jl_apply` çerçevesine geri dönmek özellikle faydalıdır; buradan bir işlevin argümanlarını görüntülemek için, örneğin,

```
(gdb) call jl_(args[0])
```

Başka yararlı bir çerçeve `to_function(jl_method_instance_t *li, bool cstyle)`'dir. `jl_method_instance_t*` argümanı, derleyiciye gönderilen nihai AST'ye bir referans içeren bir yapıdır. Ancak, bu noktada AST genellikle sıkıştırılmış olacaktır; AST'yi görüntülemek için `jl_uncompress_ast` çağrısını yapın ve ardından sonucu `jl_`'ye iletin:

```
#2  0x00007ffff7928bf7 in to_function (li=0x2812060, cstyle=false) at codegen.cpp:584
584          abort();
(gdb) p jl_(jl_uncompress_ast(li, li->ast))
```

## Inserting breakpoints upon certain conditions

### Loading a particular file

Dosya `sysimg.jl` olarak adlandırılsın:

```
(gdb) break jl_load if strcmp(fname, "sysimg.jl")==0
```

### Calling a particular method

```
(gdb) break jl_apply_generic if strcmp((char*)(jl_symbol_name)(jl_gf_mtable(F)->name), "method_to_break")==0
```

Bu işlev her çağrıda kullanıldığı için, bunu yaparsanız her şeyi 1000 kat daha yavaş hale getireceksiniz.

## Dealing with signals

Julia düzgün çalışmak için birkaç sinyale ihtiyaç duyar. Profiler, örnekleme için `SIGUSR2` kullanır ve çöp toplayıcı, iş parçacıkları senkronizasyonu için `SIGSEGV` kullanır. Profiler veya birden fazla iş parçacığı kullanan bir kodu hata ayıklıyorsanız, hata ayıklayıcının bu sinyalleri göz ardı etmesini isteyebilirsiniz çünkü normal işlemler sırasında çok sık tetiklenebilirler. Bunu GDB'de yapmak için komut (göz ardı etmek istediğiniz `SIGSEGV` yerine `SIGUSR2` veya diğer sinyalleri koyun):

```
(gdb) handle SIGSEGV noprint nostop pass
```

İlgili LLDB komutu (işlem başlatıldıktan sonra):

```
(lldb) pro hand -p true -s false -n false SIGSEGV
```

Eğer çok iş parçacıklı kodda bir segfault'u hata ayıklıyorsanız, yalnızca gerçek segfault'u yakalamak için `jl_critical_error` üzerinde bir kesme noktası ayarlayabilirsiniz (Linux ve BSD'de `sigdie_handler` da işe yarayabilir).

## Debugging during Julia's build process (bootstrap)

`make` sırasında meydana gelen hatalar özel bir işleme ihtiyaç duyar. Julia iki aşamada inşa edilir, `sys0` ve `sys.ji` oluşturulur. Hata anında hangi komutların çalıştığını görmek için `make VERBOSE=1` kullanın.

Bu yazının yazıldığı sırada, `base` dizininden `sys0` aşamasında yapı hatalarını hata ayıklayabilirsiniz:

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys0 sysimg.jl
```

`usr/lib/julia/` dizinindeki tüm dosyaları silmeniz gerekebilir, bunun çalışması için.

`sys.ji` aşamasasını şu şekilde hata ayıklayabilirsiniz:

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys -J ../usr/lib/julia/sys0.ji sysimg.jl
```

Varsayılan olarak, herhangi bir hata Julia'nın çıkmasına neden olur, gdb altında bile. Bir hatayı "eylemde" yakalamak için `jl_error` içinde bir kesme noktası ayarlayın (belirli türdeki hatalar için birkaç başka yararlı nokta da vardır, bunlar arasında: `jl_too_few_args`, `jl_too_many_args` ve `jl_throw` bulunmaktadır).

Bir hata yakalandığında, yararlı bir teknik, yığın üzerinde yukarı yürümek ve `jl_apply` ile ilgili çağrıyı inceleyerek fonksiyonu gözlemlemektir. Gerçek bir dünya örneği almak için:

```
Breakpoint 1, jl_throw (e=0x7ffdf42de400) at task.c:802
802 {
(gdb) p jl_(e)
ErrorException("auto_unbox: unable to determine argument type")
$2 = void
(gdb) bt 10
#0  jl_throw (e=0x7ffdf42de400) at task.c:802
#1  0x00007ffff65412fe in jl_error (str=0x7ffde56be000 <_j_str267> "auto_unbox:
   unable to determine argument type")
   at builtins.c:39
#2  0x00007ffde56bd01a in julia_convert_16886 ()
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
...
```

En son `jl_apply` çerçeve #3'te, bu yüzden oraya geri dönebiliriz ve `julia_convert_16886` fonksiyonu için AST'ye bakabiliriz. Bu, `convert`'in bazı yöntemleri için benzersiz bir isimdir. Bu çerçevede `f`, bir `jl_function_t*` olduğundan, `specTypes` alanından tür imzasına, varsa, bakabiliriz:

```
(gdb) f 3
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
1281            return f->fptr((jl_value_t*)f, args, nargs);
(gdb) p f->linfo->specTypes
$4 = (jl_tupletype_t *) 0x7ffdf39b1030
(gdb) p jl_( f->linfo->specTypes )
Tuple{Type{Float32}, Float64}           # <-- type signature for julia_convert_16886
```

Sonra, bu fonksiyonun AST'sine bakabiliriz:

```
(gdb) p jl_( jl_uncompress_ast(f->linfo, f->linfo->ast) )
Expr(:lambda, Array{Any, 1}[:#s29, :x], Array{Any, 1}[Array{Any, 1}[], Array{Any, 1}[Array{Any, 1}[:#s29, :Any, 0], Array{Any, 1}[:x, :Any, 0]], Array{Any, 1}[], 0], Expr(:body,
Expr(:line, 90, :float.jl)::Any,
Expr(:return, Expr(:call, :box, :Float32, Expr(:call, :fptrunc, :Float32, :x)::Any)::Any)::Any)::Any)::Any
```

Son olarak, belki de en kullanışlı olanı, işlevin yeniden derlenmesini zorlayarak kod oluşturma sürecinde adım adım ilerleyebiliriz. Bunu yapmak için, `jl_lamdbda_info_t*` içindeki önbelleğe alınmış `functionObject`'ı temizleyin:

```
(gdb) p f->linfo->functionObject
$8 = (void *) 0x1289d070
(gdb) set f->linfo->functionObject = NULL
```

Sonra, faydalı bir yere bir kesme noktası ayarlayın (örneğin, `emit_function`, `emit_expr`, `emit_call` vb.) ve kod üretimini çalıştırın:

```
(gdb) p jl_compile(f)
... # your breakpoint here
```

## Debugging precompilation errors

Modül ön derlemesi, her modülü ön derlemek için ayrı bir Julia süreci başlatır. Bir ön derleme işçisinde bir kesme noktası ayarlamak veya hataları yakalamak, işçiye bir hata ayıklayıcı bağlamayı gerektirir. En kolay yaklaşım, hata ayıklayıcının belirli bir adı eşleşen yeni süreç başlatmalarını izlemesini ayarlamaktır. Örneğin:

```
(gdb) attach -w -n julia-debug
```

veya:

```
(lldb) process attach -w -n julia-debug
```

Sonra önceden derlemeyi başlatmak için bir betik/komut çalıştırın. Daha önce açıklandığı gibi, belirli dosya yükleme olaylarını yakalamak ve hata ayıklama penceresini daraltmak için ana süreçte koşullu kesme noktaları kullanın. (bazı işletim sistemleri, ana süreçten her `fork`'u takip etmek gibi alternatif yaklaşımlar gerektirebilir)

## Mozilla's Record and Replay Framework (rr)

Julia artık Mozilla'nın hafif kayıt ve deterministik hata ayıklama çerçevesi [rr](https://rr-project.org/) ile kutudan çıkar çıkmaz çalışıyor. Bu, bir yürütmenin izini deterministik olarak yeniden oynamanızı sağlar. Yeniden oynatılan yürütmenin adres alanları, kayıt içeriği, sistem çağrısı verileri vb. her çalıştırmada tam olarak aynıdır.

Gerekli olan rr'nin en son sürümü (3.1.0 veya daha yüksek)dır.

### Reproducing concurrency bugs with rr

rr, varsayılan olarak tek iş parçacıklı bir makineyi simüle eder. Eşzamanlı kodu hata ayıklamak için `rr record --chaos` kullanabilirsiniz; bu, rr'nin rastgele seçilen bir ila sekiz çekirdek arasında simülasyon yapmasına neden olur. Bu nedenle, `JULIA_NUM_THREADS=8` ayarlamak ve kodunuzu rr altında yeniden çalıştırmak isteyebilirsiniz, ta ki hatanızı yakalayana kadar.
