```
Threads.atomic_fence()
```

Fügen Sie einen Speicherzaun mit sequentieller Konsistenz ein

Fügt einen Speicherzaun mit sequentiell konsistenten Ordnungssemantiken ein. Es gibt Algorithmen, bei denen dies erforderlich ist, d.h. bei denen eine Acquire/Release-Ordnung nicht ausreicht.

Dies ist wahrscheinlich eine sehr kostspielige Operation. Da alle anderen atomaren Operationen in Julia bereits über Acquire/Release-Semantiken verfügen, sollten explizite Zäune in den meisten Fällen nicht erforderlich sein.

Für weitere Details siehe die `fence`-Anweisung von LLVM.
