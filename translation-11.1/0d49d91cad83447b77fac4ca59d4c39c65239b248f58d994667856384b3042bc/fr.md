```
displayable(mime) -> Bool
displayable(d::AbstractDisplay, mime) -> Bool
```

Renvoie une valeur booléenne indiquant si le type `mime` donné (chaîne) est affichable par l'un des affichages dans la pile d'affichage actuelle, ou spécifiquement par l'affichage `d` dans la deuxième variante.
