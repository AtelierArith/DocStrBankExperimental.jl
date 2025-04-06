```
@ncallkw N f kw sym...
```

Generiere einen Funktionsaufruf-Ausdruck mit Schlüsselwortargumenten `kw...`. Wie im Fall von [`@ncall`](@ref) steht `sym` für eine beliebige Anzahl von Funktionsargumenten, von denen das letzte ein Ausdruck für eine anonyme Funktion sein kann und in `N` Argumente erweitert wird.

# Beispiele

```jldoctest
julia> using Base.Cartesian

julia> f(x...; a, b = 1, c = 2, d = 3) = +(x..., a, b, c, d);

julia> x_1, x_2 = (-1, -2); b = 0; kw = (c = 0, d = 0);

julia> @ncallkw 2 f (; a = 0, b, kw...) x
-3

```
