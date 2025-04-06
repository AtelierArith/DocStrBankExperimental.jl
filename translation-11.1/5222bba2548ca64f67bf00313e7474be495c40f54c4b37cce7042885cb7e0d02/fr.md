`HTML(s)`: Créez un objet qui rend `s` en html.

```
HTML("<div>foo</div>")
```

Vous pouvez également utiliser un flux pour de grandes quantités de données :

```
HTML() do io
  println(io, "<div>foo</div>")
end
```

!!! avertissement
    `HTML` est actuellement exporté pour maintenir la compatibilité ascendante, mais cet export est obsolète. Il est recommandé d'utiliser ce type comme [`Docs.HTML`](@ref) ou de l'importer explicitement depuis `Docs`.

