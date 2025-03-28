# Talking to the compiler (the `:meta` mechanism)

En algunas circunstancias, uno podría desear proporcionar pistas o instrucciones de que un bloque de código dado tiene propiedades especiales: podrías querer siempre incluirlo en línea, o podrías querer activar pases de optimización especiales del compilador. A partir de la versión 0.4, Julia tiene una convención de que estas instrucciones pueden colocarse dentro de una expresión `:meta`, que es típicamente (pero no necesariamente) la primera expresión en el cuerpo de una función.

Las expresiones `:meta` se crean con macros. Como ejemplo, considera la implementación de la macro `@inline`:

```julia
macro inline(ex)
    esc(isa(ex, Expr) ? pushmeta!(ex, :inline) : ex)
end
```

Aquí, `ex` se espera que sea una expresión que define una función. Una declaración como esta:

```julia
@inline function myfunction(x)
    x*(x+3)
end
```

se convierte en una expresión como esta:

```julia
quote
    function myfunction(x)
        Expr(:meta, :inline)
        x*(x+3)
    end
end
```

`Base.pushmeta!(ex, tag::Union{Symbol,Expr})` agrega `:tag` al final de la expresión `:meta`, creando una nueva expresión `:meta` si es necesario.

Para usar los metadatos, debes analizar estas expresiones `:meta`. Si tu implementación se puede realizar dentro de Julia, `Base.popmeta!` es muy útil: `Base.popmeta!(body, :symbol)` escaneará una expresión de *cuerpo* de función (una sin la firma de la función) en busca de la primera expresión `:meta` que contenga `:symbol`, extraerá cualquier argumento y devolverá una tupla `(found::Bool, args::Array{Any})`. Si los metadatos no tenían argumentos, o `:symbol` no se encontró, el array `args` estará vacío.

Aún no se ha proporcionado una infraestructura conveniente para analizar expresiones `:meta` de C++.
