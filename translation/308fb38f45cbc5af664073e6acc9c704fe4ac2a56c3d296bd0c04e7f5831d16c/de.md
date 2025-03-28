```
unsafe_string(p::Ptr{UInt8}, [length::Integer])
```

Kopiere einen String von der Adresse eines C-Stil (NUL-terminierten) Strings, der als UTF-8 kodiert ist. (Der Zeiger kann danach sicher freigegeben werden.) Wenn `length` angegeben ist (die Länge der Daten in Bytes), muss der String nicht NUL-terminiert sein.

Diese Funktion ist als "unsicher" gekennzeichnet, da sie abstürzt, wenn `p` keine gültige Speicheradresse für Daten der angeforderten Länge ist.
