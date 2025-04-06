```
format(dt::TimeType, format::AbstractString; locale="french") -> AbstractString
```

Construisez une chaîne en utilisant un objet `TimeType` et en appliquant le `format` fourni. Les codes de caractères suivants peuvent être utilisés pour construire la chaîne `format` :

| Code | Exemples | Commentaire                                         |
|:---- |:-------- |:--------------------------------------------------- |
| `y`  | 6        | Année numérique avec une largeur fixe               |
| `Y`  | 1996     | Année numérique avec une largeur minimale           |
| `m`  | 1, 12    | Mois numérique avec une largeur minimale            |
| `u`  | Jan      | Nom du mois abrégé à 3 caractères selon le `locale` |
| `U`  | Janvier  | Nom complet du mois selon le mot-clé `locale`       |
| `d`  | 1, 31    | Jour du mois avec une largeur minimale              |
| `H`  | 0, 23    | Heure (horloge 24 heures) avec une largeur minimale |
| `M`  | 0, 59    | Minute avec une largeur minimale                    |
| `S`  | 0, 59    | Seconde avec une largeur minimale                   |
| `s`  | 000, 500 | Milliseconde avec une largeur minimale de 3         |
| `e`  | Lun, Mar | Jours de la semaine abrégés                         |
| `E`  | Lundi    | Nom complet du jour de la semaine                   |

Le nombre de caractères de code séquentiels indique la largeur du code. Un format de `yyyy-mm` spécifie que le code `y` doit avoir une largeur de quatre tandis que `m` une largeur de deux. Les codes qui produisent des chiffres numériques ont un mode associé : largeur fixe ou largeur minimale. Le mode à largeur fixe ajoute des zéros à gauche lorsque la valeur est plus courte que la largeur spécifiée et tronque la valeur lorsqu'elle est plus longue. Le mode à largeur minimale fonctionne de la même manière que le mode à largeur fixe, sauf qu'il ne tronque pas les valeurs plus longues que la largeur.

Lors de la création d'un `format`, vous pouvez utiliser n'importe quel caractère non code comme séparateur. Par exemple, pour générer la chaîne "1996-01-15T00:00:00", vous pourriez utiliser `format` : "yyyy-mm-ddTHH:MM:SS". Notez que si vous devez utiliser un caractère de code comme littéral, vous pouvez utiliser le caractère d'échappement backslash. La chaîne "1996y01m" peut être produite avec le format "yyyy\ymm\m".
