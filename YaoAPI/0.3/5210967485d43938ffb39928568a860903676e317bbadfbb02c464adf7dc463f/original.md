```
measure!([postprocess,] [operator, ]register[, locs]; rng=Random.GLOBAL_RNG)
```

Measure current active qudits or qudits at `locs`. After measure and collapse,

```
* do nothing if postprocess is `NoPostProcess`
* reset to result state to `postprocess.config` if `postprocess` is `ResetTo`.
* remove the qubit if `postprocess` is `RemoveMeasured`
```
