```
maxintfloat(T, S)
```

Le plus grand entier consécutif représentable dans le type de flottant donné `T` qui ne dépasse pas non plus l'entier maximum représentable par le type entier `S`. En d'autres termes, c'est le minimum de `maxintfloat(T)` et de [`typemax(S)`](@ref).
