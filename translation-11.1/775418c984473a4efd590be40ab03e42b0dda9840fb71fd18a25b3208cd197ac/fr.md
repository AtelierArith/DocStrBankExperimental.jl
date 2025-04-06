```
graphemes(s::AbstractString) -> GraphemeIterator
```

Renvoie un itérateur sur les sous-chaînes de `s` qui correspondent aux graphèmes étendus dans la chaîne, tels que définis par Unicode UAX #29. (En gros, ce sont ce que les utilisateurs percevraient comme des caractères uniques, même s'ils peuvent contenir plus d'un point de code ; par exemple, une lettre combinée avec un accent est un seul graphème.)
