# [Workflow Tips](@id man-workflow-tips)

İşte Julia ile verimli çalışmak için bazı ipuçları.

## REPL-based workflow

Daha önce [The Julia REPL](@ref) içinde açıklandığı gibi, Julia'nın REPL'i, verimli bir etkileşimli iş akışını kolaylaştıran zengin işlevsellik sunar. İşte komut satırındaki deneyiminizi daha da geliştirebilecek bazı ipuçları.

### A basic editor/REPL workflow

En temel Julia iş akışları, bir metin düzenleyicisini `julia` komut satırı ile birlikte kullanmayı içerir.

Bir dosya oluşturun, örneğin `Tmp.jl`, ve içine şunları ekleyin:

```julia
module Tmp

say_hello() = println("Hello!")

# Your other definitions here

end # module

using .Tmp
```

Sonra, aynı dizinde, Julia REPL'ini başlatın ( `julia` komutunu kullanarak). Yeni dosyayı aşağıdaki gibi çalıştırın:

```
julia> include("Tmp.jl")

julia> Tmp.say_hello()
Hello!
```

REPL'de fikirleri keşfedin. İyi fikirleri `Tmp.jl` dosyasına kaydedin. Dosya değiştirildikten sonra yeniden yüklemek için sadece tekrar `include` edin.

Yukarıdaki anahtar, kodunuzun bir modülde kapsüllenmiş olmasıdır. Bu, `struct` tanımlarını düzenlemenize ve yöntemleri kaldırmanıza olanak tanır, Julia'yı yeniden başlatmadan.

(Açıklama: `struct`lar tanımlandıktan sonra düzenlenemez, yöntemler de silinemez. Ancak bir modülün tanımını yeniden yazabilirsiniz ki bu da `include("Tmp.jl")` yaptığımızda gerçekleşir.)

Ayrıca, bir modülde kodun kapsüllenmesi, REPL'deki önceki durumdan etkilenmesini engelleyerek, sizi zor tespit edilen hatalardan korur.

## Browser-based workflow

Tarayıcıda Julia ile etkileşimde bulunmanın birkaç yolu vardır:

  * Using Pluto notebooks through [Pluto.jl](https://github.com/fonsp/Pluto.jl)
  * Jupyter not defterlerini [IJulia.jl](https://github.com/JuliaLang/IJulia.jl) üzerinden kullanma

## Revise-based workflows

REPL veya IJulia'da olsanız da, genellikle geliştirme deneyiminizi [Revise](https://github.com/timholy/Revise.jl) ile geliştirebilirsiniz. Julia başlatıldığında Revise'in başlaması için genellikle yapılandırma yapmak yaygındır; bu, [Revise documentation](https://timholy.github.io/Revise.jl/stable/) içindeki talimatlara göre yapılır. Yapılandırıldıktan sonra, Revise, yüklenen modüllerdeki dosyalardaki değişiklikleri ve REPL'e `includet` ile yüklenen dosyaları (ancak düz `include` ile değil) takip eder; ardından dosyaları düzenleyebilir ve değişiklikler julia oturumunuzu yeniden başlatmadan etkili olur. Standart bir iş akışı, yukarıdaki REPL tabanlı iş akışına benzer, aşağıdaki değişikliklerle:

1. Kodunuzu yükleme yolunuzda bir modüle yerleştirin. Bunu başarmanın birkaç yolu vardır, bunlardan iki önerilen seçenek şunlardır:

      * Uzun vadeli projeler için [PkgTemplates](https://github.com/invenia/PkgTemplates.jl) kullanın:

        ```julia
        using PkgTemplates
        t = Template()
        t("MyPkg")
        ```

        Bu, `.julia/dev` dizininizde boş bir paket, `"MyPkg"` oluşturacaktır. PkgTemplates'in `Template` yapıcısı aracılığıyla birçok farklı seçeneği kontrol etmenize olanak tanıdığını unutmayın.

        Adım 2'de, `MyPkg/src/MyPkg.jl` dosyasını kaynak kodunu değiştirmek için ve `MyPkg/test/runtests.jl` dosyasını testler için düzenleyin.
      * "Atık" projeler için, işinizi geçici dizininizde (örneğin, `/tmp`) yaparak temizlik ihtiyacını ortadan kaldırabilirsiniz.

        Geçici dizininize gidin ve Julia'yı başlatın, ardından aşağıdakileri yapın:

        ```julia-repl
        pkg> generate MyPkg            # type ] to enter pkg mode
        julia> push!(LOAD_PATH, pwd())   # hit backspace to exit pkg mode
        ```

        Eğer Julia oturumunuzu yeniden başlatırsanız, `LOAD_PATH`'i değiştiren o komutu yeniden vermeniz gerekecek.

        Adım 2'de, `MyPkg/src/MyPkg.jl` dosyasını düzenleyerek kaynak kodunu değiştirin ve istediğiniz herhangi bir test dosyası oluşturun.
2. Paketinizi geliştirin

    *Önce* herhangi bir kod yüklemeden önce, Revise'in çalıştığından emin olun: `using Revise` yazın veya otomatik olarak çalışacak şekilde yapılandırma ile ilgili belgelerini takip edin.

    Sonra test dosyanızın bulunduğu dizine gidin (burada `"runtests.jl"` olduğu varsayılmaktadır) ve aşağıdakileri yapın:

    ```julia-repl
    julia> using MyPkg

    julia> include("runtests.jl")
    ```

    Kodunuzu MyPkg içinde düzenli olarak değiştirebilir ve testleri `include("runtests.jl")` ile yeniden çalıştırabilirsiniz. Değişikliklerin etkisini görmek için genellikle Julia oturumunuzu yeniden başlatmanıza gerek yoktur (birkaç [limitations](https://timholy.github.io/Revise.jl/stable/limitations/) hariç).
