```
Görev(func)
```

Verilen `func` fonksiyonunu (argüman almayan bir çağrılabilir olmalıdır) yürütmek için bir `Görev` (yani coroutine) oluşturun. Görev, bu fonksiyon döndüğünde sona erer. Görev, [`schedule`](@ref) ile yapılandırıldığında, inşaat sırasında ebeveynin "dünya yaşı" içinde çalışacaktır.

!!! uyarı     Varsayılan olarak görevlerin yapışkan bitinin `t.sticky` olarak ayarlandığına dikkat edin. Bu, [`@async`](@ref) için tarihsel varsayılanı modellemektedir. Yapışkan görevler yalnızca ilk olarak planlandıkları işçi iş parçacığında çalıştırılabilir ve planlandıklarında, planlandıkları görev yapışkan hale gelecektir. [`Threads.@spawn`](@ref) davranışını elde etmek için yapışkan bitini manuel olarak `false` olarak ayarlayın.

# Örnekler

```jldoctest
julia> a() = sum(i for i in 1:1000);

julia> b = Task(a);
```

Bu örnekte, `b` henüz başlamamış bir çalıştırılabilir `Görev`dir.
