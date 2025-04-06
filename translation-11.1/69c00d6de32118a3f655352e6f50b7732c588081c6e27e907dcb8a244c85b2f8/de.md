```
setcpuaffinity(original_command::Cmd, cpus) -> command::Cmd
```

Setzen Sie die CPU-Affinität des `command` durch eine Liste von CPU-IDs (1-basiert) `cpus`. Das Übergeben von `cpus = nothing` bedeutet, die CPU-Affinität zurückzusetzen, wenn der `original_command` eine hat.

Diese Funktion wird nur in Linux und Windows unterstützt. Sie wird in macOS nicht unterstützt, da libuv die Einstellung der Affinität nicht unterstützt.

!!! compat "Julia 1.8"
    Diese Funktion erfordert mindestens Julia 1.8.


# Beispiele

In Linux kann das Kommandozeilenprogramm `taskset` verwendet werden, um zu sehen, wie `setcpuaffinity` funktioniert.

```julia
julia> run(setcpuaffinity(`sh -c 'taskset -p $$'`, [1, 2, 5]));
pid 2273's current affinity mask: 13
```

Beachten Sie, dass der Maskenwert `13` widerspiegelt, dass das erste, zweite und das fünfte Bit (gezählt von der am wenigsten signifikanten Position) eingeschaltet sind:

```julia
julia> 0b010011
0x13
```
