`Text(s)`: Créez un objet qui rend `s` en tant que texte brut.

```
Text("foo")
```

Vous pouvez également utiliser un flux pour de grandes quantités de données :

```
Text() do io
  println(io, "foo")
end
```

!!! avertissement
    `Text` est actuellement exporté pour maintenir la compatibilité avec les versions antérieures, mais cet export est obsolète. Il est recommandé d'utiliser ce type comme [`Docs.Text`](@ref) ou de l'importer explicitement depuis `Docs`.

