```
XPRS_CORESPERCPU
```

Used to override the detected value of the number of cores on a CPU. (integer)

The cache size (either detected or specified via the CACHESIZE control) used in Barrier methods will be divided by this amount, and this scaled-down value will be the amount of cache allocated to each Barrier thread

Default value: `-1`

Domain: -1~+INF
