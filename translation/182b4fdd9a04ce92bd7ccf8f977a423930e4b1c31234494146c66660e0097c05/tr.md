```
mapfoldl(f, op, itr; [init])
```

[`mapreduce`](@ref) ile benzer, ancak [`foldl`](@ref) gibi sol birleştirmenin garantisi vardır. Eğer sağlanmışsa, anahtar kelime argümanı `init` tam olarak bir kez kullanılacaktır. Genel olarak, boş koleksiyonlarla çalışmak için `init` sağlamanız gerekecektir.
