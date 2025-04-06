```
@testset [ÖzelTestSet] [seçenekler...] ["açıklama"] begin test_ex end
@testset [ÖzelTestSet] [seçenekler...] ["açıklama $v"] for v in itr test_ex end
@testset [ÖzelTestSet] [seçenekler...] ["açıklama $v, $w"] for v in itrv, w in itrw test_ex end
@testset [ÖzelTestSet] [seçenekler...] ["açıklama"] test_func()
@testset let v = v, w = w; test_ex; end
```

# begin/end veya fonksiyon çağrısı ile

@testset kullanıldığında, begin/end veya tek bir fonksiyon çağrısı ile, makro verilen ifadeyi değerlendirmek için yeni bir test seti başlatır.

Eğer özel bir test seti türü verilmezse, varsayılan olarak `DefaultTestSet` oluşturulur. `DefaultTestSet`, tüm sonuçları kaydeder ve eğer herhangi bir `Fail` veya `Error` varsa, üst düzey (iç içe olmayan) test setinin sonunda bir istisna fırlatır ve test sonuçlarının bir özetini sunar.

Herhangi bir özel test seti türü ( `AbstractTestSet` alt türü) verilebilir ve bu, iç içe `@testset` çağrıları için de kullanılacaktır. Verilen seçenekler yalnızca verildikleri test setine uygulanır. Varsayılan test seti türü üç boolean seçeneği kabul eder:

  * `verbose`: `true` ise, iç içe test setlerinin sonuç özeti, hepsi geçtiğinde bile gösterilir (varsayılan `false`).
  * `showtiming`: `true` ise, her gösterilen test setinin süresi gösterilir (varsayılan `true`).
  * `failfast`: `true` ise, herhangi bir test hatası veya hatası, test setinin ve herhangi bir alt test setinin hemen dönmesine neden olur (varsayılan `false`). Bu, ayrıca `JULIA_TEST_FAILFAST` ortam değişkeni aracılığıyla küresel olarak ayarlanabilir.

!!! uyumluluk "Julia 1.8"
    `@testset test_func()` en az Julia 1.8 gerektirir.


!!! uyumluluk "Julia 1.9"
    `failfast` en az Julia 1.9 gerektirir.


Açıklama dizesi döngü indekslerinden interpolasyonu kabul eder. Eğer açıklama sağlanmazsa, değişkenlere dayalı olarak bir tane oluşturulur. Eğer bir fonksiyon çağrısı sağlanırsa, adı kullanılacaktır. Açık açıklama dizeleri bu davranışı geçersiz kılar.

Varsayılan olarak `@testset` makrosu test seti nesnesinin kendisini döndürecektir, ancak bu davranış diğer test seti türlerinde özelleştirilebilir. Eğer bir `for` döngüsü kullanılıyorsa, makro `finish` yönteminin döndürdüğü değerlerin bir listesini toplar ve döndürür; bu, varsayılan olarak her yinelemede kullanılan test seti nesnelerinin bir listesini döndürecektir.

`@testset` gövdesinin yürütülmesinden önce, `Random.seed!(seed)`'e örtük bir çağrı vardır; burada `seed`, küresel RNG'nin mevcut tohumudur. Ayrıca, gövdenin yürütülmesinden sonra, küresel RNG'nin durumu `@testset` öncesindeki haline geri yüklenir. Bu, başarısızlık durumunda yeniden üretilebilirliği kolaylaştırmak ve `@testset`'lerin küresel RNG durumu üzerindeki yan etkilerine bakılmaksızın sorunsuz yeniden düzenlenmesine izin vermek içindir.

## Örnekler

```jldoctest; filter = r"trigonometric identities |    4      4  [0-9\.]+s"
julia> @testset "trigonometric identities" begin
           θ = 2/3*π
           @test sin(-θ) ≈ -sin(θ)
           @test cos(-θ) ≈ cos(θ)
           @test sin(2θ) ≈ 2*sin(θ)*cos(θ)
           @test cos(2θ) ≈ cos(θ)^2 - sin(θ)^2
       end;
Test Summary:            | Pass  Total  Time
trigonometric identities |    4      4  0.2s
```

# `@testset for`

`@testset for` kullanıldığında, makro sağlanan döngünün her yinelemesi için yeni bir test başlatır. Her test setinin anlamı, `begin/end` durumundaki ile aynıdır (her döngü yinelemesi için kullanılmış gibi).

# `@testset let`

`@testset let` kullanıldığında, makro verilen nesneyi içindeki herhangi bir başarısız test için bir bağlam nesnesi olarak ekleyerek *şeffaf* bir test seti başlatır. Bu, bir büyük nesne üzerinde bir dizi ilgili test gerçekleştirirken ve bireysel testlerden herhangi biri başarısız olduğunda bu büyük nesneyi yazdırmak istenildiğinde faydalıdır. Şeffaf test setleri, test seti hiyerarşisinde ek iç içe katmanlar oluşturmaz ve doğrudan üst test setine geçilir (bağlam nesnesi herhangi bir başarısız testin yanına eklenir).

!!! uyumluluk "Julia 1.9"
    `@testset let` en az Julia 1.9 gerektirir.


!!! uyumluluk "Julia 1.10"
    Birden fazla `let` ataması, Julia 1.10'dan itibaren desteklenmektedir.


## Örnekler

```jldoctest
julia> @testset let logi = log(im)
           @test imag(logi) == π/2
           @test !iszero(real(logi))
       end
Test Failed at none:3
  Expression: !(iszero(real(logi)))
     Context: logi = 0.0 + 1.5707963267948966im

HATA: Test sırasında bir hata oluştu

julia> @testset let logi = log(im), op = !iszero
           @test imag(logi) == π/2
           @test op(real(logi))
       end
Test Failed at none:3
  Expression: op(real(logi))
     Context: logi = 0.0 + 1.5707963267948966im
              op = !iszero

HATA: Test sırasında bir hata oluştu
```
