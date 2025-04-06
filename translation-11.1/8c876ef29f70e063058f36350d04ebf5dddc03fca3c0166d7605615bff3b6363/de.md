```
GitShortHash(hash::GitHash, len::Integer)
```

Ein verkürzter Git-Objektbezeichner, der verwendet werden kann, um ein Git-Objekt zu identifizieren, wenn es eindeutig ist, und der aus den ersten `len` hexadezimalen Ziffern von `hash` besteht (die verbleibenden Ziffern werden ignoriert).
