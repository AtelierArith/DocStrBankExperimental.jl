```
SpinLock()
```

Erstellen Sie ein nicht-reentrantes Spinlock mit Test-and-Test-and-Set. Rekursive Verwendung führt zu einem Deadlock. Diese Art von Lock sollte nur um Code verwendet werden, der wenig Zeit in Anspruch nimmt und nicht blockiert (z. B. I/O durchführt). Im Allgemeinen sollte stattdessen [`ReentrantLock`](@ref) verwendet werden.

Jeder [`lock`](@ref) muss mit einem [`unlock`](@ref) übereinstimmen. Wenn [`!islocked(lck::SpinLock)`](@ref islocked) gilt, gelingt [`trylock(lck)`](@ref trylock), es sei denn, es gibt andere Aufgaben, die versuchen, das Lock "zur gleichen Zeit" zu halten.

Test-and-Test-and-Set Spinlocks sind bis zu etwa 30 konkurrierenden Threads am schnellsten. Wenn Sie mehr Konkurrenz als das haben, sollten andere Synchronisationsansätze in Betracht gezogen werden.
