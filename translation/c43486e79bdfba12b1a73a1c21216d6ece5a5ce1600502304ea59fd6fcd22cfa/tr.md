```
@test_skip ex
@test_skip f(args...) key=val ...
```

Testin çalıştırılmaması gereken bir testi işaretler, ancak test özeti raporlamasında `Broken` olarak dahil edilmelidir. Bu, aralıklı olarak başarısız olan testler veya henüz uygulanmamış işlevselliğin testleri için yararlı olabilir. Bu, [`@test ex skip=true`](@ref @test) ile eşdeğerdir.

`@test_skip f(args...) key=val...` biçimi, `@test` makrosu için olduğu gibi çalışır.

# Örnekler

```jldoctest
julia> @test_skip 1 == 2
Test Broken
  Skipped: 1 == 2

julia> @test_skip 1 == 2 atol=0.1
Test Broken
  Skipped: ==(1, 2, atol = 0.1)
```
