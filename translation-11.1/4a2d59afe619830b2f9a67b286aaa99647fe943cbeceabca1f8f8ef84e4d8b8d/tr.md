```
mapfoldr(f, op, itr; [init])
```

[`foldr`](@ref) gibi, ancak sağdan birleştirme garantisi ile, [`mapreduce`](@ref) gibi. Eğer sağlanırsa, anahtar kelime argümanı `init` tam olarak bir kez kullanılacaktır. Genel olarak, boş koleksiyonlarla çalışmak için `init` sağlamanız gerekecektir.
