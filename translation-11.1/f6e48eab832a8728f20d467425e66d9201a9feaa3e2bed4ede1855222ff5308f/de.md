```
splitdrive(path::AbstractString) -> (AbstractString, AbstractString)
```

Unter Windows wird ein Pfad in den Laufwerksbuchstaben und den Pfadteil aufgeteilt. Unter Unix-Systemen ist die erste Komponente immer der leere String.
