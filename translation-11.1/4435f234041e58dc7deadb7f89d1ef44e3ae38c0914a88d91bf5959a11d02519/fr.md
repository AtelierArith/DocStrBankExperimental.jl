```
base64encode(writefunc, args...; context=nothing)
base64encode(args...; context=nothing)
```

Étant donné une fonction de type [`write`](@ref) comme `writefunc`, qui prend un flux I/O comme premier argument, `base64encode(writefunc, args...)` appelle `writefunc` pour écrire `args...` dans une chaîne encodée en base64, et retourne la chaîne. `base64encode(args...)` est équivalent à `base64encode(write, args...)` : il convertit ses arguments en octets en utilisant les fonctions standard [`write`](@ref) et retourne la chaîne encodée en base64.

L'argument clé optionnel `context` peut être défini comme une paire `:key=>value` ou un objet `IO` ou [`IOContext`](@ref) dont les attributs sont utilisés pour le flux I/O passé à `writefunc` ou `write`.

Voir aussi [`base64decode`](@ref).
