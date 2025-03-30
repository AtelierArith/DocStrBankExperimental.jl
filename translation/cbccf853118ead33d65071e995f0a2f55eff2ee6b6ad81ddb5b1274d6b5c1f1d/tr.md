```
pipeline(from, to, ...)
```

Bir veri kaynağından bir hedefe bir boru hattı oluşturur. Kaynak ve hedef, komutlar, G/Ç akışları, dizeler veya diğer `pipeline` çağrılarının sonuçları olabilir. En az bir argüman bir komut olmalıdır. Dizeler dosya adlarını ifade eder. İki veya daha fazla argümanla çağrıldığında, soldan sağa doğru zincirlenir. Örneğin, `pipeline(a,b,c)` ifadesi `pipeline(pipeline(a,b),c)` ile eşdeğerdir. Bu, çok aşamalı boru hatlarını belirtmek için daha özlü bir yol sağlar.

**Örnekler**:

```julia
run(pipeline(`ls`, `grep xyz`))
run(pipeline(`ls`, "out.txt"))
run(pipeline("out.txt", `grep xyz`))
```
