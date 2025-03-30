```
Base.identify_package(name::String)::Union{PkgId, Nothing}
Base.identify_package(where::Union{Module,PkgId}, name::String)::Union{PkgId, Nothing}
```

Mevcut ortam yığınından adıyla paketi tanımlayın, `PkgId`'sini döndürün veya bulunamazsa `nothing` döndürün.

Sadece `name` argümanı sağlanırsa, yığın içindeki her ortamı ve adlandırılmış doğrudan bağımlılıklarını arar.

`where` argümanı, paketi aramak için bağlamı sağlar: bu durumda önce adın bağlamın kendisiyle eşleşip eşleşmediğini kontrol eder, aksi takdirde bağlam `where`'yi bulana kadar her ortamın çözülmüş manifestosundan tüm özyinelemeli bağımlılıkları arar ve oradan karşılık gelen adla bağımlılığı tanımlar.

```julia-repl
julia> Base.identify_package("Pkg") # Pkg varsayılan ortamın bir bağımlılığıdır
Pkg [44cfe95a-1eb2-52ea-b672-e2afdf69b78f]

julia> using LinearAlgebra

julia> Base.identify_package(LinearAlgebra, "Pkg") # Pkg LinearAlgebra'nın bir bağımlılığı değildir
```
