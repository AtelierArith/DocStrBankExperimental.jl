```
enumerate(iter)
```

Ein Iterator, der `(i, x)` zurückgibt, wobei `i` ein Zähler ist, der bei 1 beginnt, und `x` der `i`te Wert aus dem gegebenen Iterator ist. Es ist nützlich, wenn Sie nicht nur die Werte `x`, über die Sie iterieren, sondern auch die Anzahl der bisherigen Iterationen benötigen.

Beachten Sie, dass `i` möglicherweise nicht gültig für die Indizierung von `iter` ist oder ein anderes Element indiziert. Dies geschieht, wenn `iter` Indizes hat, die nicht bei 1 beginnen, und kann bei Strings, Dictionaries usw. auftreten. Siehe die Methode `pairs(IndexLinear(), iter)`, wenn Sie sicherstellen möchten, dass `i` ein Index ist.

# Beispiele

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
