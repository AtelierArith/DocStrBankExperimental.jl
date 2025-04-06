```
committer(c::GitCommit)
```

Gibt die `Signature` des Committers des Commits `c` zurück. Der Committer ist die Person, die die Änderungen ursprünglich, die vom [`author`](@ref) verfasst wurden, committet hat, muss jedoch nicht die gleiche Person wie der `author` sein, zum Beispiel, wenn der `author` einen Patch an einen `committer` gesendet hat, der ihn dann committet hat.
