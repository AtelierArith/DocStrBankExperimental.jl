```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Test/docs/src/index.md"
```

# Unit Testing

```@meta
DocTestSetup = :(using Test)
```

## Testing Base Julia

Julia, hızlı bir geliştirme sürecindedir ve birden fazla platformda işlevselliği doğrulamak için kapsamlı bir test paketi bulunmaktadır. Eğer Julia'yı kaynak kodundan derlerseniz, bu test paketini `make test` komutuyla çalıştırabilirsiniz. Bir ikili kurulumda ise test paketini `Base.runtests()` kullanarak çalıştırabilirsiniz.

```@docs
Base.runtests
```

## Basic Unit Tests

`Test` modülü basit *birim testi* işlevselliği sağlar. Birim testi, kodunuzun doğru olup olmadığını görmek için sonuçların beklediğiniz gibi olup olmadığını kontrol etmenin bir yoludur. Değişiklikler yaptıktan sonra kodunuzun hala çalıştığından emin olmak için yararlı olabilir ve tamamlandığında kodunuzun sahip olması gereken davranışları belirtmek için geliştirme sırasında kullanılabilir. Ayrıca, [adding tests to your Julia Package](https://pkgdocs.julialang.org/dev/creating-packages/#Adding-tests-to-the-package) için belgeleri de incelemek isteyebilirsiniz.

Basit bir birim testi `@test` ve `@test_throws` makroları ile gerçekleştirilebilir:

```@docs
Test.@test
Test.@test_throws
```

Örneğin, yeni fonksiyonumuzun `foo(x)` beklenildiği gibi çalışıp çalışmadığını kontrol etmek istiyoruz:

```jldoctest testfoo
julia> using Test

julia> foo(x) = length(x)^2
foo (generic function with 1 method)
```

Eğer koşul doğruysa, bir `Pass` döndürülür:

```jldoctest testfoo
julia> @test foo("bar") == 9
Test Passed

julia> @test foo("fizz") >= 10
Test Passed
```

Eğer koşul yanlışsa, o zaman bir `Fail` döndürülür ve bir istisna fırlatılır:

```jldoctest testfoo
julia> @test foo("f") == 20
Test Failed at none:1
  Expression: foo("f") == 20
   Evaluated: 1 == 20

ERROR: There was an error during testing
```

Eğer bir istisna fırlatıldığı için koşul değerlendirilemezse, bu durumda `length` semboller için tanımlı olmadığı için bir `Error` nesnesi döndürülür ve bir istisna fırlatılır:

```julia-repl
julia> @test foo(:cat) == 1
Error During Test
  Test threw an exception of type MethodError
  Expression: foo(:cat) == 1
  MethodError: no method matching length(::Symbol)
  The function `length` exists, but no method is defined for this combination of argument types.

  Closest candidates are:
    length(::SimpleVector) at essentials.jl:256
    length(::Base.MethodList) at reflection.jl:521
    length(::MethodTable) at reflection.jl:597
    ...
  Stacktrace:
  [...]
ERROR: There was an error during testing
```

Eğer bir ifadenin *bir istisna fırlatmasını* bekliyorsak, bunun gerçekleşip gerçekleşmediğini kontrol etmek için `@test_throws` kullanabiliriz:

```jldoctest testfoo
julia> @test_throws MethodError foo(:cat)
Test Passed
      Thrown: MethodError
```

## Working with Test Sets

Genellikle, işlevlerin bir dizi girdi üzerinde doğru çalıştığından emin olmak için çok sayıda test kullanılır. Bir test başarısız olduğunda, varsayılan davranış hemen bir istisna fırlatmaktır. Ancak, testlerin geri kalanını önce çalıştırmak, test edilen kodda ne kadar hata olduğunu daha iyi anlamak için genellikle tercih edilir.

!!! note
    `@testset` testleri çalıştırıldığında kendi yerel kapsamını oluşturacaktır.


`@testset` makrosu, testleri *setler* halinde gruplamak için kullanılabilir. Bir test setindeki tüm testler çalıştırılacak ve test setinin sonunda bir özet yazdırılacaktır. Eğer testlerden herhangi biri başarısız olursa veya bir hata nedeniyle değerlendirilemezse, test seti bir `TestSetException` fırlatacaktır.

```@docs
Test.@testset
Test.TestSetException
```

`foo(x)` fonksiyonu için testlerimizi bir test setine koyabiliriz:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @test foo("a")   == 1
           @test foo("ab")  == 4
           @test foo("abc") == 9
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    3      3  0.0s
```

Test setleri de iç içe olabilir:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @testset "Animals" begin
               @test foo("cat") == 9
               @test foo("dog") == foo("cat")
           end
           @testset "Arrays $i" for i in 1:3
               @test foo(zeros(i)) == i^2
               @test foo(fill(1.0, i)) == i^2
           end
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    8      8  0.0s
```

Fonksiyonları çağırmanın yanı sıra:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> f(x) = @test isone(x)
f (generic function with 1 method)

julia> @testset f(1);
Test Summary: | Pass  Total  Time
f             |    1      1  0.0s
```

Bu, test setlerinin faktörleştirilmesine olanak tanımak için kullanılabilir, böylece ilişkili fonksiyonları çalıştırarak bireysel test setlerini çalıştırmak daha kolay hale gelir. Fonksiyonlar durumunda, test setine çağrılan fonksiyonun adı verilecektir. Eğer iç içe geçmiş bir test setinin hatası yoksa, burada olduğu gibi, `verbose=true` seçeneği geçilmedikçe özet içinde gizlenecektir:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset verbose = true "Foo Tests" begin
           @testset "Animals" begin
               @test foo("cat") == 9
               @test foo("dog") == foo("cat")
           end
           @testset "Arrays $i" for i in 1:3
               @test foo(zeros(i)) == i^2
               @test foo(fill(1.0, i)) == i^2
           end
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    8      8  0.0s
  Animals     |    2      2  0.0s
  Arrays 1    |    2      2  0.0s
  Arrays 2    |    2      2  0.0s
  Arrays 3    |    2      2  0.0s
```

Eğer bir test hatası alırsak, yalnızca başarısız olan test setlerinin detayları gösterilecektir:

```julia-repl; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @testset "Animals" begin
               @testset "Felines" begin
                   @test foo("cat") == 9
               end
               @testset "Canines" begin
                   @test foo("dog") == 9
               end
           end
           @testset "Arrays" begin
               @test foo(zeros(2)) == 4
               @test foo(fill(1.0, 4)) == 15
           end
       end

Arrays: Test Failed
  Expression: foo(fill(1.0, 4)) == 15
   Evaluated: 16 == 15
[...]
Test Summary: | Pass  Fail  Total  Time
Foo Tests     |    3     1      4  0.0s
  Animals     |    2            2  0.0s
  Arrays      |    1     1      2  0.0s
ERROR: Some tests did not pass: 3 passed, 1 failed, 0 errored, 0 broken.
```

## Testing Log Statements

Bir [`@test_logs`](@ref) makrosunu log ifadelerini test etmek için kullanabilir veya [`TestLogger`](@ref) kullanabilirsiniz.

```@docs
Test.@test_logs
Test.TestLogger
Test.LogRecord
```

## Other Test Macros

Hesaplamalar kayan nokta değerleri üzerinde kesin olmayabileceğinden, yaklaşık eşitlik kontrollerini ya `@test a ≈ b` kullanarak (burada `≈`, `\approx`'ın sekme tamamlama ile yazıldığı) ya da doğrudan [`isapprox`](@ref) kullanarak gerçekleştirebilirsiniz.

```jldoctest
julia> @test 1 ≈ 0.999999999
Test Passed

julia> @test 1 ≈ 0.999999
Test Failed at none:1
  Expression: 1 ≈ 0.999999
   Evaluated: 1 ≈ 0.999999

ERROR: There was an error during testing
```

Göreli ve mutlak toleransları, `≈` karşılaştırmasından sonra `isapprox` fonksiyonunun `rtol` ve `atol` anahtar argümanlarını ayarlayarak belirtebilirsiniz:

```jldoctest
julia> @test 1 ≈ 0.999999  rtol=1e-5
Test Passed
```

Not edin ki bu, `≈` sembolünün özel bir özelliği değil, daha çok `@test` makrosunun genel bir özelliğidir: `@test a <op> b key=val` makro tarafından `@test op(a, b, key=val)` şeklinde dönüştürülür. Ancak, bu durum `≈` testleri için özellikle faydalıdır.

```@docs
Test.@inferred
Test.@test_deprecated
Test.@test_warn
Test.@test_nowarn
```

## Broken Tests

Eğer bir test sürekli olarak başarısız oluyorsa, `@test_broken` makrosunu kullanacak şekilde değiştirilebilir. Bu, testin başarısız olmaya devam etmesi durumunda testi `Broken` olarak işaretler ve test başarılı olursa kullanıcıyı bir `Error` ile uyarır.

```@docs
Test.@test_broken
```

`@test_skip`, bir testi değerlendirmeden atlamak için de kullanılabilir, ancak atlanan testi test seti raporlamasında sayar. Test çalışmayacak ancak `Broken` `Result` verecektir.

```@docs
Test.@test_skip
```

## Test result types

```@docs
Test.Result
Test.Pass
Test.Fail
Test.Error
Test.Broken
```

## Creating Custom `AbstractTestSet` Types

Paketler, `record` ve `finish` yöntemlerini uygulayarak kendi `AbstractTestSet` alt türlerini oluşturabilir. Alt tür, bir açıklama dizesi alan bir tek argümanlı yapıcıya sahip olmalı ve herhangi bir seçenek anahtar kelime argümanları olarak geçirilmelidir.

```@docs
Test.record
Test.finish
```

`Test`, iç içe geçmiş test setlerinin yürütülmesi sırasında bunları korumaktan sorumludur, ancak herhangi bir sonuç birikimi `AbstractTestSet` alt türünün sorumluluğundadır. Bu yığına `get_testset` ve `get_testset_depth` yöntemleri ile erişebilirsiniz. Bu işlevlerin dışa aktarılmadığını unutmayın.

```@docs
Test.get_testset
Test.get_testset_depth
```

`Test` ayrıca iç içe `@testset` çağrılarının, açıkça ayarlanmadığı sürece, ebeveynleriyle aynı `AbstractTestSet` alt türünü kullandığından emin olur. Test setinin herhangi bir özelliğini yaymaz. Seçenek miras alma davranışı, `Test`'in sağladığı yığın altyapısını kullanarak paketler tarafından uygulanabilir.

Temel bir `AbstractTestSet` alt türünü tanımlamak şöyle görünebilir:

```julia
import Test: Test, record, finish
using Test: AbstractTestSet, Result, Pass, Fail, Error
using Test: get_testset_depth, get_testset
struct CustomTestSet <: Test.AbstractTestSet
    description::AbstractString
    foo::Int
    results::Vector
    # constructor takes a description string and options keyword arguments
    CustomTestSet(desc; foo=1) = new(desc, foo, [])
end

record(ts::CustomTestSet, child::AbstractTestSet) = push!(ts.results, child)
record(ts::CustomTestSet, res::Result) = push!(ts.results, res)
function finish(ts::CustomTestSet)
    # just record if we're not the top-level parent
    if get_testset_depth() > 0
        record(get_testset(), ts)
        return ts
    end

    # so the results are printed if we are at the top level
    Test.print_test_results(ts)
    return ts
end
```

Ve o test set kullanarak şöyle görünüyor:

```julia
@testset CustomTestSet foo=4 "custom testset inner 2" begin
    # this testset should inherit the type, but not the argument.
    @testset "custom testset inner" begin
        @test true
    end
end
```

Özel bir test seti kullanmak ve kaydedilen sonuçların herhangi bir dış varsayılan test setinin parçası olarak yazdırılmasını sağlamak için, `Test.get_test_counts` tanımlayın. Bu şöyle görünebilir:

```julia
using Test: AbstractTestSet, Pass, Fail, Error, Broken, get_test_counts, TestCounts, format_duration

function Test.get_test_counts(ts::CustomTestSet)
    passes, fails, errors, broken = 0, 0, 0, 0
    # cumulative results
    c_passes, c_fails, c_errors, c_broken = 0, 0, 0, 0

    for t in ts.results
        # count up results
        isa(t, Pass)   && (passes += 1)
        isa(t, Fail)   && (fails  += 1)
        isa(t, Error)  && (errors += 1)
        isa(t, Broken) && (broken += 1)
        # handle children
        if isa(t, AbstractTestSet)
            tc = get_test_counts(t)::TestCounts
            c_passes += tc.passes + tc.cumulative_passes
            c_fails  += tc.fails + tc.cumulative_fails
            c_errors += tc.errors + tc.cumulative_errors
            c_broken += tc.broken + tc.cumulative_broken
        end
    end
    # get a duration, if we have one
    duration = format_duration(ts)
    return TestCounts(true, passes, fails, errors, broken, c_passes, c_fails, c_errors, c_broken, duration)
end
```

```@docs
Test.TestCounts
Test.get_test_counts
Test.format_duration
Test.print_test_results
```

## Test utilities

```@docs
Test.GenericArray
Test.GenericDict
Test.GenericOrder
Test.GenericSet
Test.GenericString
Test.detect_ambiguities
Test.detect_unbound_args
```

## Workflow for Testing Packages

Bize önceki bölümlerde sunulan araçları kullanarak, bir paket oluşturma ve buna test ekleme potansiyel bir iş akışı burada bulunmaktadır.

### Generating an Example Package

Bu iş akışı için `Example` adında bir paket oluşturacağız:

```julia
pkg> generate Example
shell> cd Example
shell> mkdir test
pkg> activate .
```

### Creating Sample Functions

Paketin test edilmesi için bir numaralı gereklilik, test edilecek işlevselliğe sahip olmaktır. Bunun için, test edebileceğimiz bazı basit işlevler ekleyeceğiz. Aşağıdakileri `src/Example.jl` dosyasına ekleyin:

```julia
module Example

function greet()
    "Hello world!"
end

function simple_add(a, b)
    a + b
end

function type_multiply(a::Float64, b::Float64)
    a * b
end

export greet, simple_add, type_multiply

end
```

### Creating a Test Environment

`Example` paketinin kökünden `test` dizinine gidin, orada yeni bir ortam etkinleştirin ve `Test` paketini ortama ekleyin:

```julia
shell> cd test
pkg> activate .
(test) pkg> add Test
```

### Testing Our Package

Artık `Example` için testler eklemeye hazırız. Test setlerini çalıştırmak için `test` dizininde `runtests.jl` adında bir dosya oluşturmak standart bir uygulamadır. O dosyayı `test` dizininde oluşturun ve aşağıdaki kodu ekleyin:

```julia
using Example
using Test

@testset "Example tests" begin

    @testset "Math tests" begin
        include("math_tests.jl")
    end

    @testset "Greeting tests" begin
        include("greeting_tests.jl")
    end
end
```

Bu iki dahil edilen dosyayı, `math_tests.jl` ve `greeting_tests.jl` oluşturmalıyız ve onlara bazı testler eklemeliyiz.

> **Not:** `test` ortamının `Project.toml` dosyasına `Example` eklememiz gerekmediğine dikkat edin. Bu, Julia'nın test sisteminin bir avantajıdır; [read about more here](https://pkgdocs.julialang.org/dev/creating-packages/) şeklinde kullanabilirsiniz.


#### Writing Tests for `math_tests.jl`

`Test.jl` kullanarak, `math_tests.jl` dosyasına ekleyebileceğimiz bazı örnek testler:

```julia
@testset "Testset 1" begin
    @test 2 == simple_add(1, 1)
    @test 3.5 == simple_add(1, 2.5)
        @test_throws MethodError simple_add(1, "A")
        @test_throws MethodError simple_add(1, 2, 3)
end

@testset "Testset 2" begin
    @test 1.0 == type_multiply(1.0, 1.0)
        @test isa(type_multiply(2.0, 2.0), Float64)
    @test_throws MethodError type_multiply(1, 2.5)
end
```

#### Writing Tests for `greeting_tests.jl`

`Test.jl` kullanarak, `greeting_tests.jl` dosyasına ekleyebileceğimiz bazı örnek testler:

```julia
@testset "Testset 3" begin
    @test "Hello world!" == greet()
    @test_throws MethodError greet("Antonia")
end
```

### Testing Our Package

Artık testlerimizi ve `test` içindeki `runtests.jl` scriptimizi eklediğimize göre, `Example` paketimizi test etmek için `Example` paket ortamının köküne geri dönebilir ve `Example` ortamını yeniden etkinleştirebiliriz:

```julia
shell> cd ..
pkg> activate .
```

Oradan, test paketimizi aşağıdaki gibi çalıştırabiliriz:

```julia
(Example) pkg> test
     Testing Example
      Status `/tmp/jl_Yngpvy/Project.toml`
  [fa318bd2] Example v0.1.0 `/home/src/Projects/tmp/errata/Example`
  [8dfed614] Test `@stdlib/Test`
      Status `/tmp/jl_Yngpvy/Manifest.toml`
  [fa318bd2] Example v0.1.0 `/home/src/Projects/tmp/errata/Example`
  [2a0f44e3] Base64 `@stdlib/Base64`
  [b77e0a4c] InteractiveUtils `@stdlib/InteractiveUtils`
  [56ddb016] Logging `@stdlib/Logging`
  [d6f4376e] Markdown `@stdlib/Markdown`
  [9a3f8284] Random `@stdlib/Random`
  [ea8e919c] SHA `@stdlib/SHA`
  [9e88b42a] Serialization `@stdlib/Serialization`
  [8dfed614] Test `@stdlib/Test`
     Testing Running tests...
Test Summary: | Pass  Total
Example tests |    9      9
     Testing Example tests passed
```

Ve ve her şey doğru giderse, yukarıda benzer bir çıktı görmelisiniz. `Test.jl` kullanarak, paketler için daha karmaşık testler eklenebilir, ancak bu, geliştiricileri kendi oluşturdukları paketleri test etmeye başlama konusunda yönlendirmelidir.

```@meta
DocTestSetup = nothing
```

### Code Coverage

Testler sırasında kod kapsamı takibi, `pkg> test --coverage` bayrağını kullanarak (veya daha düşük bir seviyede [`--code-coverage`](@ref command-line-interface) julia argümanını kullanarak) etkinleştirilebilir. Bu, [julia-runtest](https://github.com/julia-actions/julia-runtest) GitHub eyleminde varsayılan olarak açıktır.

Kapsama değerlendirmek için ya yerel olarak kaynak dosyaların yanında oluşturulan `.cov` dosyalarını manuel olarak inceleyin ya da CI'de [julia-processcoverage](https://github.com/julia-actions/julia-processcoverage) GitHub eylemini kullanın.

!!! compat "Julia 1.11"
    Julia 1.11'den itibaren, kapsama paket ön derleme aşamasında toplanmamaktadır.

