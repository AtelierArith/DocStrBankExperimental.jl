```
geev!(jobvl, jobvr, A) -> (W, VL, VR)
```

Trouve le système d'autovalues de `A`. Si `jobvl = N`, les autovecteurs à gauche de `A` ne sont pas calculés. Si `jobvr = N`, les autovecteurs à droite de `A` ne sont pas calculés. Si `jobvl = V` ou `jobvr = V`, les autovecteurs correspondants sont calculés. Renvoie les autovalues dans `W`, les autovecteurs à droite dans `VR`, et les autovecteurs à gauche dans `VL`.
