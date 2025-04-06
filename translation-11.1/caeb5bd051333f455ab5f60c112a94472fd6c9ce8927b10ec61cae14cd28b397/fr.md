```
isbinary(blob::GitBlob) -> Bool
```

Utilisez une heuristique pour deviner si un fichier est binaire : rechercher des octets NULL et examiner un rapport raisonnable de caractères imprimables à non imprimables parmi les 8000 premiers octets.
