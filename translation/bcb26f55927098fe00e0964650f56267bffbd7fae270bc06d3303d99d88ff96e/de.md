```
undocumented_names(mod::Module; private=false)
```

Gibt einen sortierten Vektor von undokumentierten Symbolen im `module` zurück (d.h. ohne Dokumentationsstrings). `private=false` (der Standard) gibt nur Bezeichner zurück, die mit `public` und/oder `export` deklariert sind, während `private=true` alle Symbole im Modul zurückgibt (außer compiler-generierten versteckten Symbolen, die mit `#` beginnen).

Siehe auch: [`names`](@ref), [`Docs.hasdoc`](@ref), [`Base.ispublic`](@ref).
