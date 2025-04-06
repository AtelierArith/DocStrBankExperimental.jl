```
stage(ie::IndexEntry) -> Cint
```

Obtenez le numéro de stage de `ie`. Le numéro de stage `0` représente l'état actuel de l'arbre de travail, mais d'autres numéros peuvent être utilisés en cas de conflit de fusion. Dans ce cas, les différents numéros de stage sur un `IndexEntry` décrivent à quel(x) côté(s) du conflit l'état actuel du fichier appartient. Le stage `0` est l'état avant la tentative de fusion, le stage `1` est les modifications qui ont été apportées localement, les stages `2` et supérieurs sont pour les modifications provenant d'autres branches (par exemple, dans le cas d'une fusion "octopus" multi-branches, les stages `2`, `3` et `4` pourraient être utilisés).
