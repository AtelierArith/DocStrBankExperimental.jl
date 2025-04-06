```
undocumented_names(mod::Module; private=false)
```

Belgesiz sembollerin sıralı bir vektörünü döndürür `module` (yani, dokümantasyon dizeleri eksik olan). `private=false` (varsayılan) yalnızca `public` ve/veya `export` ile tanımlanan tanımlayıcıları döndürürken, `private=true` modüldeki tüm sembolleri döndürür (başında `#` olan derleyici tarafından üretilen gizli semboller hariç).

Ayrıca bakınız: [`names`](@ref), [`Docs.hasdoc`](@ref), [`Base.ispublic`](@ref).
