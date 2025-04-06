```
as
```

`as` est utilisé comme un mot-clé pour renommer un identifiant introduit dans le scope par `import` ou `using`, dans le but de contourner les conflits de noms ainsi que pour raccourcir les noms.  (En dehors des déclarations `import` ou `using`, `as` n'est pas un mot-clé et peut être utilisé comme un identifiant ordinaire.)

`import LinearAlgebra as LA` amène la bibliothèque standard `LinearAlgebra` importée dans le scope sous le nom `LA`.

`import LinearAlgebra: eigen as eig, cholesky as chol` amène les méthodes `eigen` et `cholesky` de `LinearAlgebra` dans le scope sous les noms `eig` et `chol` respectivement.

`as` fonctionne avec `using` uniquement lorsque des identifiants individuels sont introduits dans le scope. Par exemple, `using LinearAlgebra: eigen as eig` ou `using LinearAlgebra: eigen as eig, cholesky as chol` fonctionne, mais `using LinearAlgebra as LA` est une syntaxe invalide, car il est insensé de renommer *tous* les noms exportés de `LinearAlgebra` en `LA`.
