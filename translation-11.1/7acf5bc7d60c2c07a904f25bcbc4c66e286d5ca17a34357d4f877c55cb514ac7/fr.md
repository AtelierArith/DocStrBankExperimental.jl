```
config( <voir arguments> )
```

Fonction uniquement par mots-clés pour configurer les paramètres du menu global

# Arguments

  * `charset::Symbol=:na`: caractères d'interface à utiliser (`:ascii` ou `:unicode`); remplacé par d'autres arguments
  * `cursor::Char='>'|'→'`: caractère à utiliser pour le curseur
  * `up_arrow::Char='^'|'↑'`: caractère à utiliser pour la flèche vers le haut
  * `down_arrow::Char='v'|'↓'`: caractère à utiliser pour la flèche vers le bas
  * `checked::String="[X]"|"✓"`: chaîne à utiliser pour coché
  * `unchecked::String="[ ]"|"⬚")`: chaîne à utiliser pour non coché
  * `scroll::Symbol=:nowrap`: Si `:wrap` le curseur se déplace autour du haut et du bas, si `:nowrap` ne pas déplacer le curseur
  * `supress_output::Bool=false`: Argument hérité ignoré, passez `suppress_output` comme argument de mot-clé à `request` à la place.
  * `ctrl_c_interrupt::Bool=true`: Si `false`, retourne vide sur ^C, si `true` lance InterruptException() sur ^C

!!! compat "Julia 1.6"
    À partir de Julia 1.6, `config` est obsolète. Utilisez `Config` ou `MultiSelectConfig` à la place.

