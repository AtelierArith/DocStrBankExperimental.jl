# Talking to the compiler (the `:meta` mechanism)

In einigen Fällen möchte man möglicherweise Hinweise oder Anweisungen geben, dass ein bestimmter Codeblock besondere Eigenschaften hat: Man möchte ihn möglicherweise immer inline einfügen oder spezielle Compiler-Optimierungspässe aktivieren. Seit Version 0.4 hat Julia eine Konvention, dass diese Anweisungen innerhalb eines `:meta`-Ausdrucks platziert werden können, der typischerweise (aber nicht unbedingt) der erste Ausdruck im Körper einer Funktion ist.

`:meta`-Ausdrücke werden mit Makros erstellt. Als Beispiel betrachten wir die Implementierung des `@inline`-Makros:

```julia
macro inline(ex)
    esc(isa(ex, Expr) ? pushmeta!(ex, :inline) : ex)
end
```

Hier wird erwartet, dass `ex` ein Ausdruck ist, der eine Funktion definiert. Eine Aussage wie diese:

```julia
@inline function myfunction(x)
    x*(x+3)
end
```

wird in einen Ausdruck wie diesen umgewandelt:

```julia
quote
    function myfunction(x)
        Expr(:meta, :inline)
        x*(x+3)
    end
end
```

`Base.pushmeta!(ex, tag::Union{Symbol,Expr})` fügt `:tag` am Ende des `:meta`-Ausdrucks hinzu und erstellt einen neuen `:meta`-Ausdruck, falls erforderlich.

Um die Metadaten zu verwenden, müssen Sie diese `:meta`-Ausdrücke parsen. Wenn Ihre Implementierung in Julia durchgeführt werden kann, ist `Base.popmeta!` sehr nützlich: `Base.popmeta!(body, :symbol)` durchsucht einen Funktions *body*-Ausdruck (einen ohne die Funktionssignatur) nach dem ersten `:meta`-Ausdruck, der `:symbol` enthält, extrahiert alle Argumente und gibt ein Tupel `(found::Bool, args::Array{Any})` zurück. Wenn die Metadaten keine Argumente hatten oder `:symbol` nicht gefunden wurde, ist das `args`-Array leer.

Noch nicht bereitgestellt ist eine praktische Infrastruktur zum Parsen von `:meta`-Ausdrücken aus C++.
