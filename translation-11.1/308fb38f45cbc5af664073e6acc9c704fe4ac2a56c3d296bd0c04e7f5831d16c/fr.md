```
unsafe_string(p::Ptr{UInt8}, [length::Integer])
```

Copie une chaîne à partir de l'adresse d'une chaîne de style C (terminée par NUL) encodée en UTF-8. (Le pointeur peut être libéré en toute sécurité par la suite.) Si `length` est spécifié (la longueur des données en octets), la chaîne n'a pas besoin d'être terminée par NUL.

Cette fonction est étiquetée "unsafe" car elle plantera si `p` n'est pas une adresse mémoire valide pour des données de la longueur demandée.
