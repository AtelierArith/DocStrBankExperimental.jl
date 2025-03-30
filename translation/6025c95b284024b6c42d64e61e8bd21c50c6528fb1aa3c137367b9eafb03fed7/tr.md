# Noteworthy Differences from other Languages

## Noteworthy differences from MATLAB

MATLAB kullanıcıları Julia'nın sözdizimini tanıdık bulsalar da, Julia bir MATLAB klonu değildir. Önemli sözdizimsel ve işlevsel farklılıklar vardır. Aşağıda, MATLAB'a alışkın Julia kullanıcılarını zorlayabilecek bazı dikkate değer farklılıklar bulunmaktadır:

  * Julia dizileri köşeli parantezlerle indekslenir, `A[i,j]`.
  * Julia dizileri başka bir değişkene atandığında kopyalanmaz. `A = B` sonrasında `B`'nin elemanlarını değiştirmek, `A`'yı da değiştirecektir. Bunu önlemek için `A = copy(B)` kullanın.
  * Julia değerleri bir fonksiyona geçirildiğinde kopyalanmaz. Eğer bir fonksiyon bir diziyi değiştirirse, değişiklikler çağıran yerde görünür olacaktır.
  * Julia, otomatik olarak bir atama ifadesinde dizileri büyütmez. MATLAB'da `a(4) = 3.2` ifadesi `a = [0 0 0 3.2]` dizisini oluşturabilir ve `a(5) = 7` ifadesi bunu `a = [0 0 0 3.2 7]` haline getirebilirken, karşılık gelen Julia ifadesi `a[5] = 7` eğer `a`'nın uzunluğu 5'ten azsa veya bu ifade `a` tanımlayıcısının ilk kullanımıysa bir hata verir. Julia, MATLAB'ın `a(end+1) = val` ifadesinden çok daha verimli bir şekilde `Vector`'ları büyüten [`push!`](@ref) ve [`append!`](@ref)'ya sahiptir.
  * Hayali birim `sqrt(-1)`, Julia'da [`im`](@ref) olarak temsil edilir, MATLAB'daki `i` veya `j` yerine.
  * Julia'da ondalık noktası olmayan literal sayılar (örneğin `42`) tam sayılar oluşturur, kayan nokta sayıları yerine. Sonuç olarak, bazı işlemler bir float bekliyorsa bir alan hatası verebilir; örneğin, `julia> a = -1; 2^a` bir alan hatası verir, çünkü sonuç bir tam sayı değildir (detaylar için [the FAQ entry on domain errors](@ref faq-domain-errors)'e bakın).
  * Julia'da birden fazla değer döndürülür ve demetler olarak atanır, örneğin `(a, b) = (1, 2)` veya `a, b = 1, 2`. MATLAB'daki `nargout`, genellikle döndürülen değerlerin sayısına dayalı olarak isteğe bağlı işler yapmak için kullanılır, ancak Julia'da yoktur. Bunun yerine, kullanıcılar benzer yetenekleri elde etmek için isteğe bağlı ve anahtar kelime argümanlarını kullanabilirler.
  * Julia, gerçek bir boyutlu dizilere sahiptir. Sütun vektörleri `N` boyutundadır, `Nx1` değil. Örneğin, [`rand(N)`](@ref) 1 boyutlu bir dizi oluşturur.
  * Julia'da, `[x,y,z]` her zaman `x`, `y` ve `z` içeren 3 elemanlı bir dizi oluşturur.

      * İlk ("dikey") boyutta birleştirmek için ya [`vcat(x,y,z)`](@ref) kullanın ya da noktalı virgülle ayırın (`[x; y; z]`).
      * İkinci ("yatay") boyutta birleştirmek için ya [`hcat(x,y,z)`](@ref) kullanın ya da boşluklarla ayırın (`[x y z]`).
      * Blok matrisleri oluşturmak için (ilk iki boyutta birleştirerek), ya [`hvcat`](@ref) kullanın ya da boşluklar ve noktalı virgülleri birleştirin (`[a b; c d]`).
  * Julia'da, `a:b` ve `a:b:c` `AbstractRange` nesneleri oluşturur. MATLAB'daki gibi tam bir vektör oluşturmak için [`collect(a:b)`](@ref) kullanın. Genel olarak, `collect` çağırmaya gerek yoktur. Bir `AbstractRange` nesnesi çoğu durumda normal bir dizi gibi davranır, ancak değerlerini tembel bir şekilde hesapladığı için daha verimlidir. Tam diziler yerine özel nesneler oluşturma kalıbı sıkça kullanılır ve [`range`](@ref) gibi fonksiyonlarda veya `enumerate` ve `zip` gibi iteratörlerde de görülür. Özel nesneler çoğunlukla normal diziler gibi kullanılabilir.
  * Julia'daki fonksiyonlar, son ifadelerinden veya `return` anahtar kelimesinden değer döndürür; bu, fonksiyon tanımında döndürülecek değişkenlerin isimlerini listelemek yerine geçerlidir (detaylar için bkz. [The return Keyword](@ref)).
  * Bir Julia betiği herhangi bir sayıda fonksiyon içerebilir ve tüm tanımlar dosya yüklendiğinde dışarıdan görünür olacaktır. Fonksiyon tanımları, mevcut çalışma dizininden dışarıdaki dosyalardan da yüklenebilir.
  * Julia'da, `sum(A)` gibi tek bir argümanla çağrıldığında, [`sum`](@ref), [`prod`](@ref) ve [`maximum`](@ref) gibi azaltmalar, bir dizinin her bir elemanı üzerinde gerçekleştirilir, A'nın birden fazla boyutu olsa bile.
  * Julia'da, sıfır argümanlı bir fonksiyonu çağırmak için parantezler kullanılmalıdır, örneğin [`rand()`](@ref).
  * Julia, ifadelerin sonunu noktalı virgül ile bitirmeyi teşvik etmez. İfadelerin sonuçları otomatik olarak yazdırılmaz (etkileşimli istemci dışında) ve kod satırlarının noktalı virgül ile bitirilmesi gerekmez. [`println`](@ref) veya [`@printf`](@ref) belirli bir çıktıyı yazdırmak için kullanılabilir.
  * Julia'da, `A` ve `B` dizileri varsa, mantıksal karşılaştırma işlemleri `A == B` gibi bir dizi boolean döndürmez. Bunun yerine, `A .== B` kullanın ve benzer şekilde diğer boolean operatörleri için de [`<`](@ref), [`>`](@ref) kullanın.
  * Julia'da [`&`](@ref), [`|`](@ref) ve [`⊻`](@ref xor) ([`xor`](@ref)) operatörleri, MATLAB'daki `and`, `or` ve `xor` işlemlerine karşılık gelen bit düzeyindeki işlemleri gerçekleştirir ve öncelikleri Python'un bit düzeyindeki operatörleriyle benzerdir (C'den farklı olarak). Skalarlar üzerinde veya diziler arasında eleman bazında çalışabilirler ve mantıksal dizileri birleştirmek için kullanılabilirler, ancak işlem sırasındaki farkı not edin: parantezler gerekli olabilir (örneğin, `A`'nın 1 veya 2'ye eşit olan elemanlarını seçmek için `(A .== 1) .| (A .== 2)` kullanın).
  * Julia'da, bir koleksiyonun elemanları, `...` splat operatörü kullanılarak bir fonksiyona argüman olarak geçirilebilir; örneğin `xs=[1,2]; f(xs...)`.
  * Julia'nın [`svd`](@ref) tekil değerleri yoğun bir diagonal matris yerine bir vektör olarak döndürür.
  * Julia'da `...` kod satırlarını devam ettirmek için kullanılmaz. Bunun yerine, tamamlanmamış ifadeler otomatik olarak bir sonraki satıra devam eder.
  * Hem Julia hem de MATLAB'da, `ans` değişkeni etkileşimli bir oturumda verilen son ifadenin değerine ayarlanır. Julia'da, MATLAB'ın aksine, Julia kodu etkileşimli olmayan modda çalıştırıldığında `ans` ayarlanmamaktadır.
  * Julia'nın `struct`ları, MATLAB'ın `class`ları gibi çalışma zamanında dinamik olarak alan eklemeyi desteklemez. Bunun yerine, bir [`Dict`](@ref) kullanın. Julia'daki Dict sıralı değildir.
  * Julia'da her modülün kendi küresel kapsamı/ad alanı vardır, oysa MATLAB'da sadece bir küresel kapsam vardır.
  * In MATLAB, istenmeyen değerleri kaldırmanın bir idiomatik yolu, `x(x>3)` ifadesi veya `x(x>3) = []` ifadesi gibi mantıksal dizinleme kullanmaktır; bu, `x`'i yerinde değiştirmek için kullanılır. Buna karşılık, Julia, kullanıcıların `filter(z->z>3, x)` ve `filter!(z->z>3, x)` yazmalarına olanak tanıyan [`filter`](@ref) ve [`filter!`](@ref) yüksek dereceli fonksiyonları sağlar; bu, karşılık gelen transliterasyonlar olan `x[x.>3]` ve `x = x[x.>3]` için alternatiflerdir. `4d61726b646f776e2e436f64652822222c202266696c746572212229_40726566` geçici dizilerin kullanımını azaltır.
  * Hücre dizisinin tüm elemanlarını çıkarmanın (veya "dereference" etmenin) analoğu, MATLAB'da `vertcat(A{:})` şeklinde yazılırken, Julia'da splat operatörü kullanılarak `vcat(A...)` şeklinde yazılır.
  * Julia'da `adjoint` fonksiyonu karmaşık transpozunu gerçekleştirir; MATLAB'da `adjoint`, kofaktör matrisinin transpozunu veren "adjugate" veya klasik adjoint'i sağlar.
  * Julia'da a^b^c ifadesi a^(b^c) olarak değerlendirilirken, MATLAB'da (a^b)^c şeklinde değerlendirilir.

## Noteworthy differences from R

Julia'nın hedeflerinden biri, veri analizi ve istatistiksel programlama için etkili bir dil sağlamaktır. R'den Julia'ya gelen kullanıcılar için bazı dikkate değer farklılıklar şunlardır:

  * Julia'nın tek tırnakları karakterleri, stringleri değil, kapsar.
  * Julia, dizgilerde indeksleme yaparak alt dizeler oluşturabilir. R'de, dizgiler alt dizeler oluşturulmadan önce karakter vektörlerine dönüştürülmelidir.
  * Julia'da, Python gibi ama R'den farklı olarak, dizeler üçlü tırnak işareti `""" ... """` ile oluşturulabilir. Bu sözdizimi, satır sonları içeren dizeleri oluşturmak için kullanışlıdır.
  * Julia'da varargs, belirli bir değişkenin adını takiben gelen splat operatörü `...` kullanılarak belirtilir; bu, R için geçerli değildir, çünkü R'de `...` yalnızca başıboş olarak yer alabilir.
  * Julia'da modül `mod(a, b)` şeklindedir, `a %% b` değil. Julia'da `%` kalanı hesaplama operatörüdür.
  * Julia, köşeli parantezler kullanarak vektörler oluşturur. Julia'nın `[1, 2, 3]` ifadesi, R'nın `c(1, 2, 3)` ifadesine eşdeğerdir.
  * Julia'da, tüm veri yapıları mantıksal indekslemeyi desteklemez. Ayrıca, Julia'da mantıksal indeksleme yalnızca indekslenen nesne ile aynı uzunlukta olan vektörlerle desteklenir. Örneğin:

      * R'de `c(1, 2, 3, 4)[c(TRUE, FALSE)]` ifadesi `c(1, 3)` ile eşdeğerdir.
      * R'de `c(1, 2, 3, 4)[c(TRUE, FALSE, TRUE, FALSE)]` ifadesi `c(1, 3)` ile eşdeğerdir.
      * In Julia, `[1, 2, 3, 4][[true, false]]` bir [`BoundsError`](@ref) hatası verir.
      * Julia'da, `[1, 2, 3, 4][[true, false, true, false]]` ifadesi `[1, 3]` sonucunu verir.
  * Diğer birçok dil gibi, Julia farklı uzunluktaki vektörler üzerinde her zaman işlem yapmaya izin vermez; oysa R'de vektörlerin yalnızca ortak bir indeks aralığına sahip olması gerekir. Örneğin, `c(1, 2, 3, 4) + c(1, 2)` geçerli bir R ifadesidir, ancak eşdeğeri `[1, 2, 3, 4] + [1, 2]` Julia'da bir hata verecektir.
  * Julia, kodun anlamını değiştirmediği durumlarda isteğe bağlı bir son virgül kullanımına izin verir. Bu, R kullanıcıları arasında dizilere indeksleme yaparken kafa karışıklığına neden olabilir. Örneğin, R'de `x[1,]` bir matrisin ilk satırını döndürür; ancak Julia'da virgül göz ardı edilir, bu nedenle `x[1,] == x[1]` olur ve ilk öğeyi döndürür. Bir satırı çıkarmak için `:` kullanmayı unutmayın, örneğin `x[1,:]`.
  * Julia'nın [`map`](@ref) fonksiyonu önce alır, ardından argümanlarını, R'deki `lapply(<yapı>, fonksiyon, ...)`'dan farklı olarak. Benzer şekilde, Julia'nın R'deki `apply(X, MARGIN, FUN, ...)` eşdeğeri [`mapslices`](@ref)'dır; burada fonksiyon ilk argümandır.
  * R'de çok değişkenli uygulama, örneğin `mapply(choose, 11:13, 1:3)`, Julia'da `broadcast(binomial, 11:13, 1:3)` olarak yazılabilir. Eşdeğer olarak, Julia, fonksiyonları vektörleştirmek için daha kısa bir nokta sözdizimi sunar: `binomial.(11:13, 1:3)`.
  * Julia, koşul bloklarının, döngü bloklarının ve fonksiyonların sonunu belirtmek için `end` kullanır. Tek satırlık `if ( cond ) statement` yerine, Julia `if cond; statement; end`, `cond && statement` ve `!cond || statement` biçimindeki ifadeleri kabul eder. Son iki sözdizimindeki atama ifadeleri, açıkça parantez içine alınmalıdır; örneğin, `cond && (x = value)`.
  * Julia'da `<-`, `<<-` ve `->` atama operatörleri değildir.
  * Julia'nın `->` ifadesi anonim bir fonksiyon oluşturur.
  * Julia'nın [`*`](@ref) operatörü, R'deki gibi matris çarpımı yapabilir. Eğer `A` ve `B` matrisleri ise, o zaman `A * B` ifadesi Julia'da matris çarpımını belirtir ve bu, R'deki `A %*% B` ifadesine eşdeğerdir. R'de bu aynı notasyon, eleman bazında (Hadamard) çarpım yapar. Eleman bazında çarpım işlemini elde etmek için Julia'da `A .* B` yazmanız gerekir.
  * Julia, `transpose` fonksiyonunu kullanarak matris transpozisyonu yapar ve konjuge transpozisyonu `'` operatörü veya `adjoint` fonksiyonu ile gerçekleştirir. Julia'nın `transpose(A)` fonksiyonu, R'nin `t(A)` fonksiyonuna eşdeğerdir. Ayrıca, Julia'da özyinelemeli olmayan bir transpozisyon `permutedims` fonksiyonu ile sağlanır.
  * Julia parantez gerektirmez `if` ifadeleri veya `for`/`while` döngüleri yazarken: `for i in [1, 2, 3]` yerine `for (i in c(1, 2, 3))` ve `if i == 1` yerine `if (i == 1)` kullanın.
  * Julia, `0` ve `1` sayıları Boole olarak kabul etmez. Julia'da `if (1)` yazamazsınız, çünkü `if` ifadeleri yalnızca boole değerlerini kabul eder. Bunun yerine `if true`, `if Bool(1)` veya `if 1==1` yazabilirsiniz.
  * Julia `nrow` ve `ncol` sağlamaz. Bunun yerine `nrow(M)` için `size(M, 1)` ve `ncol(M)` için `size(M, 2)` kullanın.
  * Julia, skalarlar, vektörler ve matrisleri ayırt etmekte dikkatlidir. R'de `1` ve `c(1)` aynıdır. Julia'da ise bunlar birbirinin yerine kullanılamaz.
  * Julia'nın [`diag`](@ref) ve [`diagm`](@ref) R'nin benzeri değildir.
  * Julia, atama işleminin sol tarafında fonksiyon çağrılarının sonuçlarına atama yapamaz: `diag(M) = fill(1, n)` yazamazsınız.
  * Julia, ana fonksiyonları ana ad alanına yerleştirmeyi teşvik etmez. Julia için çoğu istatistiksel işlevsellik [packages](https://pkg.julialang.org/) altında [JuliaStats organization](https://github.com/JuliaStats) bulunur. Örneğin:

      * Olasılık dağılımlarına ilişkin fonksiyonlar [Distributions package](https://github.com/JuliaStats/Distributions.jl) tarafından sağlanmaktadır.
      * [DataFrames package](https://github.com/JuliaData/DataFrames.jl) veri çerçeveleri sağlar.
      * Genelleştirilmiş lineer modeller [GLM package](https://github.com/JuliaStats/GLM.jl) tarafından sağlanmaktadır.
  * Julia, demetler ve gerçek hash tabloları sağlar, ancak R tarzı listeler sağlamaz. Birden fazla öğe döndürürken, genellikle bir demet veya adlandırılmış demet kullanmalısınız: `list(a = 1, b = 2)` yerine `(1, 2)` veya `(a=1, b=2)` kullanın.
  * Julia, kullanıcıların S3 veya S4 nesnelerinden daha kolay kullanılabilen kendi türlerini yazmalarını teşvik eder. Julia'nın çoklu dağıtım sistemi, `table(x::TypeA)` ve `table(x::TypeB)`'nin R'nin `table.TypeA(x)` ve `table.TypeB(x)` gibi davranması anlamına gelir.
  * Julia'da, değerler atandığında veya bir işleve geçirildiğinde kopyalanmaz. Bir işlev bir diziyi değiştirdiğinde, değişiklikler çağıran yerde görünür. Bu, R'den çok farklıdır ve yeni işlevlerin büyük veri yapıları üzerinde çok daha verimli bir şekilde çalışmasına olanak tanır.
  * In Julia, vektörler ve matrisler [`hcat`](@ref), [`vcat`](@ref) ve [`hvcat`](@ref) kullanılarak birleştirilir, R'deki gibi `c`, `rbind` ve `cbind` ile değil.
  * Julia'da `a:b` gibi bir aralık, R'deki gibi bir vektör için kısayol değildir, ancak yineleme için kullanılan özel bir `AbstractRange` nesnesidir. Bir aralığı bir vektöre dönüştürmek için [`collect(a:b)`](@ref) kullanın.
  * `:` operatörü R ve Julia'da farklı bir önceliğe sahiptir. Özellikle, Julia'da aritmetik operatörler `:` operatöründen daha yüksek önceliğe sahiptir, oysa R'de bunun tersi doğrudur. Örneğin, `1:n-1` Julia'da `1:(n-1)` ile eşdeğerdir.
  * Julia'nın [`max`](@ref) ve [`min`](@ref) R'deki `pmax` ve `pmin`'in eşdeğerleridir, ancak her iki argümanın da aynı boyutlarda olması gerekir. [`maximum`](@ref) ve [`minimum`](@ref) ise R'deki `max` ve `min`'i değiştirmektedir, ancak önemli farklılıklar vardır.
  * Julia'nın [`sum`](@ref), [`prod`](@ref), [`maximum`](@ref) ve [`minimum`](@ref) R'deki karşıtlarından farklıdır. Hepsi, işlemin gerçekleştirileceği boyutları belirten isteğe bağlı bir anahtar argümanı `dims` kabul eder. Örneğin, Julia'da `A = [1 2; 3 4]` ve R'de `B <- rbind(c(1,2),c(3,4))` aynı matristir. O zaman `sum(A)` ile `sum(B)` aynı sonucu verir, ancak `sum(A, dims=1)` her sütunun toplamını içeren bir satır vektörü ve `sum(A, dims=2)` her satırın toplamını içeren bir sütun vektörüdür. Bu, R'nin davranışıyla çelişir; burada ayrı `colSums(B)` ve `rowSums(B)` fonksiyonları bu işlevselliği sağlar. Eğer `dims` anahtar argümanı bir vektörse, o zaman toplamın gerçekleştirileceği tüm boyutları belirtir ve toplam dizinin boyutlarını korur; örneğin, `sum(A, dims=(1,2)) == hcat(10)`. İkinci argümanla ilgili hata kontrolü yapılmadığına dikkat edilmelidir.
  * Julia'nın argümanlarını değiştirebilen birkaç fonksiyonu vardır. Örneğin, hem [`sort`](@ref) hem de [`sort!`](@ref) vardır.
  * R'de performans, vektörleştirme gerektirir. Julia'da ise neredeyse tam tersi doğrudur: en iyi performans gösteren kod genellikle devektörleştirilmiş döngüler kullanılarak elde edilir.
  * Julia, hevesle değerlendirilir ve R tarzı tembel değerlendirmeyi desteklemez. Çoğu kullanıcı için bu, çok az sayıda alıntılanmamış ifade veya sütun adı olduğu anlamına gelir.
  * Julia `NULL` türünü desteklemez. En yakın eşdeğeri [`nothing`](@ref)'dır, ancak bir liste gibi değil, bir skalar değer gibi davranır. `is.null(x)` yerine `x === nothing` kullanın.
  * In Julia, eksik değerler [`missing`](@ref) nesnesi ile temsil edilir, `NA` ile değil. Bunun yerine [`ismissing(x)`](@ref) (veya vektörler üzerinde eleman bazında işlem için `ismissing.(x)`) kullanın. [`skipmissing`](@ref) fonksiyonu genellikle `na.rm=TRUE` yerine kullanılır (bazı özel durumlarda fonksiyonlar `skipmissing` argümanı alır).
  * Julia, R'nin `assign` veya `get` eşdeğerine sahip değildir.
  * Julia'da `return` parantez gerektirmez.
  * R'de, istenmeyen değerleri kaldırmanın bir yolu mantıksal indeksleme kullanmaktır, örneğin `x[x>3]` ifadesinde veya `x = x[x>3]` ifadesinde `x`'i yerinde değiştirmek için. Buna karşılık, Julia, kullanıcıların `filter(z->z>3, x)` ve `filter!(z->z>3, x)` yazmalarına olanak tanıyan [`filter`](@ref) ve [`filter!`](@ref) yüksek düzeyli fonksiyonlar sunar; bunlar, karşılık gelen transliterasyonlar olan `x[x.>3]` ve `x = x[x.>3]` için alternatiflerdir. `4d61726b646f776e2e436f64652822222c202266696c746572212229_40726566` kullanmak, geçici dizilerin kullanımını azaltır.

## Noteworthy differences from Python

  * Julia'nın `for`, `if`, `while` vb. blokları `end` anahtar kelimesiyle sonlandırılır. Girinti seviyesi, Python'daki gibi önemli değildir. Python'un aksine, Julia'nın `pass` anahtar kelimesi yoktur.
  * Dizeler, Julia'da çift tırnak işaretleri (`"metin"`) ile gösterilir (çok satırlı dizeler için üç çift tırnak işareti kullanılır), Python'da ise ya tek (`'metin'`) ya da çift tırnak işaretleri (`"metin"`) ile gösterilebilir. Tek tırnak işaretleri, Julia'da karakterler için kullanılır (`'c'`).
  * Dize birleştirme, Julia'da Python'daki gibi `+` yerine `*` ile yapılır. Benzer şekilde, dize tekrarı `*` yerine `^` ile yapılır. Python'daki gibi dize sabitlerinin örtük birleştirilmesi (örneğin, `'ab' 'cd' == 'abcd'`) Julia'da yapılmaz.
  * Python Listeleri—esnek ama yavaş—Julia `Vector{Any}` türüne veya daha genel olarak `Vector{T}` türüne karşılık gelir; burada `T`, bazı somut olmayan eleman türleridir. Elemanları yerinde depolayan "hızlı" diziler, yani `dtype` `np.float64`, `[('f1', np.uint64), ('f2', np.int32)]` vb. olan NumPy dizileri, `Array{T}` ile temsil edilebilir; burada `T`, somut, değişmez bir eleman türüdür. Bu, `Float64`, `Int32`, `Int64` gibi yerleşik türleri, ancak aynı zamanda `Tuple{UInt64,Float64}` gibi daha karmaşık türleri ve birçok kullanıcı tanımlı türü de içerir.
  * Julia'da dizilerin, stringlerin vb. indekslemesi 0 tabanlı değil, 1 tabanlıdır.
  * Julia'nın dilim indekslemesi, Python'dakinin aksine son öğeyi de içerir. `a[2:3]` Julia'da `a[1:3]` şeklindedir.
  * Julia, Python'dan farklı olarak [AbstractArrays with arbitrary indexes](https://julialang.org/blog/2017/04/offset-arrays/) değerlerini destekler. Python'un negatif indeksleme için özel yorumu, `a[-1]` ve `a[-2]`, Julia'da `a[end]` ve `a[end-1]` olarak yazılmalıdır.
  * Julia, son son eleman için `end` gerektirir. Python'daki `x[1:]`, Julia'da `x[2:end]` ile eşdeğerdir.
  * In Julia, `:` herhangi bir nesnenin önünde [`Symbol`](@ref) veya bir ifadeyi *tırnak içine alır*; bu nedenle, `x[:5]` `x[5]` ile aynıdır. Bir dizinin ilk `n` elemanını almak istiyorsanız, o zaman aralık indekslemesi kullanın.
  * Julia'nın aralık indekslemesi `x[start:step:stop]` formatına sahiptir, oysa Python'un formatı `x[start:(stop+1):step]` şeklindedir. Bu nedenle, Python'daki `x[0:10:2]`, Julia'daki `x[1:2:10]` ile eşdeğerdir. Benzer şekilde, Python'daki `x[::-1]`, ters çevrilmiş diziyi ifade eder ve bu, Julia'da `x[end:-1:1]` ile eşdeğerdir.
  * Julia'da, aralıklar bağımsız olarak `başlangıç:adım:dur` şeklinde oluşturulabilir, bu da dizi indekslemede kullanılan aynı sözdizimidir. `range` fonksiyonu da desteklenmektedir.
  * Julia'da, bir matrisin dizinlenmesi `X[[1,2], [1,3]]` gibi, bir alt matrisin ilk ve ikinci satırlarının birinci ve üçüncü sütunlarıyla kesişimlerini ifade eder. Python'da ise `X[[1,2], [1,3]]`, matrisin `[1,1]` ve `[2,3]` hücrelerinin değerlerini içeren bir vektörü ifade eder. Julia'daki `X[[1,2], [1,3]]`, Python'daki `X[np.ix_([0,1],[0,2])]` ile eşdeğerdir. Python'daki `X[[0,1], [0,2]]`, Julia'daki `X[[CartesianIndex(1,1), CartesianIndex(2,3)]]` ile eşdeğerdir.
  * Julia'nın satır devam ettirme sözdizimi yoktur: bir satırın sonunda, şu ana kadar olan girdi tam bir ifade ise, işlem tamamlanmış sayılır; aksi takdirde girdi devam eder. Bir ifadeyi devam ettirmeyi zorlamanın bir yolu, onu parantez içine almaktır.
  * Julia arrays are column-major (Fortran-ordered) whereas NumPy arrays are row-major (C-ordered) by default. To get optimal performance when looping over arrays, the order of the loops should be reversed in Julia relative to NumPy (see [relevant section of Performance Tips](@ref man-performance-column-major)).
  * Julia'nın güncelleme operatörleri (örneğin `+=`, `-=`, ...) *yerinde değil* iken NumPy'ninkiler yerinde. Bu, `A = [1, 1]; B = A; B += [3, 3]` ifadesinin `A`'daki değerleri değiştirmediği, bunun yerine `B` adını sağdaki sonucun `B = B + 3` ile yeniden bağladığı anlamına gelir; bu yeni bir dizidir. Yerinde işlem için `B .+= 3` kullanın (ayrıca bkz. [dot operators](@ref man-dot-operators)), açık döngüler veya `InplaceOps.jl` kullanabilirsiniz.
  * Julia, varsayılan değerleri her seferinde işlev çağrıldığında değerlendirir, Python'da ise varsayılan değerler yalnızca işlev tanımlandığında bir kez değerlendirilir. Örneğin, `f(x=rand()) = x` işlevi, argüman olmadan her çağrıldığında yeni bir rastgele sayı döndürür. Öte yandan, `g(x=[1,2]) = push!(x,3)` işlevi, `g()` olarak her çağrıldığında `[1,2,3]` döndürür.
  * Julia'da anahtar argümanlar, genellikle Python'da olduğu gibi konum olarak geçilemeyecek şekilde anahtar kelimeler kullanılarak geçilmelidir. Bir anahtar argümanı konum olarak geçmeye çalışmak, yöntem imzasını değiştirir ve bu da bir `MethodError` veya yanlış yöntemin çağrılmasına neden olur.
  * Julia'da `%` kalanı bulma operatörüdür, Python'da ise modüldür.
  * Julia'da yaygın olarak kullanılan `Int` türü, makine tam sayı türüne (`Int32` veya `Int64`) karşılık gelir; bu, Python'daki `int`'in keyfi uzunlukta bir tam sayı olduğu anlamına gelir. Bu, Julia'da `Int` türünün taşma yapacağı anlamına gelir; örneğin `2^64 == 0`. Daha büyük değerlere ihtiyacınız varsa, `Int128`, [`BigInt`](@ref) gibi başka uygun bir tür veya `Float64` gibi bir kayan nokta türü kullanın.
  * Hayali birim `sqrt(-1)` Julia'da `im` olarak, Python'da ise `j` olarak temsil edilir.
  * Julia'da üstel alma operatörü `^`'dir, Python'daki gibi `**` değil.
  * Julia `nothing` türü `Nothing` kullanarak bir null değerini temsil ederken, Python `None` türü `NoneType` kullanır.
  * Julia'da, bir matris türü üzerindeki standart operatörler matris işlemleridir, oysa Python'da standart operatörler eleman bazında işlemlerdir. Hem `A` hem de `B` matrisleri olduğunda, Julia'da `A * B` matris çarpımını gerçekleştirir, Python'daki gibi eleman bazında çarpım değil. Julia'daki `A * B`, Python'daki `A @ B` ile eşdeğerdir, oysa Python'daki `A * B`, Julia'daki `A .* B` ile eşdeğerdir.
  * Julia'daki `'` adjoint operatörü, bir vektörün adjoint'ini (satır vektörünün tembel bir temsilini) döndürürken, Python'daki `.T` transpoze operatörü bir vektör üzerinde orijinal vektörü (işlem yapmayan) döndürür.
  * Julia'da bir fonksiyon birden fazla somut uygulama (metot olarak adlandırılır) içerebilir ve bu metotlar, çağrıdaki tüm argümanların türlerine dayalı olarak çoklu dağıtım (multiple dispatch) ile seçilir. Bu, Python'daki fonksiyonlardan farklıdır; çünkü Python'da tek bir uygulama vardır ve çok biçimlilik (polymorphism) yoktur (Python metot çağrıları ise farklı bir sözdizimi kullanır ve metot alıcısına göre dağıtım yapılmasına izin verir).
  * Julia'da sınıf yoktur. Bunun yerine, veri içeren ancak yöntem içermeyen (değiştirilebilir veya değiştirilemez) yapılar vardır.
  * Bir Python sınıf örneğinin bir yöntemini çağırmak (`x = MyClass(*args); x.f(y)`) Julia'daki bir işlev çağrısına karşılık gelir, örneğin `x = MyType(args...); f(x, y)`. Genel olarak, çoklu dispatch, Python sınıf sisteminden daha esnek ve güçlüdür.
  * Julia yapıları tam olarak bir soyut üst tipe sahip olabilirken, Python sınıfları bir veya daha fazla (soyut veya somut) üst sınıftan miras alabilir.
  * Mantıksal Julia program yapısı (Paketler ve Modüller) dosya yapısından bağımsızdır, oysa Python kod yapısı dizinler (Paketler) ve dosyalar (Modüller) tarafından tanımlanır.
  * Julia'da, büyük modüllerin metnini birden fazla dosyaya ayırmak, her dosya için yeni bir modül tanıtmak yerine, idiomatik bir yaklaşımdır. Kod, `include` aracılığıyla ana dosyada tek bir modül içinde yeniden bir araya getirilir. Bunun Python'daki karşılığı (`exec`), bu kullanım için tipik değildir (önceki tanımları sessizce geçersiz kılacaktır), Julia programları `using` veya `import` ile `module` seviyesinde bir birim olarak tanımlanır; bu, ilk ihtiyaç duyulduğunda yalnızca bir kez çalıştırılacaktır - Python'daki `include` gibi. Bu modüller içinde, o modülü oluşturan bireysel dosyalar, istenen sırada bir kez listeleyerek `include` ile yüklenir.
  * Julia'daki `x > 0 ? 1 : -1` ternary operatörü, Python'daki `1 if x > 0 else -1` koşullu ifadesine karşılık gelir.
  * Julia'da `@` sembolü bir makroya, Python'da ise bir dekoratöre atıfta bulunur.
  * Julia'da istisna yönetimi `try` — `catch` — `finally` kullanılarak yapılır, `try` — `except` — `finally` yerine. Python'a kıyasla, Julia'da istisna yönetiminin normal iş akışının bir parçası olarak kullanılmasını önerilmez (Python ile karşılaştırıldığında, Julia sıradan kontrol akışında daha hızlıdır ancak istisna yakalamada daha yavaştır).
  * Julia döngüleri hızlıdır, performans nedenleriyle "vektörleştirilmiş" kod yazmaya gerek yoktur.
  * Julia'da, özellikle sıkı döngülerde, sabit olmayan global değişkenlerle dikkatli olun. Julia'da (Python'ın aksine) metal seviyesine yakın kod yazabileceğiniz için, global değişkenlerin etkisi dramatik olabilir (bkz. [Performance Tips](@ref man-performance-tips)).
  * Julia'da yuvarlama ve kesme açıktır. Python'un `int(3.7)` ifadesi `floor(Int, 3.7)` veya `Int(floor(3.7))` olmalı ve `round(Int, 3.7)` ifadesinden ayrılmaktadır. `floor(x)` ve `round(x)` kendi başlarına `x` ile aynı türde bir tam sayı değeri döndürür, her zaman `Int` döndürmez.
  * Julia'da ayrıştırma açıktır. Python'un `float("3.7")` ifadesi Julia'da `parse(Float64, "3.7")` olur.
  * Python'da, çoğu değer mantıksal bağlamlarda kullanılabilir (örneğin, `if "a":` ifadesi aşağıdaki bloğun çalıştırılacağı anlamına gelir, ve `if "":` ifadesi bunun tersi). Julia'da ise `Bool`'a açık bir dönüşüm gereklidir (örneğin, `if "a"` bir istisna fırlatır). Julia'da boş olmayan bir dizeyi test etmek istiyorsanız, açıkça `if !isempty("")` yazmalısınız. Belki de şaşırtıcı bir şekilde, Python'da `if "False"` ve `bool("False")` her ikisi de `True` olarak değerlendirilir (çünkü `"False"` boş olmayan bir dizedir); Julia'da ise `parse(Bool, "false")` `false` döner.
  * Julia'da, yeni bir yerel kapsam çoğu kod bloğu tarafından tanıtılır, döngüler ve `try` — `catch` — `finally` dahil. Anlamanız gereken, Python ve Julia'da da yeni bir yerel kapsam tanıtan derlemelerin (liste, jeneratör vb.) yanı sıra, `if` bloklarının her iki dilde de yeni bir yerel kapsam tanıtmadığıdır.

## Noteworthy differences from C/C++

  * Julia dizileri köşeli parantezlerle indekslenir ve birden fazla boyuta sahip olabilir `A[i,j]`. Bu sözdizimi, C/C++'taki bir işaretçi veya adres referansı için sadece sözdizimsel bir şekerleme değildir. [the manual entry about array construction](@ref man-multi-dim-arrays) bakın.
  * Julia'da dizilerin, stringlerin vb. indekslemesi 0 tabanlı değil, 1 tabanlıdır.
  * Julia dizileri başka bir değişkene atandığında kopyalanmaz. `A = B` işleminden sonra, `B`'nin elemanlarını değiştirmek `A`'yı da değiştirecektir. Güncelleme operatörleri gibi `+=` yerinde çalışmaz, bunlar `A = A + B` ile eşdeğerdir ve sol taraftaki değişkeni sağ taraftaki ifadenin sonucuna yeniden bağlar.
  * Julia dizileri sütun öncelikli (Fortran sıralı) iken C/C++ dizileri varsayılan olarak satır öncelikli sıralıdır. Diziler üzerinde döngü kurarken optimal performans elde etmek için döngülerin sırası C/C++'a göre Julia'da tersine çevrilmelidir (bkz. [relevant section of Performance Tips](@ref man-performance-column-major)).
  * Julia değerleri atandığında veya bir işleve geçirildiğinde kopyalanmaz. Bir işlev bir diziyi değiştirirse, değişiklikler çağıran yerde görünür olacaktır.
  * Julia'da, boşluk karakterleri önemlidir, C/C++'ın aksine, bu nedenle bir Julia programına boşluk eklerken/çıkarırken dikkatli olunmalıdır.
  * Julia'da, ondalık noktası olmayan literal sayılar (örneğin `42`), `Int` türünde işaretli tam sayılar oluşturur, ancak makine kelime boyutuna sığmayan çok büyük literal sayılar otomatik olarak daha büyük boyut türlerine yükseltilir, örneğin `Int32` ise `Int64`, `Int128` veya keyfi olarak büyük `BigInt` türüne. İşaretli ve/veya işaretsiz sayıları belirtmek için `L`, `LL`, `U`, `UL`, `ULL` gibi sayısal literal son ekleri yoktur. Ondalık literal sayılar her zaman işaretlidir ve onaltılık literal sayılar (C/C++ gibi `0x` ile başlayan) işaretsizdir, 128 bitten fazla kodladıklarında ise `BigInt` türündedirler. Onaltılık literal sayılar ayrıca, C/C++/Java'dan farklı olarak ve Julia'daki ondalık literal sayılardan farklı olarak, literalın *uzunluğuna* dayalı bir türe sahiptir, ön sıfırlar dahil. Örneğin, `0x0` ve `0x00` türü [`UInt8`](@ref), `0x000` ve `0x0000` türü [`UInt16`](@ref)'dır, ardından 5 ile 8 onaltılık basamağa sahip literal sayılar `UInt32` türünde, 9 ile 16 onaltılık basamağa sahip olanlar `UInt64` türünde, 17 ile 32 onaltılık basamağa sahip olanlar `UInt128` türünde ve 32'den fazla onaltılık basamağa sahip olanlar `BigInt` türündedir. Bu, onaltılık maskeleri tanımlarken dikkate alınmalıdır; örneğin `~0xf == 0xf0`, `~0x000f == 0xfff0`'dan çok farklıdır. 64 bit `Float64` ve 32 bit [`Float32`](@ref) bit literal sayıları sırasıyla `1.0` ve `1.0f0` olarak ifade edilir. Ondalık noktalı literal sayılar, tam olarak temsil edilemeyecekleri durumlarda yuvarlanır (ve `BigFloat` türüne yükseltilmez). Ondalık noktalı literal sayılar, C/C++'a daha yakın bir davranış sergiler. Sekizli (ön ek `0o` ile) ve ikili (ön ek `0b` ile) literal sayılar da işaretsiz olarak (veya 128 bitten fazla için `BigInt` olarak) işlenir.
  * Julia'da bölme operatörü [`/`](@ref) her iki operandın da tam sayı türünde olduğu durumlarda bir ondalık sayı döndürür. Tam sayı bölmesi yapmak için [`div`](@ref) veya [`÷`](@ref div) kullanın.
  * Bir `Array`'ı ondalık sayı türleriyle dizinlemek genellikle Julia'da bir hatadır. C ifadesi `a[i / 2]`'nin Julia eşdeğeri `a[i ÷ 2 + 1]`'dir; burada `i` tam sayı türündedir.
  * Dize dizeleri ya `"` ya da `"""` ile sınırlanabilir, `"""` ile sınırlanan dizeler, `"` karakterlerini alıntı yapmadan içerebilir, örneğin `"\""` gibi. Dize dizeleri, diğer değişkenlerin veya ifadelerin değerlerini içerebilir, bu da `$değişkenadı` veya `$(ifade)` ile gösterilir; bu, değişken adını veya ifadeyi fonksiyonun bağlamında değerlendirir.
  * `//` bir [`Rational`](@ref) numarasını belirtir ve tek satırlık bir yorum değildir (bu Julia'da `#` ile gösterilir)
  * `#=` çok satırlı bir yorumun başlangıcını belirtir ve `=#` onu bitirir.
  * Julia'da fonksiyonlar, son ifadelerinden veya `return` anahtar kelimesinden değer döndürür. Birden fazla değer, fonksiyonlardan döndürülebilir ve demetler olarak atanabilir; örneğin, `(a, b) = myfunction()` veya `a, b = myfunction()` şeklinde, C/C++'da olduğu gibi değerlerin işaretçilerini geçmek zorunda kalmadan (yani `a = myfunction(&b)`).
  * Julia, ifadelerin sonunu bitirmek için noktalı virgül kullanımını gerektirmez. İfadelerin sonuçları otomatik olarak yazdırılmaz (etkileşimli istemde, yani REPL'de hariç) ve kod satırlarının noktalı virgülle bitmesi gerekmez. [`println`](@ref) veya [`@printf`](@ref) belirli bir çıktıyı yazdırmak için kullanılabilir. REPL'de, çıktı bastırmak için `;` kullanılabilir. `;` ayrıca `[ ]` içinde farklı bir anlama sahiptir, bu yüzden dikkatli olunmalıdır. `;` tek bir satırda ifadeleri ayırmak için kullanılabilir, ancak birçok durumda kesinlikle gerekli değildir ve daha çok okunabilirliğe yardımcıdır.
  * Julia'da [`⊻`](@ref xor) ([`xor`](@ref)) operatörü bit düzeyinde XOR işlemi gerçekleştirir, yani C/C++'da [`^`](@ref) şeklindedir. Ayrıca, bit düzeyindeki operatörlerin C/C++ ile aynı önceliğe sahip olmadığını unutmayın, bu nedenle parantez kullanmak gerekebilir.
  * Julia'nın [`^`](@ref) üstel alma (pow) işlemi yapar, C/C++'daki bit düzeyinde XOR işlemi değil (Julia'da [`⊻`](@ref xor) veya [`xor`](@ref) kullanın)
  * Julia'nın iki sağa kaydırma operatörü vardır, `>>` ve `>>>`. `>>` aritmetik kaydırma yapar, `>>>` ise her zaman mantıksal kaydırma yapar; C/C++'da ise `>>` operatörünün anlamı kaydırılan değerin türüne bağlıdır.
  * Julia'nın `->` ifadesi anonim bir fonksiyon oluşturur, bir üye işaretçisine erişmez.
  * Julia parantez gerektirmez `if` ifadeleri veya `for`/`while` döngüleri yazarken: `for i in [1, 2, 3]` yerine `for (int i=1; i <= 3; i++)` ve `if i == 1` yerine `if (i == 1)` kullanın.
  * Julia, `0` ve `1` sayılarını Boolean olarak değerlendirmez. Julia'da `if (1)` yazamazsınız, çünkü `if` ifadeleri yalnızca boolean değerleri kabul eder. Bunun yerine `if true`, `if Bool(1)` veya `if 1==1` yazabilirsiniz.
  * Julia, koşul bloklarının, döngü bloklarının ve fonksiyonların sonunu belirtmek için `end` kullanır, örneğin `if`, `while`/ `for`. Tek satırlık `if ( cond ) statement` yerine, Julia `if cond; statement; end`, `cond && statement` ve `!cond || statement` biçimindeki ifadeleri kabul eder. Son iki sözdizimindeki atama ifadeleri, operatör önceliği nedeniyle açıkça parantez içine alınmalıdır, örneğin `cond && (x = value)`.
  * Julia'nın satır devam ettirme sözdizimi yoktur: bir satırın sonunda, şu ana kadar olan girdi tam bir ifade ise, tamamlanmış olarak kabul edilir; aksi takdirde girdi devam eder. Bir ifadeyi devam ettirmeyi zorlamanın bir yolu, onu parantez içine almaktır.
  * Julia makroları, programın metni yerine ayrıştırılmış ifadeler üzerinde çalışır, bu da onlara Julia kodunun karmaşık dönüşümlerini gerçekleştirme imkanı tanır. Makro adları `@` karakteri ile başlar ve hem işlev benzeri bir sözdizimine, `@mymacro(arg1, arg2, arg3)`, hem de ifade benzeri bir sözdizimine, `@mymacro arg1 arg2 arg3`, sahiptir. Bu formlar birbirinin yerine geçebilir; işlev benzeri form, makro başka bir ifadede yer aldığında özellikle kullanışlıdır ve genellikle en net olanıdır. İfade benzeri form, dağıtılmış `for` yapısı gibi blokları notlandırmak için sıklıkla kullanılır: `@distributed for i in 1:n; #= body =#; end`. Makro yapısının sonunun belirsiz olduğu durumlarda, işlev benzeri formu kullanın.
  * Julia bir enum türüne sahiptir, bu tür `@enum(isim, deger1, deger2, ...)` makrosu kullanılarak ifade edilir. Örneğin: `@enum(Meyve, muz=1, elma, armut)`
  * Gelenek olarak, argümanlarını değiştiren fonksiyonların adının sonunda `!` bulunur, örneğin `push!`.
  * C++'da, varsayılan olarak statik dağıtım vardır, yani dinamik dağıtım elde etmek için bir fonksiyonu sanal olarak işaretlemeniz gerekir. Öte yandan, Julia'da her yöntem "sanal"dır (ancak bu, yöntemlerin yalnızca `this` üzerinde değil, her argüman türü üzerinde en özel bildirim kuralına göre dağıtıldığı için daha genel bir durumdur).

### Julia ⇔ C/C++: Namespaces

  * C/C++ `namespace`'leri, yaklaşık olarak Julia `modül`lerine karşılık gelir.
  * Julia'da özel global veya alan yoktur. Her şey, istenirse göreli yollarla (veya tam nitelikli yollarla) kamuya açık bir şekilde erişilebilir.
  * `MyNamespace::myfun` (C++) yaklaşık olarak `import MyModule: myfun` (Julia) ile karşılık gelir.
  * `using namespace MyNamespace` (C++) yaklaşık olarak `using MyModule` (Julia) ile eşdeğerdir.

      * Julia'da yalnızca `export` edilen semboller çağrılan modüle sunulur.
      * C++'da yalnızca dahil edilen (kamusal) başlık dosyalarında bulunan öğeler kullanılabilir hale gelir.
  * Uyarı: `import`/`using` anahtar kelimeleri (Julia) ayrıca *modülleri yükler* (aşağıya bakın).
  * Uyarı: `import`/`using` (Julia) yalnızca global kapsam düzeyinde (`module`ler) çalışır.

      * C++'da `using namespace X` herhangi bir kapsamda (örneğin: fonksiyon kapsamı) çalışır.

### Julia ⇔ C/C++: Module loading

  * C/C++ "**kütüphane**" düşündüğünüzde, muhtemelen bir Julia "**paket**" arıyorsunuzdur.

      * Uyarı: C/C++ kütüphaneleri genellikle birden fazla "yazılım modülü" barındırırken, Julia "paketleri" genellikle bir tane barındırır.
      * Hatırlatma: Julia `modülleri` küresel kapsamdır (mutlaka "yazılım modülleri" değildir).
  * **Yerine build/`make` betikleri**, Julia "Proje Ortamları" kullanır (bazen "Proje" veya "Ortam" olarak adlandırılır).

      * Yapı betikleri yalnızca daha karmaşık uygulamalar için gereklidir (C/C++ yürütülebilir dosyaları derlemeyi veya indirmeyi gerektirenler gibi).
      * Julia'da bir uygulama veya proje geliştirmek için, kök dizinini "Proje Ortamı" olarak başlatabilir ve uygulamaya özgü kod/paketleri burada barındırabilirsiniz. Bu, proje bağımlılıkları üzerinde iyi bir kontrol sağlar ve gelecekteki yeniden üretilebilirliği artırır.
      * Mevcut paketler, `Pkg.add()` fonksiyonu veya Pkg REPL modu ile bir "Proje Ortamı"na eklenir. (Bu, söz konusu paketi **yüklemez**).
      * "Proje Ortamı" için mevcut paketlerin (doğrudan bağımlılıklar) listesi `Project.toml` dosyasında kaydedilmiştir.
      * "Proje Ortamı" için *tam* bağımlılık bilgisi, `Pkg.resolve()` tarafından otomatik olarak oluşturulur ve `Manifest.toml` dosyasına kaydedilir.
  * "Proje Ortamı"na mevcut olan paketler ("yazılım modülleri") `import` veya `using` ile yüklenir.

      * C/C++'de, nesne/fonksiyon bildirimlerini almak için `#include <moduleheader>` kullanırsınız ve çalıştırılabilir dosyayı oluşturduğunuzda kütüphaneleri bağlarsınız.
      * Julia'da, `using`/`import` komutunu tekrar çağırmak, mevcut modülü kapsam içine alır, ancak onu tekrar yüklemez (C/C++'da standart dışı `#pragma once` eklemeye benzer).
  * **Dizin tabanlı paket depoları** (Julia), `Base.LOAD_PATH` dizisine depo yolları eklenerek kullanılabilir hale getirilebilir.

      * Dizin tabanlı depolardan gelen paketler, `import` veya `using` ile yüklenmeden önce `Pkg.add()` aracını gerektirmez. Onlar, projeye basitçe mevcuttur.
      * Dizin tabanlı paket depoları, "yazılım modülleri" için yerel kütüphaneler geliştirmek için en **hızlı çözümdür**.

### Julia ⇔ C/C++: Assembling modules

  * C/C++'de, `.c`/`.cpp` dosyaları derlenir ve build/`make` betikleri ile bir kütüphaneye eklenir.

      * Julia'da `import [PkgName]`/`using [PkgName]` ifadeleri, bir paketin `[PkgName]/src/` alt dizininde bulunan `[PkgName].jl` dosyasını yükler.
      * Sırasıyla, `[PkgName].jl` genellikle `include "[someotherfile].jl"` çağrıları ile ilişkili kaynak dosyaları yükler.
  * `include "./path/to/somefile.jl"` (Julia) `#include "./path/to/somefile.jl"` (C/C++) ile çok benzer.

      * Ancak `include "..."` (Julia) başlık dosyalarını dahil etmek için kullanılmaz (gerekli değildir).
      * **Diğer "yazılım modüllerinden" kod yüklemek için** `include "..."` (Julia) **kullanmayın (bunun yerine `import`/`using` kullanın).**
      * `include "path/to/some/module.jl"` (Julia) aynı isimlere sahip *farklı* türler (vb.) oluşturarak kodun aynı versiyonlarını farklı modüllerde başlatır.
      * `include "somefile.jl"` genellikle birden fazla dosyayı *aynı Julia paketi* ("yazılım modülü") içinde bir araya getirmek için kullanılır. Bu nedenle, dosyaların yalnızca bir kez `include` edilmesini sağlamak oldukça basittir (No `#ifdef` karışıklığı).

### Julia ⇔ C/C++: Module interface

  * C++ "public" `.h`/`.hpp` dosyaları kullanarak arayüzleri açarken, Julia `modül`leri kullanıcıları için tasarlanmış belirli sembolleri `public` veya `export` olarak işaretler.

      * Sıklıkla, Julia `modül`leri mevcut fonksiyonlara (örneğin: `Base.push!`) yeni "metotlar" ekleyerek işlevsellik katmaktadır.
      * Julia paketlerinin geliştiricileri bu nedenle arayüz belgeleri için başlık dosyalarına güvenemezler.
      * Julia paketleri için arayüzler genellikle docstring'ler, README.md, statik web sayfaları vb. kullanılarak tanımlanır...
  * Bazı geliştiriciler, paketlerini/modüllerini kullanmak için gereken tüm sembolleri `export` etmeyi tercih etmez, ancak yine de dışa aktarılmayan kullanıcıya yönelik sembolleri `public` olarak işaretlemelidir.

      * Kullanıcıların bu bileşenlere, işlevleri/yapıları/... paket/modül adıyla nitelendirerek erişmeleri beklenebilir (örneğin: `MyModule.run_this_task(...)`).

### Julia ⇔ C/C++: Quick reference

| Software Concept               | Julia                                                                          | C/C++                                                     |
|:------------------------------ |:------------------------------------------------------------------------------ |:--------------------------------------------------------- |
| unnamed scope                  | `begin` ... `end`                                                              | `{` ... `}`                                               |
| function scope                 | `function x()` ... `end`                                                       | `int x() {` ... `}`                                       |
| global scope                   | `module MyMod` ... `end`                                                       | `namespace MyNS {` ... `}`                                |
| software module                | A Julia "package"                                                              | `.h`/`.hpp` files<br>+compiled `somelib.a`                |
| assembling<br>software modules | `SomePkg.jl`: ...<br>`import("subfile1.jl")`<br>`import("subfile2.jl")`<br>... | `$(AR) *.o` &rArr; `somelib.a`                            |
| import<br>software module      | `import SomePkg`                                                               | `#include <somelib>`<br>+link in `somelib.a`              |
| module library                 | `LOAD_PATH[]`, *Git repository,<br>**custom package registry                   | more `.h`/`.hpp` files<br>+bigger compiled `somebiglib.a` |

* The Julia package manager supports registering multiple packages from a single Git repository.<br> * This allows users to house a library of related packages in a single repository.<br> ** Julia registries are primarily designed to provide versioning \& distribution of packages.<br> ** Custom package registries can be used to create a type of module library.

## Noteworthy differences from Common Lisp

  * Julia, varsayılan olarak diziler için 1 tabanlı indeksleme kullanır ve ayrıca keyfi [index offsets](@ref man-custom-indices) değerlerini de işleyebilir.
  * Fonksiyonlar ve değişkenler aynı ad alanını paylaşır (“Lisp-1”).
  * [`Pair`](@ref) türü vardır, ancak bu `COMMON-LISP:CONS` olarak kullanılmak üzere tasarlanmamıştır. Çoğu dil bölümünde birbirinin yerine kullanılabilen çeşitli yinelemeli koleksiyonlar mevcuttur (örneğin splatting, tuple'lar vb.). `Tuple`lar, heterojen öğelerin *kısa* koleksiyonları için Common Lisp listelerine en yakın olanlardır. Alist'lerin yerine `NamedTuple`'lar kullanın. Homojen türlerin daha büyük koleksiyonları için `Array` ve `Dict` kullanılmalıdır.
  * Tipik Julia iş akışı, [Revise.jl](https://github.com/timholy/Revise.jl) paketi ile uygulanan görüntünün sürekli manipülasyonunu da kullanır.
  * Performans için, Julia işlemlerin [type stability](@ref man-type-stability) olmasını tercih eder. Common Lisp, temel makine işlemlerinden soyutlanırken, Julia onlara daha yakın durur. Örneğin:

      * Tam sayılarla bölme `/` her zaman bir kesirli sonuç döndürür, hesaplama tam olsa bile.

          * `//` her zaman rasyonel bir sonuç döner
          * `÷` her zaman (kısmı) tam sayı sonucu döner
      * Bignum'lar desteklenmektedir, ancak dönüşüm otomatik değildir; sıradan tam sayılar [overflow](@ref faq-integer-arithmetic).
      * Karmaşık sayılar desteklenmektedir, ancak karmaşık sonuçlar almak için [you need complex inputs](@ref faq-domain-errors).
      * Birden fazla Karmaşık ve Rasyonel türü vardır, farklı bileşen türleri ile.
  * Modüller (ad alanları) hiyerarşik olabilir. [`import`](@ref) ve [`using`](@ref) çift rol oynar: kodu yükler ve onu ad alanında kullanılabilir hale getirir. Sadece modül adı için `import` mümkündür (kabaca `ASDF:LOAD-OP` ile eşdeğerdir). Slot adlarının ayrı olarak dışa aktarılmasına gerek yoktur. Küresel değişkenlere modül dışından atama yapılamaz (sadece `eval(mod, :(var = val))` ile bir kaçış yolu olarak).
  * Makrolar `@` ile başlar ve Common Lisp kadar dilin içine entegre edilmemiştir; dolayısıyla, makro kullanımı ikincisinde olduğu kadar yaygın değildir. [macros](@ref Metaprogramming) için bir tür hijyen dil tarafından desteklenmektedir. Farklı yüzey sözdizimi nedeniyle, `COMMON-LISP:&BODY` ile eşdeğer bir şey yoktur.
  * *Tüm* fonksiyonlar genel olup çoklu dağıtım kullanır. Argüman listeleri aynı şablonu takip etmek zorunda değildir, bu da güçlü bir deyimle sonuçlanır (bkz. [`do`](@ref)). İsteğe bağlı ve anahtar kelime argümanları farklı şekilde işlenir. Yöntem belirsizlikleri, Common Lisp Nesne Sistemi'nde olduğu gibi çözülmez, bu da kesişim için daha spesifik bir yöntemin tanımlanmasını gerektirir.
  * Semboller herhangi bir pakete ait değildir ve *kendiliğinden* herhangi bir değer içermez. `M.var` sembolü `M` modülünde `var` sembolünü değerlendirir.
  * A functional programming style is fully supported by the language, including closures, but isn't always the idiomatic solution for Julia. Some [workarounds](@ref man-performance-captured) may be necessary for performance when modifying captured variables.
