```
enumerate(iter)
```

Un itérateur qui produit `(i, x)` où `i` est un compteur commençant à 1, et `x` est la `i`-ème valeur de l'itérateur donné. C'est utile lorsque vous avez besoin non seulement des valeurs `x` sur lesquelles vous itérez, mais aussi du nombre d'itérations jusqu'à présent.

Notez que `i` peut ne pas être valide pour indexer `iter`, ou peut indexer un élément différent. Cela se produira si `iter` a des indices qui ne commencent pas à 1, et peut se produire pour des chaînes de caractères, des dictionnaires, etc. Consultez la méthode `pairs(IndexLinear(), iter)` si vous souhaitez vous assurer que `i` est un index.

# Exemples

```jldoctest
julia> a = ["a", "b", "c"];

julia> for (index, value) in enumerate(a)
           println("$index $value")
       end
1 a
2 b
3 c

julia> str = "naïve";

julia> for (i, val) in enumerate(str)
           print("i = ", i, ", val = ", val, ", ")
           try @show(str[i]) catch e println(e) end
       end
i = 1, val = n, str[i] = 'n'
i = 2, val = a, str[i] = 'a'
i = 3, val = ï, str[i] = 'ï'
i = 4, val = v, StringIndexError("naïve", 4)
i = 5, val = e, str[i] = 'v'
```
