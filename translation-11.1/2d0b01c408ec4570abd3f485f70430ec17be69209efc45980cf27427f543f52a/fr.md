```
ffmerge!(repo::GitRepo, ann::GitAnnotated)
```

Fusion fastforward des modifications dans le HEAD actuel. Cela n'est possible que si le commit référencé par `ann` est un descendant du HEAD actuel (par exemple, si l'on tire des modifications d'une branche distante qui est simplement en avance par rapport à la pointe de la branche locale).
