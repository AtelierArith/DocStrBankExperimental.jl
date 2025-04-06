```
LibGit2.RebaseOptions
```

Coincide con la estructura `git_rebase_options`.

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `quiet`: informar a otros clientes de git que ayudan con/trabajan en el rebase que el rebase debe hacerse "silenciosamente". Utilizado para la interoperabilidad. El valor predeterminado es `1`.
  * `inmemory`: iniciar un rebase en memoria. Los llamadores que trabajan en el rebase pueden seguir sus pasos y confirmar cualquier cambio, pero no pueden retroceder HEAD ni actualizar el repositorio. El [`workdir`](@ref) no se modificará. Solo presente en versiones de libgit2 más nuevas o iguales a 0.24.0.
  * `rewrite_notes_ref`: nombre de la referencia a notas que se utilizarán para reescribir las notas de confirmación a medida que se complete el rebase.
  * `merge_opts`: opciones de fusión que controlan cómo se fusionarán los árboles en cada paso del rebase. Solo presente en versiones de libgit2 más nuevas o iguales a 0.24.0.
  * `checkout_opts`: opciones de checkout para escribir archivos al inicializar el rebase, avanzar a través de él y abortarlo. Consulte [`CheckoutOptions`](@ref) para más información.
