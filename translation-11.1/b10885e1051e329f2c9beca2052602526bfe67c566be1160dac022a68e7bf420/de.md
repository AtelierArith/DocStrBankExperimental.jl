```
LibGit2.read_tree!(idx::GitIndex, tree::GitTree)
LibGit2.read_tree!(idx::GitIndex, treehash::AbstractGitHash)
```

Lese den Baum `tree` (oder den Baum, auf den `treehash` im vom `idx` besessenen Repository zeigt) in den Index `idx`. Der aktuelle Inhalt des Index wird ersetzt.
