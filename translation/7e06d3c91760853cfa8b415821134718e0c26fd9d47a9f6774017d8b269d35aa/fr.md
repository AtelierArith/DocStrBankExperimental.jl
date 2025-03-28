```
merge(a::NamedTuple, bs::NamedTuple...)
```

Construit un nouveau tuple nommé en fusionnant deux ou plusieurs existants, de manière associative à gauche. La fusion se fait de gauche à droite, entre des paires de tuples nommés, et ainsi l'ordre des champs présents dans les tuples nommés les plus à gauche et les plus à droite prend la même position que celle trouvée dans le tuple nommé le plus à gauche. Cependant, les valeurs sont prises à partir des champs correspondants dans le tuple nommé le plus à droite qui contient ce champ. Les champs présents uniquement dans le tuple nommé le plus à droite d'une paire sont ajoutés à la fin. Un fallback est implémenté pour le cas où un seul tuple nommé est fourni, avec la signature `merge(a::NamedTuple)`.

!!! compat "Julia 1.1"
    La fusion de 3 tuples nommés ou plus nécessite au moins Julia 1.1.


# Exemples

```jldoctest
julia> merge((a=1, b=2, c=3), (b=4, d=5))
(a = 1, b = 4, c = 3, d = 5)
```

```jldoctest
julia> merge((a=1, b=2), (b=3, c=(d=1,)), (c=(d=2,),))
(a = 1, b = 3, c = (d = 2,))
```
