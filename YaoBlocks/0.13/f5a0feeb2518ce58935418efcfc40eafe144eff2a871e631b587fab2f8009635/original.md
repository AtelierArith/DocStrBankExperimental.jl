```
isclean(entries::EntryTable; zero_threshold=0.0)
```

Return true if the entries are ordered, unique and amplitudes are nonzero. Any value with amplitude ≤ `zero_threshold` will be regarded as zero.
