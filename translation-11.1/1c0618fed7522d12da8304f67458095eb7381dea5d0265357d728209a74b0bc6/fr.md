```
pick(m::AbstractMenu, cursor::Int)
```

Définit ce qui se passe lorsqu'un utilisateur appuie sur la touche Entrée alors que le menu est ouvert. Si `true` est retourné, `request()` sortira. `cursor` indexe la position de la sélection.
