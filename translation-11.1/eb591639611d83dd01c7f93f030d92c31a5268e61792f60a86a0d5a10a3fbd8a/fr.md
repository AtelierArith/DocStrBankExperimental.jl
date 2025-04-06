```
trsen!(job, compq, select, T, Q) -> (T, Q, w, s, sep)
trsen!(select, T, Q) -> (T, Q, w, s, sep)
```

Réorganise la factorisation de Schur d'une matrice et trouve éventuellement des nombres de condition réciproques. Si `job = N`, aucun nombre de condition n'est trouvé. Si `job = E`, seul le nombre de condition pour ce groupe de valeurs propres est trouvé. Si `job = V`, seul le nombre de condition pour l'espace invariant est trouvé. Si `job = B`, alors les nombres de condition pour le groupe et l'espace sont trouvés. Si `compq = V`, les vecteurs de Schur `Q` sont mis à jour. Si `compq = N`, les vecteurs de Schur ne sont pas modifiés. `select` détermine quelles valeurs propres sont dans le groupe. La méthode à 3 arguments appelle la méthode à 5 arguments avec `job = N` et `compq = V`.

Retourne `T`, `Q`, les valeurs propres réordonnées dans `w`, le nombre de condition du groupe de valeurs propres `s`, et le nombre de condition de l'espace invariant `sep`.
