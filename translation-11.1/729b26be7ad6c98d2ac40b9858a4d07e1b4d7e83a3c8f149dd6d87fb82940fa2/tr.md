# [Scope of Variables](@id scope-of-variables)

Bir değişkenin *kapsamı*, bir değişkenin erişilebilir olduğu kod bölgesidir. Değişken kapsamı, değişken adlandırma çakışmalarını önlemeye yardımcı olur. Kavram sezgisel: İki fonksiyonun da `x` adında argümanları olabilir, ancak bu iki `x` aynı şeye atıfta bulunmaz. Benzer şekilde, farklı kod bloklarının aynı adı kullanabileceği birçok başka durum vardır, ancak bunlar aynı şeye atıfta bulunmaz. Aynı değişken adının ne zaman aynı şeye atıfta bulunduğunu veya bulunmadığını belirleyen kurallara kapsam kuralları denir; bu bölüm bunları ayrıntılı olarak açıklar.

Belirli yapılar dilde *kapsam blokları* oluşturur; bu, bazı değişkenlerin kapsamı olabilecek kod bölgeleridir. Bir değişkenin kapsamı rastgele bir kaynak satırı seti olamaz; bunun yerine her zaman bu bloklardan biriyle hizalanır. Julia'da iki ana kapsam türü vardır: *küresel kapsam* ve *yerel kapsam*. İkincisi iç içe geçmiş olabilir. Ayrıca, Julia'da "sert kapsam" oluşturan yapılar ile yalnızca "yumuşak kapsam" oluşturan yapılar arasında bir ayrım vardır; bu, [shadowing](https://en.wikipedia.org/wiki/Variable_shadowing) aynı isimde bir küresel değişkenin izin verilip verilmeyeceğini etkiler.

### [Scope constructs](@id man-scope-table)

Kapsam bloklarını tanıtan yapılar şunlardır:

| Construct                                                                        | Scope type   | Allowed within |
|:-------------------------------------------------------------------------------- |:------------ |:-------------- |
| [`module`](@ref), [`baremodule`](@ref)                                           | global       | global         |
| [`struct`](@ref)                                                                 | local (soft) | global         |
| [`for`](@ref), [`while`](@ref), [`try`](@ref try)                                | local (soft) | global, local  |
| [`macro`](@ref)                                                                  | local (hard) | global         |
| functions, [`do`](@ref) blocks, [`let`](@ref) blocks, comprehensions, generators | local (hard) | global, local  |

Bu tablodan önemli ölçüde eksik olanlar [begin blocks](@ref man-compound-expressions) ve [if blocks](@ref man-conditional-evaluation) yeni kapsamlar tanıtmadığı için. Üç tür kapsam, aşağıda açıklanacak olan biraz farklı kurallara sahiptir.

Julia [lexical scoping](https://en.wikipedia.org/wiki/Scope_(computer_science)#Lexical_scope_vs._dynamic_scope) kullanır, bu da bir fonksiyonun kapsamının çağıranının kapsamından değil, fonksiyonun tanımlandığı kapsamdan miras aldığı anlamına gelir. Örneğin, aşağıdaki kodda `foo` içindeki `x`, `Bar` modülünün global kapsamındaki `x`'e atıfta bulunur:

```jldoctest moduleBar
julia> module Bar
           x = 1
           foo() = x
       end;
```

ve `foo`'nun kullanıldığı alanda `x` yok:

```jldoctest moduleBar
julia> import .Bar

julia> x = -1;

julia> Bar.foo()
1
```

Böylece *sözcüksel kapsam*, belirli bir kod parçasındaki bir değişkenin neye atıfta bulunduğunun yalnızca bulunduğu koddan çıkarılabileceği ve programın nasıl çalıştığına bağlı olmadığı anlamına gelir. Bir kapsam, başka bir kapsamın içinde yer aldığında, bulunduğu tüm dış kapsamlar içindeki değişkenleri "görebilir". Öte yandan, dış kapsamlar iç kapsamlar içindeki değişkenleri göremez.

## Global Scope

Her modül, diğer tüm modüllerin küresel kapsamından ayrı, yeni bir küresel kapsam tanıtır - her şey kapsayan bir küresel kapsam yoktur. Modüller, [using or import](@ref modules) ifadeleri aracılığıyla veya nokta notasyonu kullanarak nitelikli erişim yoluyla diğer modüllerin değişkenlerini kendi kapsamlarına tanıtabilir; yani her modül, adları değerlerle ilişkilendiren birinci sınıf veri yapısı olarak bir *isim alanı*dır.

Eğer bir üst düzey ifade `local` anahtar kelimesi ile bir değişken bildirimi içeriyorsa, o değişken o ifadenin dışından erişilemez. İfade içindeki değişken, aynı isimdeki küresel değişkenleri etkilemez. Bir örnek, üst düzeyde bir `begin` veya `if` bloğunda `local x` bildiriminde bulunmaktır:

```jldoctest
julia> x = 1
       begin
           local x = 0
           @show x
       end
       @show x;
x = 0
x = 1
```

Not edin ki etkileşimli istem (yani REPL), `Main` modülünün global kapsamındadır.

## [Local Scope](@id local-scope)

Yeni bir yerel kapsam, çoğu kod bloğu tarafından tanıtılır (tam liste için yukarıdaki [table](@ref man-scope-table) kısmına bakın). Eğer böyle bir blok başka bir yerel kapsamın içinde sözdizimsel olarak iç içe geçmişse, oluşturduğu kapsam, bulunduğu tüm yerel kapsamların içinde iç içe geçmiş olur ve bunlar, kodun değerlendirildiği modülün global kapsamı içinde nihayetinde iç içe geçmiş olur. Dıştaki kapsamda bulunan değişkenler, içerdiği herhangi bir kapsamdan görünür — bu, içteki kapsamda okunup yazılabileceği anlamına gelir — aynı isimde bir yerel değişkenin dıştaki aynı isimdeki değişkeni "gölgelemesi" durumu hariç. Bu, dıştaki yerelin, bir iç bloktan sonra (metin olarak aşağıda) tanımlanmış olsa bile doğrudur. Bir değişkenin belirli bir kapsamda "var" olduğunu söylediğimizde, bu, o isimde bir değişkenin mevcut kapsamın içinde bulunduğu herhangi bir kapsamda var olduğu anlamına gelir, mevcut kapsam da dahil.

Bazı programlama dilleri, yeni değişkenleri kullanmadan önce açıkça tanımlamayı gerektirir. Açık tanım, Julia'da da çalışır: herhangi bir yerel kapsamda, `local x` yazmak, o kapsamda yeni bir yerel değişken tanımlar; dış kapsamda `x` adında bir değişken olup olmadığına bakılmaksızın. Ancak, her yeni değişkeni bu şekilde tanımlamak bir miktar ayrıntılı ve sıkıcıdır, bu nedenle Julia, birçok diğer dil gibi, zaten var olmayan bir değişken adına atama yapmayı o değişkeni örtük olarak tanımlamak olarak kabul eder. Mevcut kapsam global ise, yeni değişken globaldir; mevcut kapsam yerel ise, yeni değişken en içteki yerel kapsamda yereldir ve o kapsam içinde görünür, ancak dışarıda görünmez. Mevcut bir yerel değişkene atama yaparsanız, bu *her zaman* mevcut yerel değişkeni günceller: bir yereli gölgede bırakmak için, `local` anahtar kelimesi ile iç içe bir kapsamda yeni bir yerel değişken açıkça tanımlamanız gerekir. Özellikle, bu durum iç fonksiyonlarda atanan değişkenler için geçerlidir; bu, Python'dan gelen kullanıcıları şaşırtabilir, çünkü iç bir fonksiyonda atama yapmak, değişken açıkça dışsal olarak tanımlanmadıkça yeni bir yerel değişken oluşturur.

Genellikle bu oldukça sezgisel, ancak sezgisel davranan birçok şeyde olduğu gibi, detaylar birinin safça hayal edebileceğinden daha inceliklidir.

`x = <değer>` ifadesi yerel bir kapsamda gerçekleştiğinde, Julia aşağıdaki kuralları uygular; bu kurallar, atama ifadesinin nerede gerçekleştiğine ve o konumda `x`'in neye atıfta bulunduğuna göre ifadenin ne anlama geldiğini belirler:

1. **Mevcut yerel:** Eğer `x` *zaten bir yerel değişkense*, o zaman mevcut yerel `x` atanır;
2. **Sert bir kapsam:** Eğer `x` *zaten yerel bir değişken değilse* ve atama herhangi bir sert kapsam yapısının içinde gerçekleşiyorsa (yani bir `let` bloğu, fonksiyon veya makro gövdesi, anlama veya jeneratör içinde), atamanın kapsamı içinde yeni bir yerel `x` adıyla değişken oluşturulur;
3. **Yumuşak kapsam:** Eğer `x` *zaten yerel bir değişken değilse* ve atamayı içeren tüm kapsam yapıları yumuşak kapsamlar (döngüler, `try`/`catch` blokları veya `struct` blokları) ise, davranış, küresel değişken `x`'in tanımlı olup olmamasına bağlıdır:

      * eğer global `x` *tanımsızsa*, atama kapsamına yeni bir yerel `x` oluşturulur;
      * eğer global `x` *tanımlıysa*, atama belirsiz olarak kabul edilir:

          * *etkileşimli olmayan* bağlamlarda (dosyalar, eval), bir belirsizlik uyarısı yazdırılır ve yeni bir yerel oluşturulur;
          * *etkileşimli* bağlamlarda (REPL, defterler), global değişken `x` atanır.

Non-interaktif bağlamlarda, sert ve yumuşak kapsam davranışlarının, bir küresel değişkeni gölgeleyen (yani `local x` ile tanımlanmamış) örtük yerel bir değişkenin uyarı vermesi dışında, aynı olduğunu not edebilirsiniz. Etkileşimli bağlamlarda, kurallar kolaylık sağlamak amacıyla daha karmaşık bir sezgiye uyar. Bu, takip eden örneklerde derinlemesine ele alınmaktadır.

Artık kuralları bildiğinize göre, bazı örneklere bakalım. Her örneğin, yalnızca o kod bloğunda atanan küresel değişkenlerin bulunduğu yeni bir REPL oturumunda değerlendirileceği varsayılmaktadır.

Bir fonksiyon gövdesi gibi katı bir kapsam içinde, o isimde zaten mevcut bir yerel değişken olmadığında, güzel ve net bir durumla başlayacağız:

```jldoctest
julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
ERROR: UndefVarError: `x` not defined in `Main`
```

`greet` fonksiyonu içinde, `x = "hello"` ataması `x`'in fonksiyonun kapsamındaki yeni bir yerel değişken olmasına neden olur. İki ilgili gerçek vardır: atama yerel kapsamda gerçekleşir ve mevcut bir yerel `x` değişkeni yoktur. `x` yerel olduğu için, global olarak adlandırılmış bir `x` olup olmaması önemli değildir. Burada örneğin, `greet` fonksiyonunu tanımlamadan ve çağırmadan önce `x = 123` tanımlıyoruz:

```jldoctest
julia> x = 123 # global
123

julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
123
```

`greet` içindeki `x` yereldir, bu nedenle `greet` çağrıldığında global `x`'in değeri (veya yokluğu) etkilenmez. Sert kapsam kuralı, global olarak adlandırılan bir `x`'in var olup olmamasını umursamaz: sert bir kapsamda `x`'e atama yapmak yereldir (eğer `x` global olarak ilan edilmemişse).

Göz önünde bulunduracağımız bir sonraki net durum, zaten `x` adında bir yerel değişkenin olduğu durumdur; bu durumda `x = <değer>` her zaman mevcut yerel `x`'e atama yapar. Bu, atamanın aynı yerel kapsamda, aynı işlev gövdesindeki bir iç yerel kapsamda veya başka bir işlevin gövdesinde yer alan bir işlevin içinde gerçekleşip gerçekleşmediğine bakılmaksızın doğrudur; bu da [closure](https://en.wikipedia.org/wiki/Closure_(computer_programming)) olarak bilinir.

`sum_to` fonksiyonunu kullanacağız, bu fonksiyon `1`'den `n`'ye kadar olan tam sayıların toplamını hesaplar, bir örnek olarak:

```julia
function sum_to(n)
    s = 0 # new local
    for i = 1:n
        s = s + i # assign existing local
    end
    return s # same local
end
```

`sum_to` fonksiyonunun gövdesinde `s`'ye yapılan ilk atama, `s`'yi yeni bir yerel değişken haline getirir. `for` döngüsü, fonksiyon kapsamı içinde kendi iç yerel kapsamına sahiptir. `s = s + i` ifadesinin gerçekleştiği noktada, `s` zaten bir yerel değişken olduğundan, atama mevcut `s`'yi günceller, yeni bir yerel değişken oluşturmaz. Bunu REPL'de `sum_to`'yu çağırarak test edebiliriz:

```jldoctest
julia> function sum_to(n)
           s = 0 # new local
           for i = 1:n
               s = s + i # assign existing local
           end
           return s # same local
       end
sum_to (generic function with 1 method)

julia> sum_to(10)
55

julia> s # global
ERROR: UndefVarError: `s` not defined in `Main`
```

`sum_to` fonksiyonu için `s` yereldir, bu nedenle fonksiyonu çağırmak küresel değişken `s` üzerinde hiçbir etkiye sahip değildir. Ayrıca, `for` döngüsündeki `s = s + i` güncellemesinin, `s = 0` ile yapılan başlangıçta oluşturulan aynı `s`'yi güncellediğini görebiliriz, çünkü 1'den 10'a kadar olan tam sayılar için doğru toplam olan 55'i alıyoruz.

Bir saniye için `for` döngüsü gövdesinin kendi kapsamı olduğunu inceleyelim ve buna `sum_to_def` adını vereceğimiz biraz daha ayrıntılı bir varyasyon yazalım. Burada `s + i` toplamını `s`'yi güncellemeden önce `t` adlı bir değişkende saklayacağız:

```jldoctest
julia> function sum_to_def(n)
           s = 0 # new local
           for i = 1:n
               t = s + i # new local `t`
               s = t # assign existing local `s`
           end
           return s, @isdefined(t)
       end
sum_to_def (generic function with 1 method)

julia> sum_to_def(10)
(55, false)
```

Bu sürüm, daha önce olduğu gibi `s` döndürür, ancak aynı zamanda fonksiyonun en dıştaki yerel kapsamında tanımlı bir yerel değişken olan `t` olup olmadığını belirten bir boolean döndürmek için `@isdefined` makrosunu kullanır. Gördüğünüz gibi, `for` döngüsü gövdesinin dışında tanımlı bir `t` yok. Bunun nedeni yine sert kapsam kuralıdır: `t`'ye atama, bir fonksiyonun içinde gerçekleştiğinden, bu sert kapsamı tanıtır ve atama, göründüğü yerel kapsamda yeni bir yerel değişken olan `t`'yi oluşturur, yani döngü gövdesinin içinde. Eğer global olarak tanımlı bir `t` olsaydı, bu fark etmezdi—sert kapsam kuralı global kapsamda olan hiçbir şeyden etkilenmez.

Dikkat edin ki, bir for döngüsü gövdesinin yerel kapsamı, bir iç fonksiyonun yerel kapsamından farksızdır. Bu, bu örneği, döngü gövdesinin bir iç yardımcı fonksiyon çağrısı olarak uygulanacak şekilde yeniden yazabileceğimiz anlamına gelir ve aynı şekilde davranır:

```jldoctest
julia> function sum_to_def_closure(n)
           function loop_body(i)
               t = s + i # new local `t`
               s = t # assign same local `s` as below
           end
           s = 0 # new local
           for i = 1:n
               loop_body(i)
           end
           return s, @isdefined(t)
       end
sum_to_def_closure (generic function with 1 method)

julia> sum_to_def_closure(10)
(55, false)
```

Bu örnek birkaç önemli noktayı göstermektedir:

1. İç fonksiyon kapsamları, diğer yerel iç içe kapsamlar gibi çalışır. Özellikle, bir değişken dışarıda bir iç fonksiyonun dışında zaten yerel ise ve iç fonksiyonda ona atama yaparsanız, dıştaki yerel değişken güncellenir.
2. Dış yerel bir tanımın güncellendiği yerin altında olup olmaması önemli değildir, kural aynı kalır. Tüm kapsayıcı yerel kapsam analiz edilir ve iç yerel anlamlar çözülmeden önce yerel değişkenler belirlenir.

Bu tasarım, genel olarak bir iç işlevin içine veya dışına kod taşıyabileceğiniz anlamına gelir; bu da kapamaları kullanarak dildeki birçok yaygın deyimi kolaylaştırır (bkz. [do blocks](@ref Do-Block-Syntax-for-Function-Arguments)).

Daha belirsiz durumlara geçelim, yumuşak kapsam kuralı tarafından kapsanan. Bunu, `greet` ve `sum_to_def` fonksiyonlarının gövdelerini yumuşak kapsam bağlamlarına çıkararak keşfedeceğiz. Öncelikle, `greet` fonksiyonunun gövdesini bir `for` döngüsüne koyarak—sert değil, yumuşak—ve REPL'de değerlendirelim:

```jldoctest
julia> for i = 1:3
           x = "hello" # new local
           println(x)
       end
hello
hello
hello

julia> x
ERROR: UndefVarError: `x` not defined in `Main`
```

Küresel `x` tanımlı olmadığından, `for` döngüsü değerlendirildiğinde, yumuşak kapsam kuralının ilk maddesi geçerlidir ve `x` döngüye özgü olarak oluşturulur, bu nedenle küresel `x` döngü çalıştıktan sonra tanımsız kalır. Şimdi, `sum_to_def` fonksiyonunun gövdesini küresel kapsamda ele alalım ve argümanını `n = 10` olarak sabitleyelim.

```julia
s = 0
for i = 1:10
    t = s + i
    s = t
end
s
@isdefined(t)
```

Bu kod ne yapar? İpucu: bu bir hile sorusu. Cevap "duruma bağlı." Bu kod etkileşimli olarak girildiğinde, bir işlev gövdesinde olduğu gibi davranır. Ancak kod bir dosyada yer alıyorsa, bir belirsizlik uyarısı verir ve tanımsız değişken hatası fırlatır. Önce REPL'de nasıl çalıştığını görelim:

```jldoctest
julia> s = 0 # global
0

julia> for i = 1:10
           t = s + i # new local `t`
           s = t # assign global `s`
       end

julia> s # global
55

julia> @isdefined(t) # global
false
```

REPL, bir fonksiyonun gövdesinde olmayı, döngü içindeki atamanın bir küresel değişkene mi yoksa yeni bir yerel değişken mi oluşturduğuna karar vererek yaklaşık olarak simüle eder. Eğer o isimde bir küresel değişken tanımlıysa, atama onu günceller. Eğer küresel yoksa, atama yeni bir yerel değişken oluşturur. Bu örnekte her iki durumu da eylemde görüyoruz:

  * Küresel bir `t` yok, bu yüzden `t = s + i` ifadesi `for` döngüsüne özgü yeni bir `t` oluşturur;
  * Küresel bir `s` var, bu yüzden `s = t` ona atama yapar.

İkinci gerçek, döngünün `s`'nin küresel değerini neden değiştirdiğidir ve birinci gerçek, döngü çalıştıktan sonra `t`'nin neden hala tanımsız olduğudur. Şimdi, bu aynı kodu bir dosyada varmış gibi değerlendirmeye çalışalım:

```jldoctest
julia> code = """
       s = 0 # global
       for i = 1:10
           t = s + i # new local `t`
           s = t # new local `s` with warning
       end
       s, # global
       @isdefined(t) # global
       """;

julia> include_string(Main, code)
┌ Warning: Assignment to `s` in soft scope is ambiguous because a global variable by the same name exists: `s` will be treated as a new local. Disambiguate by using `local s` to suppress this warning or `global s` to assign to the existing global variable.
└ @ string:4
ERROR: LoadError: UndefVarError: `s` not defined in local scope
```

Burada [`include_string`](@ref) kullanarak `code`'u bir dosyanın içeriğiymiş gibi değerlendiriyoruz. `code`'u bir dosyaya kaydedip ardından o dosyayı `include` ile çağırmak da aynı sonucu verecektir. Gördüğünüz gibi, bu, aynı kodu REPL'de değerlendirirken oldukça farklı bir davranış sergiliyor. Şimdi burada neler olduğunu inceleyelim:

  * global `s` döngü değerlendirilmeden önce `0` değeri ile tanımlanmıştır.
  * atama `s = t` yumuşak bir kapsamda—herhangi bir işlev gövdesinin veya başka bir sert kapsam yapısının dışında bir `for` döngüsünde gerçekleşir.
  * bu nedenle yumuşak kapsam kuralının ikinci maddesi uygulanır ve atama belirsizdir, bu yüzden bir uyarı verilir.
  * çalışma devam ediyor, `s`'yi `for` döngüsü gövdesine yerel hale getiriyor
  * `for` döngüsüne özgü olduğu için `s` tanımsızdır, bu da `t = s + i` ifadesi değerlendirildiğinde bir hata oluşmasına neden olur.
  * değerlendirme orada durur, ancak `s` ve `@isdefined(t)`'ye ulaşırsa, `0` ve `false` döner.

Bu, kapsamın bazı önemli yönlerini gösterir: bir kapsamda, her değişkenin yalnızca bir anlamı olabilir ve bu anlam, ifadelerin sırasından bağımsız olarak belirlenir. Döngüdeki `s = t` ifadesinin varlığı, `s`'nin döngüye özgü olmasına neden olur; bu, `t = s + i` ifadesinin sağ tarafında yer aldığında da yerel olduğu anlamına gelir, oysa bu ifade ilk olarak görünür ve ilk olarak değerlendirilir. Döngünün ilk satırındaki `s`'nin küresel, döngünün ikinci satırındaki `s`'nin ise yerel olabileceğini hayal edebilirsiniz, ancak bu mümkün değildir çünkü iki satır aynı kapsam bloğundadır ve her değişkenin belirli bir kapsamda yalnızca bir anlamı olabilir.

#### [On Soft Scope](@id on-soft-scope)

Artık tüm yerel kapsam kurallarını ele aldık, ancak bu bölümü kapatmadan önce, belirsiz yumuşak kapsam durumunun etkileşimli ve etkileşimli olmayan bağlamlarda neden farklı şekilde ele alındığı hakkında birkaç kelime söylenmelidir. Sorulabilecek iki belirgin soru var:

1. Neden her yerde REPL gibi çalışmıyor?
2. Neden her yerdeki dosyalar gibi çalışmıyor? Ve belki uyarıyı atlayabilir miyiz?

Julia ≤ 0.6'da, tüm global kapsamlar mevcut REPL gibi çalışıyordu: `x = <değer>` bir döngüde (veya `try`/`catch`, veya `struct` gövdesinde) ancak bir fonksiyon gövdesinin (veya `let` bloğunun veya anlama'nın) dışında gerçekleştiğinde, `x`'in döngüye yerel olup olmayacağı, global olarak tanımlı bir `x` olup olmadığına bağlı olarak belirleniyordu. Bu davranış, bir fonksiyon gövdesi içindeki davranışı mümkün olduğunca yakından taklit ettiğinden, sezgisel ve kullanışlı olma avantajına sahiptir. Özellikle, bir fonksiyonun davranışını hata ayıklarken kodu bir fonksiyon gövdesi ile REPL arasında kolayca taşımayı sağlar. Ancak, bazı dezavantajları vardır. Öncelikle, oldukça karmaşık bir davranıştır: yıllar içinde birçok insan bu davranıştan kafası karışmış ve bunun karmaşık ve hem açıklaması hem de anlaşılması zor olduğunu şikayet etmiştir. Adil bir nokta. İkincisi ve belki de daha kötü olanı, "ölçekli programlama" için kötü olmasıdır. Burada olduğu gibi bir yerde küçük bir kod parçası gördüğünüzde, ne olduğunu anlamak oldukça açıktır:

```julia
s = 0
for i = 1:10
    s += i
end
```

Açıkça niyet, mevcut küresel değişken `s`'yi değiştirmektir. Başka ne anlama gelebilir ki? Ancak, gerçek dünya kodu her zaman bu kadar kısa veya net değildir. Aşağıdaki gibi kodların sıkça karşılaşıldığını bulduk:

```julia
x = 123

# much later
# maybe in a different file

for i = 1:10
    x = "hello"
    println(x)
end

# much later
# maybe in yet another file
# or maybe back in the first one where `x = 123`

y = x + 234
```

Burada ne olacağına dair çok daha az netlik var. `x + "hello"` bir yöntem hatası olduğundan, `x`'in `for` döngüsüne özgü olması niyetinin olası olduğu görülüyor. Ancak çalışma zamanı değerleri ve hangi yöntemlerin mevcut olduğu, değişkenlerin kapsamlarını belirlemek için kullanılamaz. Julia ≤ 0.6 davranışı ile, birinin `for` döngüsünü önce yazmış olması, bunun düzgün çalışması, ancak daha sonra başka birinin uzakta, muhtemelen farklı bir dosyada yeni bir global eklemesi durumunda, kodun aniden anlamının değişmesi ve ya gürültülü bir şekilde bozulması ya da daha kötüsü, sessizce yanlış bir şey yapması konusunda özellikle endişe vericidir. Bu tür bir ["spooky action at a distance"](https://en.wikipedia.org/wiki/Action_at_a_distance_(computer_programming)) iyi programlama dili tasarımlarının önlemesi gereken bir durumdur.

Bu nedenle Julia 1.0'da kapsam kurallarını basitleştirdik: herhangi bir yerel kapsamda, zaten yerel bir değişken olmayan bir isme atama yapmak yeni bir yerel değişken oluşturuyordu. Bu, yumuşak kapsam kavramını tamamen ortadan kaldırdı ve korkutucu eylem potansiyelini de kaldırdı. Yumuşak kapsamın kaldırılması nedeniyle önemli sayıda hatayı ortaya çıkardık ve düzelttik, bu da ondan kurtulma seçimini haklı çıkardı. Ve çok sevinç vardı! Aslında, hayır, pek değil. Çünkü bazı insanlar artık şunları yazmak zorunda oldukları için kızgındılar:

```julia
s = 0
for i = 1:10
    global s += i
end
```

O `global` notasyonu orada mı? Çirkin. Bu durumun tolere edilemeyeceği aşikar. Ama cidden, bu tür üst düzey kod için `global` gerektirmekte iki ana sorun var:

1. Artık bir işlev gövdesinin içindeki kodu REPL'e kopyalayıp yapıştırmak pratik değil - `global` açıklamaları eklemeniz ve ardından geri dönmek için bunları kaldırmanız gerekiyor;
2. Yeni başlayanlar bu tür kodları `global` olmadan yazacaklar ve kodlarının neden çalışmadığını anlamayacaklar—aldıkları hata, `s`'nin tanımsız olduğu ve bu hatayı yapan hiç kimseyi aydınlatmıyor gibi görünüyor.

Julia 1.5 itibarıyla, bu kod etkileşimli bağlamlarda, REPL veya Jupyter defterleri gibi (tıpkı Julia 0.6'da olduğu gibi) `global` notasyonu olmadan çalışır ve dosyalarda ve diğer etkileşimli olmayan bağlamlarda, bu çok doğrudan uyarıyı yazdırır:

> `soft` kapsamındaki `s`'ye atama, aynı isimde bir global değişken bulunduğu için belirsizdir: `s`, yeni bir yerel değişken olarak kabul edilecektir. Bu uyarıyı bastırmak için `local s` kullanarak ya da mevcut global değişkene atama yapmak için `global s` kullanarak belirsizliği giderebilirsiniz.


Bu, hem "ölçekli programlama" 1.0 davranışının faydalarını korurken her iki sorunu da ele alır: global değişkenler, uzakta olabilecek kodun anlamı üzerinde korkutucu bir etkiye sahip değildir; REPL'de kopyala-yapıştır hata ayıklama çalışır ve acemilerin herhangi bir sorunu yoktur; birisi ya bir `global` notasyonunu unuttuğunda ya da mevcut bir globali yumuşak bir kapsamda yerel bir değişkenle yanlışlıkla gölgelettiğinde, ki bu zaten kafa karıştırıcı olur, net bir uyarı alırlar.

Bu tasarımın önemli bir özelliği, bir dosyada uyarı olmadan çalışan herhangi bir kodun, yeni bir REPL'de aynı şekilde davranacağıdır. Ve tersine, eğer bir REPL oturumunu alıp dosyaya kaydederseniz, eğer REPL'deki gibi davranmıyorsa, o zaman bir uyarı alırsınız.

### Let Blocks

`let` ifadeleri her çalıştıklarında yeni bir *sert kapsam* bloğu oluşturur (yukarıya bakın) ve her seferinde yeni değişken bağlamaları tanıtır. Değişken hemen atanmak zorunda değildir:

```jldoctest
julia> var1 = let x
           for i in 1:5
               (i == 4) && (x = i; break)
           end
           x
       end
4
```

Mevcut bir değer konumuna yeni bir değer atamak için atamalar yeniden atama yapabilirken, `let` her zaman yeni bir konum oluşturur. Bu fark genellikle önemli değildir ve yalnızca kapsamlarını aşan değişkenler için kapamalar aracılığıyla tespit edilebilir. `let` sözdizimi, virgülle ayrılmış bir dizi atama ve değişken adı kabul eder:

```jldoctest
julia> x, y, z = -1, -1, -1;

julia> let x = 1, z
           println("x: $x, y: $y") # x is local variable, y the global
           println("z: $z") # errors as z has not been assigned yet but is local
       end
x: 1, y: -1
ERROR: UndefVarError: `z` not defined in local scope
```

Atamalar sırasıyla değerlendirilir; sağdaki her ifade, soldaki yeni değişken tanıtılmadan önceki kapsamda değerlendirilir. Bu nedenle, `let x = x` gibi bir şey yazmak mantıklıdır çünkü iki `x` değişkeni ayrıdır ve ayrı depolama alanlarına sahiptir. İşte `let`'in davranışının gerekli olduğu bir örnek:

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           Fs[i] = ()->i
           global i += 1
       end

julia> Fs[1]()
3

julia> Fs[2]()
3
```

Burada `i` değişkenini döndüren iki kapanış oluşturuyor ve saklıyoruz. Ancak, her zaman aynı `i` değişkeni olduğu için iki kapanış da aynı şekilde davranır. `i` için yeni bir bağlama oluşturmak üzere `let` kullanabiliriz:

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           let i = i
               Fs[i] = ()->i
           end
           global i += 1
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

`begin` yapısı yeni bir kapsam tanımlamadığı için, hemen yeni bağlamlar oluşturmadan sadece yeni bir kapsam bloğu tanıtmak için sıfır argümanlı bir `let` kullanmak faydalı olabilir:

```jldoctest
julia> let
           local x = 1
           let
               local x = 2
           end
           x
       end
1
```

`let` yeni bir kapsam bloğu tanıttığı için, içteki yerel `x`, dıştaki yerel `x`'ten farklı bir değişkendir. Bu özel örnek şuna eşdeğerdir:

```jldoctest
julia> let x = 1
           let x = 2
           end
           x
       end
1
```

### Loops and Comprehensions

In loops and [comprehensions](@ref man-comprehensions), new variables introduced in their body scopes are freshly allocated for each loop iteration, as if the loop body were surrounded by a `let` block, as demonstrated by this example:

```jldoctest
julia> Fs = Vector{Any}(undef, 2);

julia> for j = 1:2
           Fs[j] = ()->j
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

Bir `for` döngüsü veya anlama yineleme değişkeni her zaman yeni bir değişkendir:

```julia-repl enable_doctest_when_deprecation_warning_is_removed
julia> function f()
           i = 0
           for i = 1:3
               # empty
           end
           return i
       end;

julia> f()
0
```

Ancak, mevcut bir yerel değişkeni yineleme değişkeni olarak yeniden kullanmak bazen faydalı olabilir. Bu, `outer` anahtar kelimesini ekleyerek rahatlıkla yapılabilir:

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # empty
           end
           return i
       end;

julia> f()
3
```

## Constants

Değişkenlerin yaygın bir kullanımı, belirli, değişmeyen değerlere isim vermektir. Bu tür değişkenler yalnızca bir kez atanır. Bu niyet, derleyiciye [`const`](@ref) anahtar kelimesi kullanılarak iletilebilir:

```jldoctest
julia> const e  = 2.71828182845904523536;

julia> const pi = 3.14159265358979323846;
```

Birden fazla değişken tek bir `const` ifadesinde tanımlanabilir:

```jldoctest
julia> const a, b = 1, 2
(1, 2)
```

`const` bildirimi yalnızca küresel kapsamda küreseller üzerinde kullanılmalıdır. Küresel değişkenlerle ilgili kodu optimize etmek derleyici için zordur, çünkü değerleri (veya hatta türleri) neredeyse her an değişebilir. Eğer bir küresel değişken değişmeyecekse, bir `const` bildirimi eklemek bu performans sorununu çözer.

Yerel sabitler oldukça farklıdır. Derleyici, bir yerel değişkenin sabit olup olmadığını otomatik olarak belirleyebilir, bu nedenle yerel sabit bildirimleri gerekli değildir ve aslında şu anda desteklenmemektedir.

Özel üst düzey atamalar, `function` ve `struct` anahtar kelimeleri gibi, varsayılan olarak sabittir.

`const` yalnızca değişken bağlamasını etkiler; değişken, değiştirilebilir bir nesneye (örneğin bir dizi) bağlanabilir ve o nesne hala değiştirilebilir. Ayrıca, bir sabit olarak tanımlanan bir değişkene bir değer atamaya çalışıldığında aşağıdaki senaryolar mümkündür:

  * eğer yeni bir değer, sabitin türünden farklı bir türe sahipse, bir hata fırlatılır:

```jldoctest
julia> const x = 1.0
1.0

julia> x = 1
ERROR: invalid redefinition of constant x
```

  * eğer yeni bir değer sabit ile aynı türe sahipse, bir uyarı yazdırılır:

```jldoctest
julia> const y = 1.0
1.0

julia> y = 2.0
WARNING: redefinition of constant y. This may fail, cause incorrect answers, or produce other errors.
2.0
```

  * eğer bir atama değişken değerinin değişmesine neden olmuyorsa, hiçbir mesaj verilmez:

```jldoctest
julia> const z = 100
100

julia> z = 100
100
```

Son kural, değişken bağlaması değişse bile, değiştirilemez nesnelere uygulanır; örneğin:

```julia-repl
julia> const s1 = "1"
"1"

julia> s2 = "1"
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x00000000132c9638
 Ptr{UInt8} @0x0000000013dd3d18

julia> s1 = s2
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x0000000013dd3d18
 Ptr{UInt8} @0x0000000013dd3d18
```

Ancak, değiştirilebilir nesneler için uyarı beklendiği gibi yazdırılır:

```jldoctest
julia> const a = [1]
1-element Vector{Int64}:
 1

julia> a = [1]
WARNING: redefinition of constant a. This may fail, cause incorrect answers, or produce other errors.
1-element Vector{Int64}:
 1
```

Not edin ki, bazen mümkün olsa da, bir `const` değişkeninin değerini değiştirmek şiddetle tavsiye edilmez ve yalnızca etkileşimli kullanım sırasında kolaylık sağlamak için tasarlanmıştır. Sabitleri değiştirmek çeşitli sorunlara veya beklenmedik davranışlara neden olabilir. Örneğin, bir yöntem bir sabite atıfta bulunuyorsa ve sabit değiştirildikten sonra zaten derlenmişse, o zaman eski değeri kullanmaya devam edebilir:

```jldoctest
julia> const x = 1
1

julia> f() = x
f (generic function with 1 method)

julia> f()
1

julia> x = 2
WARNING: redefinition of constant x. This may fail, cause incorrect answers, or produce other errors.
2

julia> f()
1
```

## [Typed Globals](@id man-typed-globals)

!!! compat "Julia 1.8"
    Julia 1.8'de tipli global değişkenler için destek eklendi.


Sabitler olarak ilan edilmekle benzer şekilde, küresel bağlamalar da her zaman sabit bir türde olacağı şekilde ilan edilebilir. Bu, ya `global x::T` sözdizimini kullanarak gerçek bir değer atamadan yapılabilir ya da atama sırasında `x::T = 123` şeklinde yapılabilir.

```jldoctest
julia> x::Float64 = 2.718
2.718

julia> f() = x
f (generic function with 1 method)

julia> Base.return_types(f)
1-element Vector{Any}:
 Float64
```

Herhangi bir atama için, Julia önce bunu uygun türe dönüştürmeye çalışacaktır [`convert`](@ref):

```jldoctest
julia> global y::Int

julia> y = 1.0
1.0

julia> y
1

julia> y = 3.14
ERROR: InexactError: Int64(3.14)
Stacktrace:
[...]
```

Tipin somut olması gerekmez, ancak soyut türlerle yapılan anotasyonların genellikle çok az performans faydası vardır.

Bir global ya birine atanmış ya da türü belirlenmişse, bağlama türünün değişmesine izin verilmez:

```jldoctest
julia> x = 1
1

julia> global x::Int
ERROR: cannot set type for global x. It already has a value or is already set to a different type.
Stacktrace:
[...]
```
