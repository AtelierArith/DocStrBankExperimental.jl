```
merge!(repo::GitRepo; kwargs...) -> Bool
```

Führen Sie einen Git-Merge im Repository `repo` durch, indem Sie Commits mit divergierender Historie in den aktuellen Branch zusammenführen. Gibt `true` zurück, wenn der Merge erfolgreich war, andernfalls `false`.

Die Schlüsselwortargumente sind:

  * `committish::AbstractString=""`: Führen Sie die benannten Commits in `committish` zusammen.
  * `branch::AbstractString=""`: Führen Sie den Branch `branch` und alle seine Commits seit der Divergenz vom aktuellen Branch zusammen.
  * `fastforward::Bool=false`: Wenn `fastforward` `true` ist, führen Sie nur zusammen, wenn der Merge ein Fast-Forward ist (der aktuelle Branch-Kopf ist ein Vorfahre der zusammenzuführenden Commits), andernfalls verweigern Sie den Merge und geben `false` zurück. Dies entspricht der Git-CLI-Option `--ff-only`.
  * `merge_opts::MergeOptions=MergeOptions()`: `merge_opts` gibt Optionen für den Merge an, wie z.B. die Merge-Strategie im Falle von Konflikten.
  * `checkout_opts::CheckoutOptions=CheckoutOptions()`: `checkout_opts` gibt Optionen für den Checkout-Schritt an.

Entspricht `git merge [--ff-only] [<committish> | <branch>]`.

!!! Hinweis     Wenn Sie einen `branch` angeben, muss dies im Referenzformat erfolgen, da der String in eine `GitReference` umgewandelt wird. Wenn Sie beispielsweise den Branch `branch_a` zusammenführen möchten, würden Sie `merge!(repo, branch="refs/heads/branch_a")` aufrufen.
