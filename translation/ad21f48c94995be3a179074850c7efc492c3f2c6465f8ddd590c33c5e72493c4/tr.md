```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Logging/docs/src/index.md"
```

# [Logging](@id man-logging)

[`Logging`](@ref Logging.Logging) modülü, bir hesaplamanın tarihini ve ilerlemesini olayların bir kaydı olarak kaydetmenin bir yolunu sağlar. Olaylar, kaynak koda bir günlük kaydı ifadesi ekleyerek oluşturulur, örneğin:

```julia
@warn "Abandon printf debugging, all ye who enter here!"
┌ Warning: Abandon printf debugging, all ye who enter here!
└ @ Main REPL[1]:1
```

Sistem, `println()` çağrılarıyla kaynak kodunuzu karıştırmaktan daha fazla avantaj sunar. İlk olarak, kaynak kodunu düzenlemeden mesajların görünürlüğünü ve sunumunu kontrol etmenizi sağlar. Örneğin, yukarıdaki `@warn` ile karşılaştırıldığında

```julia
@debug "The sum of some values $(sum(rand(100)))"
```

varsayılan olarak hiçbir çıktı üretmeyecektir. Ayrıca, bu tür hata ayıklama ifadelerini kaynak kodunda bırakmak çok ucuzdur çünkü sistem, mesajın daha sonra göz ardı edileceği durumlarda değerlendirilmesini önler. Bu durumda `sum(rand(100))` ve ilgili dize işleme, hata ayıklama kaydı etkinleştirilmedikçe asla yürütülmeyecektir.

İkincisi, günlükleme araçları, her olaya bir dizi anahtar-değer çifti olarak rastgele veriler eklemenize olanak tanır. Bu, yerel değişkenleri ve diğer program durumlarını daha sonraki analizler için yakalamanızı sağlar. Örneğin, yerel dizi değişkeni `A` ve bir vektör `v`'nin toplamını `s` anahtarı olarak eklemek için şunu kullanabilirsiniz:

```jldoctest
A = ones(Int, 4, 4)
v = ones(100)
@info "Some variables"  A  s=sum(v)

# output
┌ Info: Some variables
│   A =
│    4×4 Matrix{Int64}:
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
└   s = 100.0
```

Tüm günlükleme makroları `@debug`, `@info`, `@warn` ve `@error` ortak özellikler taşır ve bu özellikler daha genel makro [`@logmsg`](@ref) için belgelerde ayrıntılı olarak açıklanmıştır.

## Log event structure

Her bir etkinlik, kullanıcının sağladığı ve otomatik olarak çıkarılan bazı veriler de dahil olmak üzere birkaç veri parçası üretir. Öncelikle kullanıcı tanımlı verileri inceleyelim:

  * *log seviyesi*, erken filtreleme için kullanılan mesajın geniş bir kategorisidir. [`LogLevel`](@ref) türünde birkaç standart seviye vardır; kullanıcı tanımlı seviyeler de mümkündür. Her biri amacında farklıdır:

      * [`Logging.Debug`](@ref) (log seviyesi -1000) programın geliştiricisi için tasarlanmış bilgilerdir. Bu olaylar varsayılan olarak devre dışıdır.
      * [`Logging.Info`](@ref) (log seviyesi 0) kullanıcıya genel bilgi vermek içindir. Bunu, `println` kullanmanın bir alternatifi olarak düşünün.
      * [`Logging.Warn`](@ref) (log seviyesi 1000) bir şeylerin yanlış olduğunu ve muhtemelen bir eylem gerektirdiğini, ancak şu anda programın hala çalıştığını ifade eder.
      * [`Logging.Error`](@ref) (log seviyesi 2000) bir şeylerin yanlış olduğunu ve bunun, en azından bu kod parçası tarafından, kurtarılmasının pek olası olmadığını ifade eder. Genellikle bu log seviyesi gereksizdir çünkü bir istisna fırlatmak gerekli tüm bilgileri iletebilir.
  * *mesaj* bir olayı tanımlayan bir nesnedir. Gelenek gereği, mesaj olarak geçirilen `AbstractString`'lerin markdown formatında olduğu varsayılır. Diğer türler, metin tabanlı çıktı için `print(io, obj)` veya `string(obj)` kullanılarak ve muhtemelen kurulu günlüğü kullanarak diğer multimedya görüntülemeleri için `show(io,mime,obj)` ile görüntülenecektir.
  * Opsiyonel *anahtar–değer çiftleri*, her olaya rastgele verilerin eklenmesine olanak tanır. Bazı anahtarların, bir olayın nasıl yorumlandığını etkileyebilecek geleneksel anlamları vardır (bkz. [`@logmsg`](@ref)).

Sistem ayrıca her etkinlik için bazı standart bilgileri de üretir:

  * Genişletilen `module` günlükleme makrosunun bulunduğu.
  * Kaynak kodda günlükleme makrosunun gerçekleştiği `dosya` ve `satır`.
  * Bir `id` mesajı, günlükleme makrosunun göründüğü *kaynak kodu ifadesi* için benzersiz, sabit bir tanımlayıcıdır. Bu tanımlayıcı, dosyanın kaynak kodu değişse bile, günlükleme ifadesi kendisi aynı kaldığı sürece oldukça kararlı olacak şekilde tasarlanmıştır.
  * Bir etkinlik için `grup`, varsayılan olarak dosyanın uzantısı olmadan temel adı olarak ayarlanmıştır. Bu, mesajları log seviyesinden daha ince kategorilere ayırmak için kullanılabilir (örneğin, tüm kullanım dışı uyarılar `:depwarn` grubuna sahiptir) veya modüller arasında veya içinde mantıksal gruplamalar yapmak için.

Dikkat edin ki, etkinlik zamanı gibi bazı yararlı bilgiler varsayılan olarak dahil edilmemiştir. Bunun nedeni, bu tür bilgilerin çıkarılmasının maliyetli olabilmesi ve ayrıca mevcut günlüğü tutucuya *dinamik olarak* erişilebilir olmasıdır. Gerekli olduğunda etkinlik verilerini zaman, geri izleme, küresel değişkenlerin değerleri ve diğer yararlı bilgilerle artırmak için bir [custom logger](@ref AbstractLogger-interface) tanımlamak basittir.

## Processing log events

Gördüğünüz gibi örneklerde, günlükleme ifadeleri günlük olaylarının nereye gittiği veya nasıl işlendiği hakkında hiçbir şey belirtmiyor. Bu, sistemi bileşenler halinde birleştirilebilir ve eşzamanlı kullanım için doğal hale getiren önemli bir tasarım özelliğidir. Bu, iki farklı kaygıyı ayırarak yapılır:

  * *Oluşturma* log olayları, olayların ne zaman tetikleneceğine ve hangi bilgilerin dahil edileceğine karar vermesi gereken modül yazarının sorumluluğudur.
  * *Log olaylarının işlenmesi* — yani, görüntüleme, filtreleme, toplama ve kaydetme — birden fazla modülü bir araya getirip işbirliği yapan bir uygulama oluşturması gereken uygulama yazarının endişesidir.

### Loggers

Olayların işlenmesi bir *logger* tarafından gerçekleştirilir; bu, olayı gören ilk kullanıcı yapılandırılabilir kod parçasıdır. Tüm logger'lar [`AbstractLogger`](@ref) alt türleri olmalıdır.

Bir olay tetiklendiğinde, uygun günlüğü bulmak için global günlüğü yedek olarak kullanarak görev yerel günlüğüne bakılır. Buradaki fikir, uygulama kodunun günlük olaylarının nasıl işlenmesi gerektiğini bilmesidir ve bu, çağrı yığınında bir yerde üstte bulunur. Bu nedenle, günlüğü keşfetmek için çağrı yığınına yukarı doğru bakmalıyız — yani, günlük *dinamik olarak kapsamlı* olmalıdır. (Bu, günlüğün *sözdizimsel olarak kapsamlı* olduğu günlüğü çerçeveleri ile bir karşıtlık noktasıdır; modül yazarının açıkça sağladığı veya basit bir global değişken olarak. Böyle bir sistemde, birden fazla modülden işlevsellik oluştururken günlüğü kontrol etmek zorlayıcıdır.)

Küresel günlükleyici [`global_logger`](@ref) ile ayarlanabilir ve görev yerel günlükleyicileri [`with_logger`](@ref) kullanılarak kontrol edilir. Yeni oluşturulan görevler, ana görevin günlükleyicisini miras alır.

Kütüphane tarafından sağlanan üç logger türü vardır.  [`ConsoleLogger`](@ref) REPL'yi başlattığınızda gördüğünüz varsayılan logger'dır. Olayları okunabilir bir metin formatında görüntüler ve biçimlendirme ve filtreleme üzerinde basit ama kullanıcı dostu bir kontrol sağlamaya çalışır. [`NullLogger`](@ref) gerektiğinde tüm mesajları atmanın pratik bir yoludur; bu, [`devnull`](@ref) akışının logging eşdeğeridir. [`SimpleLogger`](@ref) ise, esasen logging sisteminin kendisini hata ayıklamak için yararlı olan çok basit bir metin biçimlendirme logger'dır.

Özel günlükleyiciler, [reference section](@ref AbstractLogger-interface) tanımlanan işlevler için aşırı yüklemelerle birlikte gelmelidir.

### Early filtering and message handling

Bir olay meydana geldiğinde, atılacak mesajların üretilmesini önlemek için birkaç erken filtreleme adımı gerçekleşir:

1. Mesaj günlük seviyesi, bir global minimum seviye ile kontrol edilir (şu şekilde ayarlanmıştır: [`disable_logging`](@ref)). Bu, kaba ama son derece ucuz bir global ayardır.
2. Mevcut logger durumu kontrol edilir ve mesaj seviyesi, [`Logging.min_enabled_level`](@ref) çağrılarak bulunan logger'ın önbelleğe alınmış minimum seviyesi ile karşılaştırılır. Bu davranış, ortam değişkenleri aracılığıyla geçersiz kılınabilir (bununla ilgili daha fazla bilgi daha sonra).
3. [`Logging.shouldlog`](@ref) fonksiyonu, bazı minimal bilgileri (seviye, modül, grup, kimlik) alarak mevcut logger ile çağrılır; bu bilgiler statik olarak hesaplanabilir. En kullanışlı olanı, `shouldlog`'a bir olay `kimliği` geçilir; bu, önceden belirlenmiş bir koşula dayanarak olayları erken bir şekilde atmak için kullanılabilir.

Eğer bu kontrollerin hepsi geçerse, mesaj ve anahtar-değer çiftleri tam olarak değerlendirilir ve mevcut günlüğe [`Logging.handle_message`](@ref) fonksiyonu aracılığıyla iletilir. `handle_message()` gerektiğinde ek filtreleme yapabilir ve olayı ekranda gösterebilir, bir dosyaya kaydedebilir vb.

Oluşturma sırasında meydana gelen istisnalar, varsayılan olarak yakalanır ve kaydedilir. Bu, bireysel bozuk olayların uygulamayı çökertmesini önler; bu, üretim sisteminde az kullanılan hata ayıklama olaylarını etkinleştirirken faydalıdır. Bu davranış, [`Logging.catch_exceptions`](@ref) uzantısını kullanarak her bir günlüğü kaydedici türü için özelleştirilebilir.

## Testing log events

Log olayları, normal kodu çalıştırmanın bir yan etkisidir, ancak belirli bilgilendirici mesajları ve uyarıları test etmek isteyebilirsiniz. `Test` modülü, günlük olay akışına karşı desen eşleştirmek için kullanılabilecek bir [`@test_logs`](@ref) makrosu sağlar.

## Environment variables

Mesaj filtreleme, [`JULIA_DEBUG`](@ref JULIA_DEBUG) ortam değişkeni aracılığıyla etkilenebilir ve bir dosya veya modül için hata ayıklama günlüğünü etkinleştirmenin kolay bir yolunu sunar. `JULIA_DEBUG=loading` ile julia yüklemek, `loading.jl` dosyasında `@debug` günlük mesajlarını etkinleştirecektir. Örneğin, Linux kabuklarında:

```
$ JULIA_DEBUG=loading julia -e 'using OhMyREPL'
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
[ Info: Recompiling stale cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji for module OhMyREPL
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/Tokenize.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
...
```

Windows'ta, aynı şey `CMD`'de `set JULIA_DEBUG="loading"` komutunu çalıştırarak ve `Powershell`'da `$env:JULIA_DEBUG="loading"` komutunu kullanarak gerçekleştirilebilir.

Benzer şekilde, ortam değişkeni `Pkg` gibi modüllerin veya modül köklerinin hata ayıklama günlüklemesini etkinleştirmek için kullanılabilir (bkz. [`Base.moduleroot`](@ref)). Tüm hata ayıklama günlüklemesini etkinleştirmek için özel değer `all` kullanın.

REPL'den hata ayıklama günlüğünü açmak için `ENV["JULIA_DEBUG"]`'yi ilgi alanındaki modülün adıyla ayarlayın. REPL'de tanımlanan fonksiyonlar `Main` modülüne aittir; bunlar için günlüğü şu şekilde etkinleştirebilirsiniz:

```julia-repl
julia> foo() = @debug "foo"
foo (generic function with 1 method)

julia> foo()

julia> ENV["JULIA_DEBUG"] = Main
Main

julia> foo()
┌ Debug: foo
└ @ Main REPL[1]:1

```

Birden fazla modül için hata ayıklamayı etkinleştirmek için virgül ayırıcı kullanın: `JULIA_DEBUG=loading,Main`.

## Examples

### Example: Writing log events to a file

Bazen log olaylarını bir dosyaya yazmak faydalı olabilir. İşte bir görev yerel ve global günlüğü kullanarak bir metin dosyasına bilgi yazmanın bir örneği:

```julia-repl
# Load the logging module
julia> using Logging

# Open a textfile for writing
julia> io = open("log.txt", "w+")
IOStream(<file log.txt>)

# Create a simple logger
julia> logger = SimpleLogger(io)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# Log a task-specific message
julia> with_logger(logger) do
           @info("a context specific log message")
       end

# Write all buffered messages to the file
julia> flush(io)

# Set the global logger to logger
julia> global_logger(logger)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# This message will now also be written to the file
julia> @info("a global log message")

# Close the file
julia> close(io)
```

### Example: Enable debug-level messages

İşte [`ConsoleLogger`](@ref) oluşturmanın bir örneği; bu, log seviyesi [`Logging.Debug`](@ref) veya daha yüksek olan herhangi bir mesajı geçiren bir yapı sağlar.

```julia-repl
julia> using Logging

# Create a ConsoleLogger that prints any log messages with level >= Debug to stderr
julia> debuglogger = ConsoleLogger(stderr, Logging.Debug)

# Enable debuglogger for a task
julia> with_logger(debuglogger) do
           @debug "a context specific log message"
       end

# Set the global logger
julia> global_logger(debuglogger)
```

## Reference

### Logging module

```@docs
Logging.Logging
```

### Creating events

```@docs
Logging.@logmsg
Logging.LogLevel
Logging.Debug
Logging.Info
Logging.Warn
Logging.Error
Logging.BelowMinLevel
Logging.AboveMaxLevel
```

### [Processing events with AbstractLogger](@id AbstractLogger-interface)

Olay işleme, `AbstractLogger` ile ilişkili işlevlerin geçersiz kılınmasıyla kontrol edilir:

| Methods to implement                |                        | Brief description                            |
|:----------------------------------- |:---------------------- |:-------------------------------------------- |
| [`Logging.handle_message`](@ref)    |                        | Handle a log event                           |
| [`Logging.shouldlog`](@ref)         |                        | Early filtering of events                    |
| [`Logging.min_enabled_level`](@ref) |                        | Lower bound for log level of accepted events |
| **Optional methods**                | **Default definition** | **Brief description**                        |
| [`Logging.catch_exceptions`](@ref)  | `true`                 | Catch exceptions during event evaluation     |

```@docs
Logging.AbstractLogger
Logging.handle_message
Logging.shouldlog
Logging.min_enabled_level
Logging.catch_exceptions
Logging.disable_logging
```

### Using Loggers

Logger kurulumu ve denetimi:

```@docs
Logging.global_logger
Logging.with_logger
Logging.current_logger
```

Sisteme ile birlikte sağlanan loglayıcılar:

```@docs
Logging.NullLogger
Logging.ConsoleLogger
Logging.SimpleLogger
```
