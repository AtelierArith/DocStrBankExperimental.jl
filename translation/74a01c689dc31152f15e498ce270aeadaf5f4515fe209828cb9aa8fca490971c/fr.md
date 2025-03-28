```
dt::Date + t::Time -> DateTime
```

L'addition d'une `Date` avec un `Time` produit un `DateTime`. Les parties heure, minute, seconde et milliseconde du `Time` sont utilisées avec l'année, le mois et le jour de la `Date` pour créer le nouveau `DateTime`. Des microsecondes ou des nanosecondes non nulles dans le type `Time` entraîneront le lancement d'une `InexactError`.
