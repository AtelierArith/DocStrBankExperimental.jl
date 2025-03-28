```
callers(funcname, [data, lidict], [filename=<filename>], [linerange=<start:stop>]) -> Vector{Tuple{count, lineinfo}}
```

Étant donné une exécution de profilage précédente, déterminez qui a appelé une fonction particulière. Fournir le nom de fichier (et éventuellement, la plage de numéros de ligne sur laquelle la fonction est définie) vous permet de désambiguïser une méthode surchargée. La valeur retournée est un vecteur contenant un compte du nombre d'appels et des informations de ligne sur l'appelant. On peut optionnellement fournir un `data` de backtrace obtenu à partir de [`retrieve`](@ref); sinon, le tampon de profilage interne actuel est utilisé.
