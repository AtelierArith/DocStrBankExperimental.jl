```
isascii(cu::AbstractVector{CU}) where {CU <: Integer} -> Bool
```

Testez si toutes les valeurs du vecteur appartiennent à l'ensemble de caractères ASCII (0x00 à 0x7f). Cette fonction est destinée à être utilisée par d'autres implémentations de chaînes qui ont besoin d'une vérification ASCII rapide.
