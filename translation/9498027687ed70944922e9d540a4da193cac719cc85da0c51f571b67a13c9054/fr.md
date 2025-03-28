```
memoryref(::GenericMemory, index::Integer)
memoryref(::GenericMemoryRef, index::Integer)
```

Construit un `GenericMemoryRef` à partir d'un objet mémoire et d'un index de décalage (basé sur 1) qui peut également être négatif. Cela renvoie toujours un objet dans les limites, et générera une erreur si cela n'est pas possible (car l'index entraînerait un décalage hors limites de la mémoire sous-jacente).
