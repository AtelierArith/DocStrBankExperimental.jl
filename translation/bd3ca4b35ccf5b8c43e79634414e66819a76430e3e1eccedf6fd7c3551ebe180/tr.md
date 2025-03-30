```
@MIME_str
```

[`MIME`](@ref) türlerini yazmak için bir kolaylık makrosudur, genellikle [`show`](@ref) yöntemlerine eklenirken kullanılır. Örneğin, `show(io::IO, ::MIME"text/html", x::MyType) = ...` sözdizimi, `MyType`'ın HTML temsilini nasıl yazacağınızı tanımlamak için kullanılabilir.
