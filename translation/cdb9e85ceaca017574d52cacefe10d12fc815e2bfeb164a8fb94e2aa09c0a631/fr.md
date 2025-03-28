```
DateFormat(format::AbstractString, locale="français") -> DateFormat
```

Construisez un objet de formatage de date qui peut être utilisé pour analyser des chaînes de date ou formater un objet date en tant que chaîne. Les codes de caractères suivants peuvent être utilisés pour construire la chaîne `format` :

| Code       | Correspond à | Commentaire                                                                 |
|:---------- |:------------ |:--------------------------------------------------------------------------- |
| `Y`        | 1996, 96     | Renvoie l'année de 1996, 0096                                               |
| `y`        | 1996, 96     | Identique à `Y` sur `parse` mais ignore les chiffres excessifs sur `format` |
| `m`        | 1, 01        | Correspond à des mois de 1 ou 2 chiffres                                    |
| `u`        | Jan          | Correspond à des mois abrégés selon le mot-clé `locale`                     |
| `U`        | Janvier      | Correspond à des noms de mois complets selon le mot-clé `locale`            |
| `d`        | 1, 01        | Correspond à des jours de 1 ou 2 chiffres                                   |
| `H`        | 00           | Correspond aux heures (horloge 24 heures)                                   |
| `I`        | 00           | Pour afficher les heures avec une horloge de 12 heures                      |
| `M`        | 00           | Correspond aux minutes                                                      |
| `S`        | 00           | Correspond aux secondes                                                     |
| `s`        | .500         | Correspond aux millisecondes                                                |
| `e`        | Lun, Mar     | Correspond à des jours abrégés de la semaine                                |
| `E`        | Lundi        | Correspond à des noms complets des jours de la semaine                      |
| `p`        | AM           | Correspond à AM/PM (insensible à la casse)                                  |
| `yyyymmdd` | 19960101     | Correspond à l'année, au mois et au jour à largeur fixe                     |

Les caractères non listés ci-dessus sont normalement traités comme des délimiteurs entre les slots de date et d'heure. Par exemple, une chaîne `dt` de "1996-01-15T00:00:00.0" aurait une chaîne `format` comme "y-m-dTH:M:S.s". Si vous devez utiliser un caractère de code comme délimiteur, vous pouvez l'échapper en utilisant un antislash. La date "1995y01m" aurait le format "y\ym\m".

Notez que 12:00AM correspond à 00:00 (minuit), et 12:00PM correspond à 12:00 (midi). Lors de l'analyse d'une heure avec un spécificateur `p`, toute heure (soit `H` ou `I`) est interprétée comme une horloge de 12 heures, donc le code `I` est principalement utile pour la sortie.

Créer un objet DateFormat est coûteux. Chaque fois que cela est possible, créez-le une fois et utilisez-le plusieurs fois ou essayez la macro de chaîne [`dateformat""`](@ref @dateformat_str). L'utilisation de cette macro crée l'objet DateFormat une fois au moment de l'expansion de la macro et le réutilise plus tard. Il existe également plusieurs [formatteurs pré-définis](@ref Common-Date-Formatters), listés plus loin.

Voir [`DateTime`](@ref) et [`format`](@ref) pour savoir comment utiliser un objet DateFormat pour analyser et écrire des chaînes de date respectivement.
