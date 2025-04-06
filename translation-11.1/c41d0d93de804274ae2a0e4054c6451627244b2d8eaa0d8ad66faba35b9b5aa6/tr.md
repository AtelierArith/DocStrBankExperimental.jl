```
@test ex
@test f(args...) key=val ...
@test ex broken=true
@test ex skip=true
```

`ex` ifadesinin `true` değerine eşit olduğunu test edin. Eğer bir `@testset` içinde çalıştırılırsa, `true` ise `Pass` `Result` döndürün, `false` ise `Fail` `Result` döndürün ve değerlendirilemezse `Error` `Result` döndürün. Eğer bir `@testset` dışında çalıştırılırsa, `Fail` veya `Error` döndürmek yerine bir istisna fırlatın.

# Örnekler

```jldoctest
julia> @test true
Test Geçti

julia> @test [1, 2] + [2, 1] == [3, 3]
Test Geçti
```

`@test f(args...) key=val...` biçimi, `@test f(args..., key=val...)` yazmakla eşdeğerdir ve bu, ifadenin yaklaşık karşılaştırmalar gibi infiks sözdizimi kullanan bir çağrı olması durumunda yararlı olabilir:

```jldoctest
julia> @test π ≈ 3.14 atol=0.01
Test Geçti
```

Bu, daha çirkin bir test olan `@test ≈(π, 3.14, atol=0.01)` ile eşdeğerdir. İlk ifade bir çağrı ifadesi olmadıkça birden fazla ifade sağlamak bir hatadır ve geri kalanlar atama (`k=v`) olmalıdır.

`key=val` argümanları için herhangi bir anahtar kullanabilirsiniz, ancak `broken` ve `skip` anahtarları, `@test` bağlamında özel anlamlara sahiptir:

  * `broken=cond`, `cond==true` olduğunda geçmesi gereken ancak şu anda sürekli olarak başarısız olan bir testi belirtir. `ex` ifadesinin `false` değerine eşit olduğunu veya bir istisna oluşturduğunu test eder. Eğer öyleyse `Broken` `Result` döndürür veya ifade `true` değerine eşit olursa `Error` `Result` döndürür. `cond==false` olduğunda normal `@test ex` değerlendirilir.
  * `skip=cond`, `cond==true` olduğunda çalıştırılmaması gereken ancak test özeti raporlamasında `Broken` olarak dahil edilmesi gereken bir testi işaretler. Bu, aralıklı olarak başarısız olan testler veya henüz uygulanmamış işlevsellik testleri için yararlı olabilir. `cond==false` olduğunda normal `@test ex` değerlendirilir.

# Örnekler

```jldoctest
julia> @test 2 + 2 ≈ 6 atol=1 broken=true
Test Bozuk
  İfade: ≈(2 + 2, 6, atol = 1)

julia> @test 2 + 2 ≈ 5 atol=1 broken=false
Test Geçti

julia> @test 2 + 2 == 5 skip=true
Test Bozuk
  Atlandı: 2 + 2 == 5

julia> @test 2 + 2 == 4 skip=false
Test Geçti
```

!!! uyumluluk "Julia 1.7"
    `broken` ve `skip` anahtar argümanları en az Julia 1.7 gerektirir.

