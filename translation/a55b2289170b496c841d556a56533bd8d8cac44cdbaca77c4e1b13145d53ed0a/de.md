```
LibGit2.push!(w::GitRevWalker, cid::GitHash)
```

Starten Sie den [`GitRevWalker`](@ref) `walker` bei dem Commit `cid`. Diese Funktion kann verwendet werden, um eine Funktion auf alle Commits seit einem bestimmten Jahr anzuwenden, indem der erste Commit dieses Jahres als `cid` übergeben wird und dann das resultierende `w` an [`LibGit2.map`](@ref) übergeben wird.
