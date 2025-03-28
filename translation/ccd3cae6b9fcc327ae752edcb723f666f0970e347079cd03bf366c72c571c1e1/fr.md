```
gglse!(A, c, B, d) -> (X,res)
```

Résout l'équation `A * x = c` où `x` est soumis à la contrainte d'égalité `B * x = d`. Utilise la formule `||c - A*x||^2 = 0` pour résoudre. Renvoie `X` et la somme des carrés résiduels.
