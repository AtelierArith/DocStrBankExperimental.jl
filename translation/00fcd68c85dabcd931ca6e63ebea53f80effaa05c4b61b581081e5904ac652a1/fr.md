```
strptime([format], timestr)
```

Analyse une chaîne de caractères de temps formatée en un `TmStruct` donnant les secondes, la minute, l'heure, la date, etc. Les formats pris en charge sont les mêmes que ceux de la bibliothèque standard C. Sur certaines plateformes, les fuseaux horaires ne seront pas analysés correctement. Si le résultat de cette fonction doit être passé à `time` pour le convertir en secondes depuis l'époque, le champ `isdst` doit être rempli manuellement. Le définir à `-1` indiquera à la bibliothèque C d'utiliser les paramètres système actuels pour déterminer le fuseau horaire.
