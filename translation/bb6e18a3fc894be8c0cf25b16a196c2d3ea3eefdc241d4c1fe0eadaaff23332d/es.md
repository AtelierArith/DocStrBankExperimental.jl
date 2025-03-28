```
committer(c::GitCommit)
```

Devuelve la `Signature` del committer del commit `c`. El committer es la persona que realizó los cambios originalmente creados por el [`author`](@ref), pero no tiene que ser el mismo que el `author`, por ejemplo, si el `author` envió un parche a un `committer` que lo comprometió.
