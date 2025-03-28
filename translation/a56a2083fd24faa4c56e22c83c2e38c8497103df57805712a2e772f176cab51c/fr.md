```
codepoint(c::AbstractChar) -> Integer
```

Renvoie le point de code Unicode (un entier non signé) correspondant au caractère `c` (ou lève une exception si `c` ne représente pas un caractère valide). Pour `Char`, il s'agit d'une valeur `UInt32`, mais les types `AbstractChar` qui ne représentent qu'un sous-ensemble de Unicode peuvent renvoyer un entier de taille différente (par exemple, `UInt8`).
