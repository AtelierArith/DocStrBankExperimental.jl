```
setcpuaffinity(original_command::Cmd, cpus) -> command::Cmd
```

`command`'ın CPU bağlılığını, bir CPU ID'leri (1 tabanlı) listesi `cpus` ile ayarlayın. `cpus = nothing` geçmek, `original_command`'ın herhangi bir CPU bağlılığı varsa bunu kaldırmak anlamına gelir.

Bu fonksiyon yalnızca Linux ve Windows'ta desteklenmektedir. macOS'ta desteklenmemektedir çünkü libuv bağlılık ayarlamayı desteklememektedir.

!!! compat "Julia 1.8"
    Bu fonksiyon en az Julia 1.8 gerektirir.


# Örnekler

Linux'ta, `taskset` komut satırı programı `setcpuaffinity`'nin nasıl çalıştığını görmek için kullanılabilir.

```julia
julia> run(setcpuaffinity(`sh -c 'taskset -p $$'`, [1, 2, 5]));
pid 2273's current affinity mask: 13
```

Maske değeri `13`'ün, ilk, ikinci ve beşinci bitlerin (en az anlamlı konumdan sayarak) açık olduğunu yansıttığını unutmayın:

```julia
julia> 0b010011
0x13
```
