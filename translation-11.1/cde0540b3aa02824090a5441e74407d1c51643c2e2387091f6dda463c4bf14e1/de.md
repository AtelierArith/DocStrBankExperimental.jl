```
remove_frames!(stack::StackTrace, name::Symbol)
```

Nimmt einen `StackTrace` (ein Vektor von `StackFrames`) und einen Funktionsnamen (ein `Symbol`) und entfernt den `StackFrame`, der durch den Funktionsnamen im `StackTrace` angegeben ist (entfernt auch alle Frames über der angegebenen Funktion). Wird hauptsächlich verwendet, um `StackTraces`-Funktionen aus dem `StackTrace` zu entfernen, bevor er zurückgegeben wird.
