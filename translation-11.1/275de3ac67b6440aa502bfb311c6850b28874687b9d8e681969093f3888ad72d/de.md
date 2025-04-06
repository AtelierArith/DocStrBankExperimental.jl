```
LibGit2.push_head!(w::GitRevWalker)
```

Schiebt den HEAD-Commit und seine Vorfahren auf den [`GitRevWalker`](@ref) `w`. Dies stellt sicher, dass HEAD und alle seine Vorfahren während des Durchlaufs getroffen werden.
