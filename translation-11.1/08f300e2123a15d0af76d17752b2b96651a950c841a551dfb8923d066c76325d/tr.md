```
codeunit(s::AbstractString) -> Type{<:Union{UInt8, UInt16, UInt32}}
```

Verilen dize nesnesinin kod birimi türünü döndürür. ASCII, Latin-1 veya UTF-8 kodlamalı dizeler için bu `UInt8` olur; UCS-2 ve UTF-16 için `UInt16`; UTF-32 için `UInt32` olur. Kod birimi türü bu üç türle sınırlı olmak zorunda değildir, ancak bu birimlerden birini kullanmayan yaygın olarak kullanılan dize kodlamalarını düşünmek zordur. `codeunit(s)` ifadesi, `s` boş olmayan bir dize olduğunda `typeof(codeunit(s,1))` ile aynıdır.

Ayrıca [`ncodeunits`](@ref) bakınız.
