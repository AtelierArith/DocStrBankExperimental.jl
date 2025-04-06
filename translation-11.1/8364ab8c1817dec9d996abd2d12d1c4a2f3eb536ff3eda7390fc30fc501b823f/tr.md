```
fdio([name::AbstractString, ]fd::Integer[, own::Bool=false]) -> IOStream
```

Bir tamsayı dosya tanımlayıcısından bir [`IOStream`](@ref) nesnesi oluşturur. Eğer `own` `true` ise, bu nesneyi kapatmak, alttaki tanımlayıcıyı kapatacaktır. Varsayılan olarak, bir `IOStream` çöp toplayıcı tarafından toplandığında kapatılır. `name`, tanımlayıcıyı adlandırılmış bir dosyayla ilişkilendirmenizi sağlar.
