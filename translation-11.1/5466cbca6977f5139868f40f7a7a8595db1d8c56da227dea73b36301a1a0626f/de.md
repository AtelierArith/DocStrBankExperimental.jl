```
merge!(repo::GitRepo, anns::Vector{GitAnnotated}, fastforward::Bool; kwargs...) -> Bool
```

Mergen Sie Änderungen aus den annotierten Commits (erfasst als [`GitAnnotated`](@ref) Objekte) `anns` in den HEAD des Repositories `repo`. Wenn `fastforward` `true` ist, ist *nur* ein Fast-Forward-Merge erlaubt. In diesem Fall schlägt der Merge fehl, wenn Konflikte auftreten. Andernfalls, wenn `fastforward` `false` ist, kann der Merge eine Konfliktdatei erzeugen, die der Benutzer lösen muss.

Die Schlüsselwortargumente sind:

  * `merge_opts::MergeOptions = MergeOptions()`: Optionen für die Durchführung des Merges, einschließlich ob Fast-Forwarding erlaubt ist. Siehe [`MergeOptions`](@ref) für weitere Informationen.
  * `checkout_opts::CheckoutOptions = CheckoutOptions()`: Optionen für die Durchführung des Checkouts. Siehe [`CheckoutOptions`](@ref) für weitere Informationen.

`anns` kann sich auf lokale oder entfernte Branch-Köpfe beziehen. Gibt `true` zurück, wenn der Merge erfolgreich ist, andernfalls `false` (zum Beispiel, wenn kein Merge möglich ist, weil die Branches keinen gemeinsamen Vorfahren haben).

# Beispiele

```julia
upst_ann_1 = LibGit2.GitAnnotated(repo, "branch/a")

# merge den Branch ein, fastforward
LibGit2.merge!(repo, [upst_ann_1], true)

# Merge-Konflikte!
upst_ann_2 = LibGit2.GitAnnotated(repo, "branch/b")
# merge den Branch ein, versuche fastforward
LibGit2.merge!(repo, [upst_ann_2], true) # wird false zurückgeben
LibGit2.merge!(repo, [upst_ann_2], false) # wird true zurückgeben
```
