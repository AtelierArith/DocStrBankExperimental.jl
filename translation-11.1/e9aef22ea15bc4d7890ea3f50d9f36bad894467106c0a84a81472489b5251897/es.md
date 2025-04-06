```
merge!(repo::GitRepo; kwargs...) -> Bool
```

Realiza una fusión de git en el repositorio `repo`, fusionando commits con historia divergente en la rama actual. Devuelve `true` si la fusión tuvo éxito, `false` si no.

Los argumentos clave son:

  * `committish::AbstractString=""`: Fusiona el/los commit(s) nombrados en `committish`.
  * `branch::AbstractString=""`: Fusiona la rama `branch` y todos sus commits desde que divergió de la rama actual.
  * `fastforward::Bool=false`: Si `fastforward` es `true`, solo fusiona si la fusión es un avance rápido (la cabeza de la rama actual es un ancestro de los commits a fusionar), de lo contrario, se niega a fusionar y devuelve `false`. Esto es equivalente a la opción de CLI de git `--ff-only`.
  * `merge_opts::MergeOptions=MergeOptions()`: `merge_opts` especifica opciones para la fusión, como la estrategia de fusión en caso de conflictos.
  * `checkout_opts::CheckoutOptions=CheckoutOptions()`: `checkout_opts` especifica opciones para el paso de checkout.

Equivalente a `git merge [--ff-only] [<committish> | <branch>]`.

!!! nota
    Si especificas una `branch`, esto debe hacerse en formato de referencia, ya que la cadena se convertirá en un `GitReference`. Por ejemplo, si quisieras fusionar la rama `branch_a`, llamarías a `merge!(repo, branch="refs/heads/branch_a")`.

