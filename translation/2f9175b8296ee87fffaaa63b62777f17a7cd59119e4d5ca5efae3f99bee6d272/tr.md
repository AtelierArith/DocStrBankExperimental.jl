```
DEPOT_PATH
```

Paket yöneticisinin ve Julia'nın kod yükleme mekanizmalarının paket kayıtlarını, kurulu paketleri, adlandırılmış ortamları, repo kopyalarını, önbelleğe alınmış derlenmiş paket görüntülerini ve yapılandırma dosyalarını aradığı "depot" konumlarının bir yığını. Varsayılan olarak şunları içerir:

1. `~/.julia` burada `~` sistemde uygun olan kullanıcı ana dizinidir;
2. mimariye özgü paylaşılan bir sistem dizini, örneğin `/usr/local/share/julia`;
3. mimariden bağımsız paylaşılan bir sistem dizini, örneğin `/usr/share/julia`.

Yani `DEPOT_PATH` şu şekilde olabilir:

```julia
[joinpath(homedir(), ".julia"), "/usr/local/share/julia", "/usr/share/julia"]
```

İlk giriş "kullanıcı deposu"dur ve mevcut kullanıcı tarafından yazılabilir ve sahip olunmalıdır. Kullanıcı deposu, kayıtların kopyalandığı, yeni paket sürümlerinin kurulduğu, adlandırılmış ortamların oluşturulup güncellendiği, paket reposunun kopyalandığı, yeni derlenmiş paket görüntü dosyalarının kaydedildiği, günlük dosyalarının yazıldığı, geliştirme paketlerinin varsayılan olarak kontrol edildiği ve küresel yapılandırma verilerinin kaydedildiği yerdir. Depo yolundaki sonraki girişler yalnızca okunur olarak kabul edilir ve sistem yöneticileri tarafından kurulan ve yönetilen kayıtlar, paketler vb. için uygundur.

`DEPOT_PATH`, ayarlanmışsa [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) ortam değişkenine dayalı olarak doldurulur.

## DEPOT_PATH içeriği

`DEPOT_PATH`'deki her giriş, Julia'nın çeşitli amaçlar için kullandığı alt dizinleri içeren bir dizine giden bir yoldur. İşte bir depoda var olabilecek bazı alt dizinlerin genel bir görünümü:

  * `artifacts`: Paketlerin kurulumunu yönettiği içerikleri içerir.
  * `clones`: Paket reposunun tam kopyalarını içerir. `Pkg.jl` tarafından korunur ve önbellek olarak kullanılır.
  * `config`: `startup.jl` gibi julia düzeyinde yapılandırmaları içerir.
  * `compiled`: Paketler için önceden derlenmiş `*.ji` dosyalarını içerir. Julia tarafından korunur.
  * `dev`: `Pkg.develop` için varsayılan dizin. `Pkg.jl` ve kullanıcı tarafından korunur.
  * `environments`: Varsayılan paket ortamları. Örneğin, belirli bir julia sürümü için küresel ortam. `Pkg.jl` tarafından korunur.
  * `logs`: `Pkg` ve `REPL` işlemlerinin günlüklerini içerir. `Pkg.jl` ve `Julia` tarafından korunur.
  * `packages`: Bazıları açıkça kurulan ve bazıları örtük bağımlılıklar olan paketleri içerir. `Pkg.jl` tarafından korunur.
  * `registries`: Paket kayıtlarını içerir. Varsayılan olarak yalnızca `General`. `Pkg.jl` tarafından korunur.
  * `scratchspaces`: Bir paketin kendisinin [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl) paketi aracılığıyla kurduğu içerikleri içerir. `Pkg.gc()` kullanılmayan olarak bilinen içeriği silecektir.

!!! not
    İçerik depolamak isteyen paketler, depo kökünde yeni alt dizinler oluşturmak yerine [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl) aracılığıyla `scratchspaces` alt dizinini kullanmalıdır.


Ayrıca bkz. [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) ve [Kod Yükleme](@ref code-loading).
