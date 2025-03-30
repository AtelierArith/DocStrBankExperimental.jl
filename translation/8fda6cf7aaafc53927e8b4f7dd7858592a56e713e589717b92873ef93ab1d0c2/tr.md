```
@time expr
@time "açıklama" expr
```

Bir ifadeyi yürütmek için bir makro, yürütme süresini, yapılan tahsis sayısını ve yürütmenin neden olduğu toplam tahsis edilen bayt sayısını yazdırır, ardından ifadenin değerini döndürür. Çöp toplama (gc), yeni kod derleme veya geçersiz kılınmış kodu yeniden derleme için harcanan süre bir yüzde olarak gösterilir. Beklemek zorunda kalan bir [`ReentrantLock`](@ref) varsa, bu bir sayı olarak gösterilir.

Zaman raporundan önce yazdırmak için isteğe bağlı bir açıklama dizesi sağlayın.

Bazı durumlarda sistem, `@time` ifadesinin içine bakacak ve üst düzey ifadenin yürütülmesinden önce çağrılan kodun bir kısmını derleyecektir. Bu olduğunda, bazı derleme süreleri sayılmaz. Bu süreyi dahil etmek için `@time @eval ...` komutunu çalıştırabilirsiniz.

Ayrıca [`@showtime`](@ref), [`@timev`](@ref), [`@timed`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref) ve [`@allocations`](@ref) ile de bakabilirsiniz.

!!! not
    Daha ciddi performans testleri için, gürültüyü azaltmak amacıyla fonksiyonu birden fazla kez değerlendiren `@btime` makrosunu BenchmarkTools.jl paketinden düşünün.


!!! uyumluluk "Julia 1.8"
    Açıklama ekleme seçeneği Julia 1.8'de tanıtıldı.

    Derleme süresinin derleme süresinden ayrı olarak gösterilmesi Julia 1.8'de tanıtıldı.


!!! uyumluluk "Julia 1.11"
    Herhangi bir kilit çatışmasının raporlanması Julia 1.11'de eklendi.


```julia-repl
julia> x = rand(10,10);

julia> @time x * x;
  0.606588 saniye (2.19 M tahsis: 116.555 MiB, %3.75 gc süresi, %99.94 derleme süresi)

julia> @time x * x;
  0.000009 saniye (1 tahsis: 896 bayt)

julia> @time begin
           sleep(0.3)
           1+1
       end
  0.301395 saniye (8 tahsis: 336 bayt)
2

julia> @time "Bir saniyelik uyku" sleep(1)
Bir saniyelik uyku: 1.005750 saniye (5 tahsis: 144 bayt)

julia> for loop in 1:3
            @time loop sleep(1)
        end
1: 1.006760 saniye (5 tahsis: 144 bayt)
2: 1.001263 saniye (5 tahsis: 144 bayt)
3: 1.003676 saniye (5 tahsis: 144 bayt)
```
