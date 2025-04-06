# Calling Conventions

Julia utilise trois conventions d'appel pour quatre objectifs distincts :

| Name    | Prefix    | Purpose                          |
|:------- |:--------- |:-------------------------------- |
| Native  | `julia_`  | Speed via specialized signatures |
| JL Call | `jlcall_` | Wrapper for generic calls        |
| JL Call | `jl_`     | Builtins                         |
| C ABI   | `jlcapi_` | Wrapper callable from C          |

## Julia Native Calling Convention

La convention d'appel native est conçue pour des appels rapides non génériques. Elle utilise généralement une signature spécialisée.

  * Les fantômes LLVM (types de longueur nulle) sont omis.
  * Les scalaires et les vecteurs LLVM sont passés par valeur.
  * Les agrégats LLVM (tableaux et structures) sont passés par référence.

Une petite valeur de retour est renvoyée en tant que valeurs de retour LLVM. Une grande valeur de retour est renvoyée via la convention de "retour de structure" (`sret`), où l'appelant fournit un pointeur vers un emplacement de retour.

Un argument ou des valeurs de retour qui sont un tuple homogène sont parfois représentés comme un vecteur LLVM au lieu d'un tableau LLVM.

## JL Call Convention

La convention d'appel JL est destinée aux fonctions intégrées et à l'envoi générique. Les fonctions écrites à la main utilisant cette convention sont déclarées via la macro `JL_CALLABLE`. La convention utilise exactement 3 paramètres :

  * `F`  - Représentation Julia de la fonction qui est appliquée
  * `args` - pointeur vers un tableau de pointeurs vers des boîtes
  * `nargs` - longueur du tableau

La valeur de retour est un pointeur vers une boîte.

## C ABI

Les wrappers C ABI permettent d'appeler Julia depuis C. Le wrapper appelle une fonction en utilisant la convention d'appel native.

Les tuples sont toujours représentés comme des tableaux C.
