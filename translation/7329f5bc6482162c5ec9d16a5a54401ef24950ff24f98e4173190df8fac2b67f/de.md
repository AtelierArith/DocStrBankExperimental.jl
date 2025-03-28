```
merge!(repo::GitRepo, anns::Vector{GitAnnotated}; kwargs...) -> Bool
```

Mergen Sie Änderungen aus den annotierten Commits (erfasst als [`GitAnnotated`](@ref) Objekte) `anns` in den HEAD des Repositories `repo`. Die Schlüsselwortargumente sind:

  * `merge_opts::MergeOptions = MergeOptions()`: Optionen, wie das Mergen durchgeführt werden soll, einschließlich ob Fast-Forwarding erlaubt ist. Siehe [`MergeOptions`](@ref) für weitere Informationen.
  * `checkout_opts::CheckoutOptions = CheckoutOptions()`: Optionen, wie der Checkout durchgeführt werden soll. Siehe [`CheckoutOptions`](@ref) für weitere Informationen.

`anns` kann sich auf entfernte oder lokale Branch-Köpfe beziehen. Gibt `true` zurück, wenn das Mergen erfolgreich ist, andernfalls `false` (zum Beispiel, wenn kein Mergen möglich ist, weil die Branches keinen gemeinsamen Vorfahren haben).

# Beispiele

```julia
upst_ann = LibGit2.GitAnnotated(repo, "branch/a")

# den Branch mergen
LibGit2.merge!(repo, [upst_ann])
```
