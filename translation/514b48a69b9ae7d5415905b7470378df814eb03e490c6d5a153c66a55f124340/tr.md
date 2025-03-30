```
cconvert(T,x)
```

`x`'i `T` türünde C koduna geçilecek bir değere dönüştür. Genellikle `convert(T, x)` çağrısı yaparak gerçekleştirilir.

`x`'in `T`'ye güvenli bir şekilde dönüştürülemeyeceği durumlarda, [`convert`](@ref) ile karşılaştırıldığında, `cconvert` `T`'den farklı bir türde bir nesne döndürebilir; ancak bu nesne [`unsafe_convert`](@ref) tarafından işlenmek için uygundur. Bu fonksiyonun sonucu, [`unsafe_convert`](@ref) sonucuna ihtiyaç duyulmadığı sürece geçerli (GC için) tutulmalıdır. Bu, `ccall` tarafından erişilecek belleği tahsis etmek için kullanılabilir. Birden fazla nesne tahsis edilmesi gerekiyorsa, nesnelerin bir demeti döndürme değeri olarak kullanılabilir.

Ne `convert` ne de `cconvert`, bir Julia nesnesini `Ptr`'ye dönüştürmelidir.
