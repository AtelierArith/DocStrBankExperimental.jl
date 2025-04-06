```
Parser()
```

TOML `Parser` için yapıcı. Çoğu durumda, bir `Parser`'ı açıkça oluşturmak gerekmez, bunun yerine doğrudan [`TOML.parsefile`](@ref) veya [`TOML.parse`](@ref) kullanılır. Ancak, açık bir ayrıştırıcı kullanmak, daha büyük sayıda küçük dosya ayrıştırıldığında performans açısından faydalı olabilecek bazı dahili veri yapılarını yeniden kullanacaktır.
