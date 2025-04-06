```
@test_broken ex
@test_broken f(args...) key=val ...
```

Başarılı olması gereken ancak şu anda sürekli olarak başarısız olan bir testi belirtir. `ex` ifadesinin `false` değerini döndürdüğünü veya bir istisna oluşturduğunu test eder. Eğer öyleyse, bir `Broken` `Result` döner; aksi takdirde, ifade `true` değerini dönerse bir `Error` `Result` döner. Bu, [`@test ex broken=true`](@ref @test) ile eşdeğerdir.

`@test_broken f(args...) key=val...` biçimi, `@test` makrosu için olduğu gibi çalışır.

# Örnekler

```jldoctest
julia> @test_broken 1 == 2
Test Broken
  İfade: 1 == 2

julia> @test_broken 1 == 2 atol=0.1
Test Broken
  İfade: ==(1, 2, atol = 0.1)
```
