```
remove_frames!(stack::StackTrace, name::Symbol)
```

Prend un `StackTrace` (un vecteur de `StackFrames`) et un nom de fonction (un `Symbol`) et supprime le `StackFrame` spécifié par le nom de la fonction du `StackTrace` (supprimant également tous les frames au-dessus de la fonction spécifiée). Utilisé principalement pour supprimer les `StackTraces` des fonctions du `StackTrace` avant de le retourner.
