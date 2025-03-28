```
StackFrame
```

Informations sur la pile représentant le contexte d'exécution, avec les champs suivants :

  * `func::Symbol`

    Le nom de la fonction contenant le contexte d'exécution.
  * `linfo::Union{Core.MethodInstance, Method, Module, Core.CodeInfo, Nothing}`

    L'instance de méthode ou les informations de code contenant le contexte d'exécution (si cela a pu être trouvé), ou le module (pour les expansions de macro).
  * `file::Symbol`

    Le chemin vers le fichier contenant le contexte d'exécution.
  * `line::Int`

    Le numéro de ligne dans le fichier contenant le contexte d'exécution.
  * `from_c::Bool`

    Vrai si le code provient de C.
  * `inlined::Bool`

    Vrai si le code provient d'une trame en ligne.
  * `pointer::UInt64`

    Représentation du pointeur vers le contexte d'exécution tel que retourné par `backtrace`.
