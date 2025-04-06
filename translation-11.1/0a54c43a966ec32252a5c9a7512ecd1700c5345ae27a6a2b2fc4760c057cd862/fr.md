```
syevd!(jobz, uplo, A)
```

Trouve les valeurs propres (`jobz = N`) ou les valeurs propres et les vecteurs propres (`jobz = V`) d'une matrice symétrique `A`. Si `uplo = U`, le triangle supérieur de `A` est utilisé. Si `uplo = L`, le triangle inférieur de `A` est utilisé.

Utilise la méthode de diviser pour régner, au lieu de l'itération QR utilisée par `syev!` ou des représentations relativement robustes multiples utilisées par `syevr!`. Voir James W. Demmel et al, SIAM J. Sci. Comput. 30, 3, 1508 (2008) pour une comparaison de la précision et des performances des différentes méthodes.
