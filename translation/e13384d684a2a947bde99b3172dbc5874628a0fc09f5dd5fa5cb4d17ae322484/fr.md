# Talking to the compiler (the `:meta` mechanism)

Dans certaines circonstances, on peut souhaiter fournir des indices ou des instructions indiquant qu'un bloc de code donné a des propriétés spéciales : vous pourriez toujours vouloir l'inliner, ou vous pourriez vouloir activer des passes d'optimisation spéciales du compilateur. À partir de la version 0.4, Julia a une convention selon laquelle ces instructions peuvent être placées à l'intérieur d'une expression `:meta`, qui est généralement (mais pas nécessairement) la première expression dans le corps d'une fonction.

`:meta` expressions sont créées avec des macros. Par exemple, considérons l'implémentation de la macro `@inline` :

```julia
macro inline(ex)
    esc(isa(ex, Expr) ? pushmeta!(ex, :inline) : ex)
end
```

Ici, `ex` est censé être une expression définissant une fonction. Une déclaration comme celle-ci :

```julia
@inline function myfunction(x)
    x*(x+3)
end
```

se transforme en une expression comme celle-ci :

```julia
quote
    function myfunction(x)
        Expr(:meta, :inline)
        x*(x+3)
    end
end
```

`Base.pushmeta!(ex, tag::Union{Symbol,Expr})` ajoute `:tag` à la fin de l'expression `:meta`, créant une nouvelle expression `:meta` si nécessaire.

Pour utiliser les métadonnées, vous devez analyser ces expressions `:meta`. Si votre implémentation peut être effectuée dans Julia, `Base.popmeta!` est très pratique : `Base.popmeta!(body, :symbol)` va scanner une expression de *corps* de fonction (une sans la signature de la fonction) à la recherche de la première expression `:meta` contenant `:symbol`, extraire les arguments et retourner un tuple `(found::Bool, args::Array{Any})`. Si les métadonnées n'avaient pas d'arguments, ou si `:symbol` n'a pas été trouvé, le tableau `args` sera vide.

Pas encore fourni est une infrastructure pratique pour analyser les expressions `:meta` de C++.
