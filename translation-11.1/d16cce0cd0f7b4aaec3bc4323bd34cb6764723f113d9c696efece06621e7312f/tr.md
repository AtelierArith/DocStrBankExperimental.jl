# Dates

```@meta
DocTestSetup = :(using Dates)
```

`Dates` modülü, tarihlerle çalışmak için iki tür sağlar: [`Date`](@ref) ve [`DateTime`](@ref), sırasıyla gün ve milisaniye hassasiyetini temsil eder; her ikisi de soyut [`TimeType`](@ref) türünün alt türleridir. Farklı türlerin motivasyonu basittir: bazı işlemler, daha büyük hassasiyetin karmaşıklıklarıyla uğraşmak zorunda kalmadığınızda, hem kod hem de zihinsel akıl yürütme açısından çok daha basittir. Örneğin, `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` türü yalnızca tek bir tarihin hassasiyetine (yani saat, dakika veya saniye yok) çözündüğünden, zaman dilimleri, yaz saati uygulaması/yaz zamanı ve artık saniyeler için normal dikkate alınmalar gereksiz hale gelir ve kaçınılır.

Her iki [`Date`](@ref) ve [`DateTime`](@ref) temelde değişmez [`Int64`](@ref) sarmalayıcılardır. Her iki türün tek `instant` alanı aslında sürekli artan bir makine zaman çizelgesini temsil eden bir `UTInstant{P}` türüdür ve bu, UT saniyesine dayanmaktadır [^1]. `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` türü zaman dilimlerinden haberdar değildir (*naif*, Python terimiyle), Java 8'deki bir *LocalDateTime* ile benzerlik gösterir. Ek zaman dilimi işlevselliği, [TimeZones.jl package](https://github.com/JuliaTime/TimeZones.jl/) aracılığıyla eklenebilir; bu, [IANA time zone database](https://www.iana.org/time-zones) derleyicisidir. Hem `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` hem de `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566`, proleptik Gregory takvimine uyan [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) standardına dayanmaktadır. Bir not olarak, ISO 8601 standardı M.Ö./M.S. tarihleri konusunda özeldir. Genel olarak, M.Ö./M.S. döneminin son günü, 1-12-31 M.Ö./M.S., 1-1-1 M.S./M.S. ile takip edilmiştir, bu nedenle sıfır yıl yoktur. Ancak ISO standardı, 1 M.Ö./M.S.'nin sıfır yıl olduğunu belirtmektedir, bu nedenle `0000-12-31`, `0001-01-01`'den bir gün öncesidir ve yıl `-0001` (evet, yıl için negatif bir) 2 M.Ö./M.S., yıl `-0002` 3 M.Ö./M.S. vb. dir.

[^1]: The notion of the UT second is actually quite fundamental. There are basically two different notions of time generally accepted, one based on the physical rotation of the earth (one full rotation = 1 day), the other based on the SI second (a fixed, constant value). These are radically different! Think about it, a "UT second", as defined relative to the rotation of the earth, may have a different absolute length depending on the day! Anyway, the fact that [`Date`](@ref) and [`DateTime`](@ref) are based on UT seconds is a simplifying, yet honest assumption so that things like leap seconds and all their complexity can be avoided. This basis of time is formally called [UT](https://en.wikipedia.org/wiki/Universal_Time) or UT1. Basing types on the UT second basically means that every minute has 60 seconds and every day has 24 hours and leads to more natural calculations when working with calendar dates.

## Constructors

[`Date`](@ref) ve [`DateTime`](@ref) türleri, tam sayılar veya [`Period`](@ref) türleri tarafından, ayrıştırılarak veya ayarlayıcılar aracılığıyla (bunlar hakkında daha sonra) oluşturulabilir:

```jldoctest
julia> DateTime(2013)
2013-01-01T00:00:00

julia> DateTime(2013,7)
2013-07-01T00:00:00

julia> DateTime(2013,7,1)
2013-07-01T00:00:00

julia> DateTime(2013,7,1,12)
2013-07-01T12:00:00

julia> DateTime(2013,7,1,12,30)
2013-07-01T12:30:00

julia> DateTime(2013,7,1,12,30,59)
2013-07-01T12:30:59

julia> DateTime(2013,7,1,12,30,59,1)
2013-07-01T12:30:59.001

julia> Date(2013)
2013-01-01

julia> Date(2013,7)
2013-07-01

julia> Date(2013,7,1)
2013-07-01

julia> Date(Dates.Year(2013),Dates.Month(7),Dates.Day(1))
2013-07-01

julia> Date(Dates.Month(7),Dates.Year(2013))
2013-07-01
```

[`Date`](@ref) veya [`DateTime`](@ref) ayrıştırma, format dizeleri kullanılarak gerçekleştirilir. Format dizeleri, bir noktayı ayrıştırmak için *sınırlı* veya *sabit genişlikte* "slotlar" tanımlama kavramıyla çalışır ve ayrıştırılacak metni ve bir `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` veya `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` yapıcısına geçer, biçimi `Date("2015-01-01",dateformat"y-m-d")` veya `DateTime("20150101",dateformat"yyyymmdd")` şeklindedir.

Sınırlı alanlar, iki ardışık dönem arasında beklenen ayırıcıyı belirterek işaretlenir; bu nedenle `"y-m-d"` ifadesi, bir tarih dizesi olan `"2014-07-16"` içindeki birinci ve ikinci alan arasında `-` karakterinin bulunması gerektiğini belirtir. `y`, `m` ve `d` karakterleri, her alanda hangi dönemlerin ayrıştırılacağını belirtir.

Yukarıda `Date(2013)` gibi yapıcılar için olduğu gibi, sınırlı `DateFormat`'lar, önceki kısımlar verildiği sürece tarih ve saatlerin eksik parçalarına izin verir. Diğer parçalar, alışıldık varsayılan değerleri alır. Örneğin, `Date("1981-03", dateformat"y-m-d")` `1981-03-01` dönerken, `Date("31/12", dateformat"d/m/y")` `0001-12-31` verir. (Varsayılan yılın 1 MS/CE olduğunu unutmayın.) Ancak, boş bir dize her zaman bir `ArgumentError` fırlatır.

Sabit genişlikteki slotlar, karakterler arasında herhangi bir ayırıcı olmaksızın genişliğe karşılık gelen sayıda nokta karakterini tekrarlayarak belirtilir. Bu nedenle `dateformat"yyyymmdd"` ifadesi, `"20140716"` gibi bir tarih dizesine karşılık gelir. Ayrıştırıcı, bir ayırıcı olmamasıyla sabit genişlikteki bir slotu ayırt eder ve bir nokta karakterinden diğerine geçişi `"yyyymm"` olarak not eder.

Metin biçiminde ay ayrıştırma desteği, sırasıyla kısaltılmış ve tam uzunlukta ay adları için `u` ve `U` karakterleri aracılığıyla da desteklenmektedir. Varsayılan olarak, yalnızca İngilizce ay adları desteklenmektedir, bu nedenle `u` "Jan", "Feb", "Mar" vb. ile ilişkilidir. `U` ise "Ocak", "Şubat", "Mart" vb. ile ilişkilidir. Diğer ad=>değer eşleme işlevlerine benzer şekilde [`dayname`](@ref) ve [`monthname`](@ref), özel yereller `MONTHTOVALUEABBR` ve `MONTHTOVALUE` sözlüklerine kısaltılmış ve tam ad ay adları için `locale=>Dict{String,Int}` eşlemesi geçerek yüklenebilir.

Yukarıdaki örnekler `dateformat""` dize makrosunu kullandı. Bu makro, makro genişletildiğinde bir `DateFormat` nesnesi oluşturur ve bir kod parçası birden fazla kez çalıştırılsa bile aynı `DateFormat` nesnesini kullanır.

```jldoctest
julia> for i = 1:10^5
           Date("2015-01-01", dateformat"y-m-d")
       end
```

Ya da DateFormat nesnesini açıkça oluşturabilirsiniz:

```jldoctest
julia> df = DateFormat("y-m-d");

julia> dt = Date("2015-01-01",df)
2015-01-01

julia> dt2 = Date("2015-01-02",df)
2015-01-02
```

Alternatif olarak, yayınlama kullanın:

```jldoctest
julia> years = ["2015", "2016"];

julia> Date.(years, DateFormat("yyyy"))
2-element Vector{Date}:
 2015-01-01
 2016-01-01
```

Kolaylık açısından, format dizesini doğrudan geçebilirsiniz (örneğin, `Date("2015-01-01","y-m-d")`), ancak bu form, aynı formatı tekrar tekrar ayrıştırıyorsanız performans maliyetleri doğurur, çünkü her seferinde yeni bir `DateFormat` nesnesi oluşturur.

`Date` veya `DateTime`, [`parse`](@ref) ve [`tryparse`](@ref) fonksiyonları kullanılarak dizelerden oluşturulabilir, ancak formatı belirten `DateFormat` türünde isteğe bağlı bir üçüncü argüman ile; örneğin, `parse(Date, "06.23.2013", dateformat"m.d.y")` veya varsayılan formatı kullanan `tryparse(DateTime, "1999-12-31T23:59:59")`. Fonksiyonlar arasındaki dikkat çekici fark, `4d61726b646f776e2e436f64652822222c202274727970617273652229_40726566` ile, dize boş veya geçersiz bir formatta olduğunda bir hata fırlatılmamasıdır; bunun yerine `nothing` döndürülür.

!!! compat "Julia 1.9"
    Julia 1.9'dan önce, boş dizeler yapıcılara ve `parse`'a hata vermeden geçirilebiliyordu ve uygun şekilde `DateTime(1)`, `Date(1)` veya `Time(0)` döndürüyordu. Benzer şekilde, `tryparse` da `nothing` döndürmüyordu.


[`stdlib/Dates/test/io.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/io.jl) için tam bir ayrıştırma ve biçimlendirme testleri ve örnekleri mevcuttur.

## Durations/Comparisons

Finding the length of time between two [`Date`](@ref) or [`DateTime`](@ref) is straightforward given their underlying representation as `UTInstant{Day}` and `UTInstant{Millisecond}`, respectively. The difference between [`Date`](@ref) is returned in the number of [`Day`](@ref), and [`DateTime`](@ref) in the number of [`Millisecond`](@ref). Similarly, comparing [`TimeType`](@ref) is a simple matter of comparing the underlying machine instants (which in turn compares the internal [`Int64`](@ref) values).

```jldoctest
julia> dt = Date(2012,2,29)
2012-02-29

julia> dt2 = Date(2000,2,1)
2000-02-01

julia> dump(dt)
Date
  instant: Dates.UTInstant{Day}
    periods: Day
      value: Int64 734562

julia> dump(dt2)
Date
  instant: Dates.UTInstant{Day}
    periods: Day
      value: Int64 730151

julia> dt > dt2
true

julia> dt != dt2
true

julia> dt + dt2
ERROR: MethodError: no method matching +(::Date, ::Date)
[...]

julia> dt * dt2
ERROR: MethodError: no method matching *(::Date, ::Date)
[...]

julia> dt / dt2
ERROR: MethodError: no method matching /(::Date, ::Date)

julia> dt - dt2
4411 days

julia> dt2 - dt
-4411 days

julia> dt = DateTime(2012,2,29)
2012-02-29T00:00:00

julia> dt2 = DateTime(2000,2,1)
2000-02-01T00:00:00

julia> dt - dt2
381110400000 milliseconds
```

## Accessor Functions

Çünkü [`Date`](@ref) ve [`DateTime`](@ref) türleri tek bir [`Int64`](@ref) değeri olarak saklanmaktadır, tarih parçaları veya alanları erişim işlevleri aracılığıyla alınabilir. Küçük harfli erişim işlevleri alanı bir tamsayı olarak döndürür:

```jldoctest tdate
julia> t = Date(2014, 1, 31)
2014-01-31

julia> Dates.year(t)
2014

julia> Dates.month(t)
1

julia> Dates.week(t)
5

julia> Dates.day(t)
31
```

While propercase return the same value in the corresponding [`Period`](@ref) type:

```jldoctest tdate
julia> Dates.Year(t)
2014 years

julia> Dates.Day(t)
31 days
```

Bileşen yöntemler, birden fazla alana aynı anda erişmenin bireysel olarak erişmekten daha verimli olması nedeniyle sağlanmıştır:

```jldoctest tdate
julia> Dates.yearmonth(t)
(2014, 1)

julia> Dates.monthday(t)
(1, 31)

julia> Dates.yearmonthday(t)
(2014, 1, 31)
```

Birisi ayrıca temel `UTInstant` veya tam sayı değerine erişebilir:

```jldoctest tdate
julia> dump(t)
Date
  instant: Dates.UTInstant{Day}
    periods: Day
      value: Int64 735264

julia> t.instant
Dates.UTInstant{Day}(Day(735264))

julia> Dates.value(t)
735264
```

## Query Functions

Sorgu işlevleri, [`TimeType`](@ref) hakkında takvim bilgileri sağlar. Haftanın günü hakkında bilgi içerir:

```jldoctest tdate2
julia> t = Date(2014, 1, 31)
2014-01-31

julia> Dates.dayofweek(t)
5

julia> Dates.dayname(t)
"Friday"

julia> Dates.dayofweekofmonth(t) # 5th Friday of January
5
```

Yılın ayı:

```jldoctest tdate2
julia> Dates.monthname(t)
"January"

julia> Dates.daysinmonth(t)
31
```

[`TimeType`](@ref)'ın yılı ve çeyreği hakkında bilgi ile birlikte:

```jldoctest tdate2
julia> Dates.isleapyear(t)
false

julia> Dates.dayofyear(t)
31

julia> Dates.quarterofyear(t)
1

julia> Dates.dayofquarter(t)
31
```

[`dayname`](@ref) ve [`monthname`](@ref) yöntemleri, diğer diller/yereller için gün veya ay adını döndürmek üzere kullanılabilecek isteğe bağlı bir `locale` anahtar kelimesi alabilir. Ayrıca, kısaltılmış adları döndüren bu işlevlerin versiyonları da vardır; bunlar [`dayabbr`](@ref) ve [`monthabbr`](@ref)'dir. Öncelikle eşleme `LOCALES` değişkenine yüklenir:

```jldoctest tdate2
julia> french_months = ["janvier", "février", "mars", "avril", "mai", "juin",
                        "juillet", "août", "septembre", "octobre", "novembre", "décembre"];

julia> french_months_abbrev = ["janv","févr","mars","avril","mai","juin",
                              "juil","août","sept","oct","nov","déc"];

julia> french_days = ["lundi","mardi","mercredi","jeudi","vendredi","samedi","dimanche"];

julia> Dates.LOCALES["french"] = Dates.DateLocale(french_months, french_months_abbrev, french_days, [""]);
```

Yukarıda bahsedilen fonksiyonlar, sorguları gerçekleştirmek için kullanılabilir:

```jldoctest tdate2
julia> Dates.dayname(t;locale="french")
"vendredi"

julia> Dates.monthname(t;locale="french")
"janvier"

julia> Dates.monthabbr(t;locale="french")
"janv"
```

Kısaltılmış gün versiyonları yüklenmediğinden, `dayabbr` fonksiyonunu kullanmaya çalışmak bir hata verecektir.

```jldoctest tdate2
julia> Dates.dayabbr(t;locale="french")
ERROR: BoundsError: attempt to access 1-element Vector{String} at index [5]
Stacktrace:
[...]
```

## TimeType-Period Arithmetic

Herhangi bir dil/tarih çerçevesi kullanırken, tarih-dönem aritmetiğinin nasıl ele alındığını bilmek iyi bir uygulamadır, çünkü bazı [tricky issues](https://codeblog.jonskeet.uk/2010/12/01/the-joys-of-date-time-arithmetic/) ile başa çıkmak gerekir (gün hassasiyetine sahip türler için çok daha az).

`Dates` modülü yaklaşımı, [`Period`](@ref) aritmetiği yaparken mümkün olduğunca az değişiklik yapma basit ilkesini takip etmeye çalışır. Bu yaklaşım genellikle *takvimsel* aritmetik olarak da bilinir veya birinin size aynı hesaplamayı bir konuşmada sorması durumunda muhtemelen tahmin edeceğiniz şeydir. Bununla neden bu kadar çok uğraşılıyor? Klasik bir örneğe bakalım: 31 Ocak 2014'e 1 ay ekleyin. Cevap nedir? Javascript [March 3](https://markhneedham.com/blog/2009/01/07/javascript-add-a-month-to-a-date/) (31 gün varsayıyor) diyecektir. PHP ise [March 2](https://stackoverflow.com/questions/5760262/php-adding-months-to-a-date-while-not-exceeding-the-last-day-of-the-month) (30 gün varsayıyor) diyecektir. Gerçek şu ki, doğru bir cevap yoktur. `Dates` modülünde sonuç 28 Şubat olarak verilmektedir. Bunu nasıl hesaplıyor? Kumarhanelerdeki klasik 7-7-7 kumar oyununu düşünün.

Şimdi sadece hayal edin ki 7-7-7 yerine, slotlar Yıl-Ay-Gün şeklinde, ya da bizim örneğimizde, 2014-01-31. Bu tarihe 1 ay eklemek istediğinizde, ay slotu artırılır, böylece artık 2014-02-31'imiz var. Ardından, gün numarasının yeni ayın son geçerli gününden büyük olup olmadığı kontrol edilir; eğer büyükse (yukarıdaki durumda olduğu gibi), gün numarası son geçerli güne (28) ayarlanır. Bu yaklaşımın sonuçları nelerdir? Hadi tarihimize bir ay ekleyelim, `2014-02-28 + Ay(1) == 2014-03-28`. Ne? Mart ayının son günü mü bekliyordunuz? Hayır, üzgünüm, 7-7-7 slotlarını hatırlayın. Mümkün olduğunca az slot değişecek, bu yüzden önce ay slotunu 1 artırıyoruz, 2014-03-28 ve boom, işimiz bitti çünkü bu geçerli bir tarih. Öte yandan, orijinal tarihe 2 ay eklersek, 2014-01-31, o zaman beklenildiği gibi 2014-03-31 ile karşılaşırız. Bu yaklaşımın diğer bir sonucu, belirli bir sıralamanın zorlandığı durumlarda (yani, farklı sıralarda ekleme yapmak farklı sonuçlar doğurur) bir birleşme kaybıdır. Örneğin:

```jldoctest
julia> (Date(2014,1,29)+Dates.Day(1)) + Dates.Month(1)
2014-02-28

julia> (Date(2014,1,29)+Dates.Month(1)) + Dates.Day(1)
2014-03-01
```

Orada ne oluyor? İlk satırda, 29 Ocak'a 1 gün ekliyoruz, bu da 2014-01-30 sonucunu veriyor; ardından 1 ay ekliyoruz, bu da 2014-02-30 sonucunu veriyor, bu da 2014-02-28'e ayarlanıyor. İkinci örnekte, önce 1 ay ekliyoruz, burada 2014-02-29 elde ediyoruz, bu da 2014-02-28'e ayarlanıyor ve *sonra* 1 gün ekliyoruz, bu da 2014-03-01 sonucunu veriyor. Bu durumda yardımcı olan bir tasarım ilkesi, birden fazla Dönem bulunduğunda, işlemlerin Dönemlerin *türlerine* göre sıralanmasıdır, değerlerine veya konumsal sıralarına göre değil; bu, `Yıl`'ın her zaman önce ekleneceği, ardından `Ay`, sonra `Hafta` vb. olacağı anlamına gelir. Bu nedenle aşağıdaki *birliktelik* sağlar ve İşler:

```jldoctest
julia> Date(2014,1,29) + Dates.Day(1) + Dates.Month(1)
2014-03-01

julia> Date(2014,1,29) + Dates.Month(1) + Dates.Day(1)
2014-03-01
```

Karmaşık mı? Belki. Masum bir `Dates` kullanıcısı ne yapsın? Sonuç olarak, aylarla ilgili bir belirli bir ilişkilendirmeyi açıkça zorlamanın bazı beklenmedik sonuçlara yol açabileceğini bilmek önemlidir, ancak aksi takdirde her şey beklenildiği gibi çalışmalıdır. Neyse ki, bu, UT'de zamanla ilgili tarih-dönem aritmetiğinde karşılaşılan garip durumların neredeyse tamamıdır (gündüz tasarrufu, artık saniyeler vb. ile başa çıkmanın "sevinçlerinden" kaçınarak).

Bir bonus olarak, tüm dönem aritmetik nesneleri doğrudan aralıklarla çalışır:

```jldoctest
julia> dr = Date(2014,1,29):Day(1):Date(2014,2,3)
Date("2014-01-29"):Day(1):Date("2014-02-03")

julia> collect(dr)
6-element Vector{Date}:
 2014-01-29
 2014-01-30
 2014-01-31
 2014-02-01
 2014-02-02
 2014-02-03

julia> dr = Date(2014,1,29):Dates.Month(1):Date(2014,07,29)
Date("2014-01-29"):Month(1):Date("2014-07-29")

julia> collect(dr)
7-element Vector{Date}:
 2014-01-29
 2014-02-28
 2014-03-29
 2014-04-29
 2014-05-29
 2014-06-29
 2014-07-29
```

## Adjuster Functions

Tarih aritmetiği ne kadar kullanışlı olsa da, genellikle tarihler üzerinde gereken hesaplamalar, sabit bir dönem sayısından ziyade *takvimsel* veya *zamansal* bir nitelik taşır. Tatiller mükemmel bir örnektir; çoğu "Anma Günü = Mayıs'ın Son Pazartesi'si" veya "Şükran Günü = Kasım'ın 4. Perşembesi" gibi kuralları takip eder. Bu tür zamansal ifadeler, ayın ilk veya son günü, gelecek Salı veya birinci ve üçüncü Çarşamba gibi takvimle ilgili kurallarla ilgilidir.

`Dates` modülü, zamansal kuralları basit ve özlü bir şekilde ifade etmeye yardımcı olan birkaç kullanışlı yöntem aracılığıyla *ayarlayıcı* API'sini sağlar. Ayarlayıcı yöntemlerin ilk grubu, haftaların, ayların, çeyreklerin ve yılların ilk ve sonlarıyla ilgilidir. Her biri tek bir [`TimeType`](@ref) girişi alır ve girdiyle ilgili olarak istenen dönemin ilk veya sonuna *ayarlar* veya döner.

```jldoctest
julia> Dates.firstdayofweek(Date(2014,7,16)) # Adjusts the input to the Monday of the input's week
2014-07-14

julia> Dates.lastdayofmonth(Date(2014,7,16)) # Adjusts to the last day of the input's month
2014-07-31

julia> Dates.lastdayofquarter(Date(2014,7,16)) # Adjusts to the last day of the input's quarter
2014-09-30
```

Sonraki iki yüksek dereceli yöntem, [`tonext`](@ref) ve [`toprev`](@ref), bir `DateFunction`'ı ilk argüman olarak alarak ve bir başlangıç [`TimeType`](@ref) ile birlikte zamansal ifadelerle çalışmayı genelleştirir. Bir `DateFunction`, genellikle anonim olan ve tek bir `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566` girişi alan ve bir [`Bool`](@ref) döndüren bir işlevdir; `true`, tatmin edici bir ayarlama kriterini gösterir. Örneğin:

```jldoctest
julia> istuesday = x->Dates.dayofweek(x) == Dates.Tuesday; # Returns true if the day of the week of x is Tuesday

julia> Dates.tonext(istuesday, Date(2014,7,13)) # 2014-07-13 is a Sunday
2014-07-15

julia> Dates.tonext(Date(2014,7,13), Dates.Tuesday) # Convenience method provided for day of the week adjustments
2014-07-15
```

Bu, daha karmaşık zamansal ifadeler için do-block sözdizimi ile kullanışlıdır:

```jldoctest
julia> Dates.tonext(Date(2014,7,13)) do x
           # Return true on the 4th Thursday of November (Thanksgiving)
           Dates.dayofweek(x) == Dates.Thursday &&
           Dates.dayofweekofmonth(x) == 4 &&
           Dates.month(x) == Dates.November
       end
2014-11-27
```

[`Base.filter`](@ref) yöntemi, belirli bir aralıktaki tüm geçerli tarihleri/anları elde etmek için kullanılabilir:

```jldoctest
# Pittsburgh street cleaning; Every 2nd Tuesday from April to November
# Date range from January 1st, 2014 to January 1st, 2015
julia> dr = Dates.Date(2014):Day(1):Dates.Date(2015);

julia> filter(dr) do x
           Dates.dayofweek(x) == Dates.Tue &&
           Dates.April <= Dates.month(x) <= Dates.Nov &&
           Dates.dayofweekofmonth(x) == 2
       end
8-element Vector{Date}:
 2014-04-08
 2014-05-13
 2014-06-10
 2014-07-08
 2014-08-12
 2014-09-09
 2014-10-14
 2014-11-11
```

Ekstra örnekler ve testler [`stdlib/Dates/test/adjusters.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/adjusters.jl) adresinde mevcuttur.

## Period Types

Dönemler, zamanın kesik, bazen düzensiz sürelerini insan bakış açısıyla değerlendiren bir kavramdır. 1 ayı düşünün; bu, yıl ve ay bağlamına bağlı olarak gün olarak 28, 29, 30 veya 31 değerini temsil edebilir. Ya da bir yıl, artık yıl durumunda 365 veya 366 gün olarak temsil edilebilir. [`Period`](@ref) türleri basit [`Int64`](@ref) sarmalayıcılarıdır ve herhangi bir `Int64` dönüştürülebilir türü sarmalayarak oluşturulmuştur, yani `Year(1)` veya `Month(3.0)`. Aynı türdeki `4d61726b646f776e2e436f64652822222c2022506572696f642229_40726566` arasındaki aritmetik, tıpkı tam sayılar gibi davranır ve sınırlı `Period-Real` aritmetiği mevcuttur. Temel tam sayıyı [`Dates.value`](@ref) ile çıkarabilirsiniz.

```jldoctest
julia> y1 = Dates.Year(1)
1 year

julia> y2 = Dates.Year(2)
2 years

julia> y3 = Dates.Year(10)
10 years

julia> y1 + y2
3 years

julia> div(y3,y2)
5

julia> y3 - y2
8 years

julia> y3 % y2
0 years

julia> div(y3,3) # mirrors integer division
3 years

julia> Dates.value(Dates.Millisecond(10))
10
```

Dönemleri veya temel türlerin tam katları olmayan süreleri temsil etmek, [`Dates.CompoundPeriod`](@ref) türü ile gerçekleştirilebilir. Bileşik dönemler, basit [`Period`](@ref) türlerinden manuel olarak oluşturulabilir. Ayrıca, [`canonicalize`](@ref) fonksiyonu, bir dönemi `4d61726b646f776e2e436f64652822222c202244617465732e436f6d706f756e64506572696f642229_40726566`'ya ayırmak için kullanılabilir. Bu, bir süreyi, örneğin, iki `DateTime` arasındaki farkı, daha uygun bir temsile dönüştürmek için özellikle yararlıdır.

```jldoctest
julia> cp = Dates.CompoundPeriod(Day(1),Minute(1))
1 day, 1 minute

julia> t1 = DateTime(2018,8,8,16,58,00)
2018-08-08T16:58:00

julia> t2 = DateTime(2021,6,23,10,00,00)
2021-06-23T10:00:00

julia> canonicalize(t2-t1) # creates a CompoundPeriod
149 weeks, 6 days, 17 hours, 2 minutes
```

## Rounding

[`Date`](@ref) ve [`DateTime`](@ref) değerleri, [`floor`](@ref), [`ceil`](@ref) veya [`round`](@ref) ile belirtilen bir çözünürlüğe (örneğin, 1 ay veya 15 dakika) yuvarlanabilir:

```jldoctest
julia> floor(Date(1985, 8, 16), Dates.Month)
1985-08-01

julia> ceil(DateTime(2013, 2, 13, 0, 31, 20), Dates.Minute(15))
2013-02-13T00:45:00

julia> round(DateTime(2016, 8, 6, 20, 15), Dates.Day)
2016-08-07T00:00:00
```

[`round`](@ref) yönteminin varsayılan olarak eşit sayılara doğru bağları kırdığı [`TimeType`](@ref)`4d61726b646f776e2e436f64652822222c2022726f756e642229_40726566` yönteminin `RoundNearestTiesUp` yuvarlama modunu kullandığı gibi. (Eşit sayılara en yakın "çift" `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566` bağlarını kırmanın ne anlama geleceğini tahmin etmek zordur.) Mevcut `RoundingMode` lar hakkında daha fazla ayrıntı [API reference](@ref stdlib-dates-api) içinde bulunabilir.

Yuvarlama genellikle beklenildiği gibi davranmalıdır, ancak beklenen davranışın belirgin olmadığı birkaç durum vardır.

### Rounding Epoch

Birçok durumda, yuvarlama için belirtilen çözünürlük (örneğin, `Dates.Second(30)`) bir sonraki en büyük döneme (bu durumda, `Dates.Minute(1)`) tam olarak bölünür. Ancak, bunun doğru olmadığı durumlarda yuvarlama davranışı kafa karışıklığına yol açabilir. [`DateTime`](@ref) değerini en yakın 10 saate yuvarlamanın beklenen sonucu nedir?

```jldoctest
julia> round(DateTime(2016, 7, 17, 11, 55), Dates.Hour(10))
2016-07-17T12:00:00
```

Bu kafa karıştırıcı görünebilir, çünkü saat (12) 10'a tam bölünemez. `2016-07-17T12:00:00`'ın seçilmesinin nedeni, `0000-01-01T00:00:00`'dan 17,676,660 saat sonra olmasıdır ve 17,676,660 sayısı 10'a tam bölünebilir.

Julia [`Date`](@ref) ve [`DateTime`](@ref) değerleri ISO 8601 standardına göre temsil edilmektedir, `0000-01-01T00:00:00` günlerin (ve milisaniyelerin) yuvarlama hesaplamalarında kullanılacak olan sayımın başlangıcı (veya "yuvarlama epoch'u") olarak seçilmiştir. (Bu, Julia'nın `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` değerlerini [Rata Die notation](https://en.wikipedia.org/wiki/Rata_Die) kullanarak içsel temsilinden biraz farklıdır; ancak ISO 8601 standardı son kullanıcıya en görünür olanı olduğu için, karışıklığı en aza indirmek amacıyla yuvarlama epoch'u olarak `0000-01-01T00:00:00` seçilmiştir, içsel olarak kullanılan `0000-12-31T00:00:00` yerine.)

`0000-01-01T00:00:00` olarak yuvarlama epokası kullanma konusundaki tek istisna, haftalara yuvarlamadır. En yakın haftaya yuvarlama her zaman bir Pazartesi (ISO 8601 tarafından belirtilen haftanın ilk günü) dönecektir. Bu nedenle, haftalara yuvarlarken `0000-01-03T00:00:00` (ISO 8601 tarafından tanımlanan yıl 0000'ın ilk haftasının ilk günü) temel olarak kullanılır.

İşte beklenen davranışın kesinlikle belirgin olmadığı ilgili bir durum: `P(2)`'ye en yakın değere yuvarladığımızda ne olur, burada `P` bir [`Period`](@ref) türüdür? Bazı durumlarda (özellikle `P <: Dates.TimePeriod` olduğunda) cevap nettir:

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Hour(2))
2016-07-17T08:00:00

julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Minute(2))
2016-07-17T08:56:00
```

Bu, her bir bu dönemden ikisinin bir sonraki daha büyük dönemle eşit şekilde bölünmesi nedeniyle açık görünüyor. Ancak iki ay durumu (bir yıla hala eşit şekilde bölünebilen) için cevap şaşırtıcı olabilir:

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Month(2))
2016-07-01T00:00:00
```

Neden Temmuz'un ilk gününe yuvarlanıyor, oysa bu 7. ay (tek bir sayı)? Anahtar, ayların 1'den başladığıdır (ilk ay 1 olarak atanır), saatler, dakikalar, saniyeler ve milisaniyeler gibi (ilk olanlar 0 olarak atanır).

Bu, [`DateTime`](@ref) değerinin saniye, dakika, saat veya yıl gibi çift bir katına yuvarlanmasının (çünkü ISO 8601 spesifikasyonu sıfır yılı içerir) o alanda çift bir değere sahip bir `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` ile sonuçlanacağı anlamına gelirken, `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` değerinin çift bir katına ay olarak yuvarlanmasının aylar alanının tek bir değere sahip olacağı anlamına gelir. Hem ayların hem de yılların düzensiz sayıda gün içerebileceğinden, çift bir gün sayısına yuvarlamanın günler alanında çift bir değere yol açıp açmayacağı belirsizdir.

`Dates` modülünden dışa aktarılan yöntemler hakkında ek bilgi için [API reference](@ref stdlib-dates-api)'ye bakın.

## [API reference](@id stdlib-dates-api)

### Dates and Time Types

```@docs
Dates.Period
Dates.CompoundPeriod
Dates.Instant
Dates.UTInstant
Dates.TimeType
Dates.DateTime
Dates.Date
Dates.Time
Dates.TimeZone
Dates.UTC
```

### Dates Functions

```@docs
Dates.DateTime(::Int64, ::Int64, ::Int64, ::Int64, ::Int64, ::Int64, ::Int64)
Dates.DateTime(::Dates.Period)
Dates.DateTime(::Function, ::Any...)
Dates.DateTime(::Dates.TimeType)
Dates.DateTime(::AbstractString, ::AbstractString)
Dates.format(::Dates.TimeType, ::AbstractString)
Dates.DateFormat
Dates.@dateformat_str
Dates.DateTime(::AbstractString, ::Dates.DateFormat)
Dates.Date(::Int64, ::Int64, ::Int64)
Dates.Date(::Dates.Period)
Dates.Date(::Function, ::Any, ::Any, ::Any)
Dates.Date(::Dates.TimeType)
Dates.Date(::AbstractString, ::AbstractString)
Dates.Date(::AbstractString, ::Dates.DateFormat)
Dates.Time(::Int64::Int64, ::Int64, ::Int64, ::Int64, ::Int64)
Dates.Time(::Dates.TimePeriod)
Dates.Time(::Function, ::Any...)
Dates.Time(::Dates.DateTime)
Dates.Time(::AbstractString, ::AbstractString)
Dates.Time(::AbstractString, ::Dates.DateFormat)
Dates.now()
Dates.now(::Type{Dates.UTC})
Base.eps(::Union{Type{DateTime}, Type{Date}, Type{Time}, TimeType})
```

#### Accessor Functions

```@docs
Dates.year
Dates.month
Dates.week
Dates.day
Dates.hour
Dates.minute
Dates.second
Dates.millisecond
Dates.microsecond
Dates.nanosecond
Dates.Year(::Dates.TimeType)
Dates.Month(::Dates.TimeType)
Dates.Week(::Dates.TimeType)
Dates.Day(::Dates.TimeType)
Dates.Hour(::DateTime)
Dates.Minute(::DateTime)
Dates.Second(::DateTime)
Dates.Millisecond(::DateTime)
Dates.Microsecond(::Dates.Time)
Dates.Nanosecond(::Dates.Time)
Dates.yearmonth
Dates.monthday
Dates.yearmonthday
```

#### Query Functions

```@docs
Dates.dayname
Dates.dayabbr
Dates.dayofweek
Dates.dayofmonth
Dates.dayofweekofmonth
Dates.daysofweekinmonth
Dates.monthname
Dates.monthabbr
Dates.daysinmonth
Dates.isleapyear
Dates.dayofyear
Dates.daysinyear
Dates.quarterofyear
Dates.dayofquarter
```

#### Adjuster Functions

```@docs
Base.trunc(::Dates.TimeType, ::Type{Dates.Period})
Dates.firstdayofweek
Dates.lastdayofweek
Dates.firstdayofmonth
Dates.lastdayofmonth
Dates.firstdayofyear
Dates.lastdayofyear
Dates.firstdayofquarter
Dates.lastdayofquarter
Dates.tonext(::Dates.TimeType, ::Int)
Dates.toprev(::Dates.TimeType, ::Int)
Dates.tofirst
Dates.tolast
Dates.tonext(::Function, ::Dates.TimeType)
Dates.toprev(::Function, ::Dates.TimeType)
```

#### Periods

```@docs
Dates.Period(::Any)
Dates.CompoundPeriod(::Vector{<:Dates.Period})
Dates.canonicalize
Dates.value
Dates.default
Dates.periods
```

#### Rounding Functions

`Tarih` ve `TarihSaat` değerleri, `floor`, `ceil` veya `round` ile belirli bir çözünürlüğe (örneğin, 1 ay veya 15 dakika) yuvarlanabilir.

```@docs
Base.floor(::Dates.TimeType, ::Dates.Period)
Base.ceil(::Dates.TimeType, ::Dates.Period)
Base.round(::Dates.TimeType, ::Dates.Period, ::RoundingMode{:NearestTiesUp})
```

Çoğu `Period` değeri, belirli bir çözünürlüğe yuvarlanabilir:

```@docs
Base.floor(::Dates.ConvertiblePeriod, ::T) where T <: Dates.ConvertiblePeriod
Base.ceil(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod)
Base.round(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod, ::RoundingMode{:NearestTiesUp})
```

Aşağıdaki fonksiyonlar dışa aktarılmamıştır:

```@docs
Dates.floorceil
Dates.epochdays2date
Dates.epochms2datetime
Dates.date2epochdays
Dates.datetime2epochms
```

#### Conversion Functions

```@docs
Dates.today
Dates.unix2datetime
Dates.datetime2unix
Dates.julian2datetime
Dates.datetime2julian
Dates.rata2datetime
Dates.datetime2rata
```

### Constants

Haftanın Günleri:

| Variable    | Abbr. | Value (Int) |
|:----------- |:----- |:----------- |
| `Monday`    | `Mon` | 1           |
| `Tuesday`   | `Tue` | 2           |
| `Wednesday` | `Wed` | 3           |
| `Thursday`  | `Thu` | 4           |
| `Friday`    | `Fri` | 5           |
| `Saturday`  | `Sat` | 6           |
| `Sunday`    | `Sun` | 7           |

Yılın Ayları:

| Variable    | Abbr. | Value (Int) |
|:----------- |:----- |:----------- |
| `January`   | `Jan` | 1           |
| `February`  | `Feb` | 2           |
| `March`     | `Mar` | 3           |
| `April`     | `Apr` | 4           |
| `May`       | `May` | 5           |
| `June`      | `Jun` | 6           |
| `July`      | `Jul` | 7           |
| `August`    | `Aug` | 8           |
| `September` | `Sep` | 9           |
| `October`   | `Oct` | 10          |
| `November`  | `Nov` | 11          |
| `December`  | `Dec` | 12          |

#### Common Date Formatters

```@docs
ISODateTimeFormat
ISODateFormat
ISOTimeFormat
RFC1123Format
```

```@meta
DocTestSetup = nothing
```
