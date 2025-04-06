```
undocumented_names(mod::Module; private=false)
```

Devuelve un vector ordenado de símbolos no documentados en `module` (es decir, que carecen de cadenas de documentación). `private=false` (el valor predeterminado) devuelve solo identificadores declarados con `public` y/o `export`, mientras que `private=true` devuelve todos los símbolos en el módulo (excluyendo los símbolos ocultos generados por el compilador que comienzan con `#`).

Véase también: [`names`](@ref), [`Docs.hasdoc`](@ref), [`Base.ispublic`](@ref).
