# Module loading

[`Base.require`](@ref) modülleri yüklemekten sorumludur ve ayrıca ön derleme önbelleğini yönetir. Bu, `import` ifadesinin bir uygulamasıdır.

## Experimental features

Aşağıdaki özellikler deneysel olup, stabil Julia API'sinin bir parçası değildir. Bunlara dayanarak bir şey inşa etmeden önce, mevcut düşünce hakkında bilgi edinin ve bunların yakında değişip değişmeyeceğini kontrol edin.

### Package loading callbacks

`Base.require` tarafından yüklenen paketleri dinlemek, bir geri çağırma kaydederek mümkündür.

```julia
loaded_packages = Base.PkgId[]
callback = (pkg::Base.PkgId) -> push!(loaded_packages, pkg)
push!(Base.package_callbacks, callback)
```

Bunu kullanmak şöyle görünecek:

```julia-repl
julia> using Example

julia> loaded_packages
1-element Vector{Base.PkgId}:
 Example [7876af07-990d-54b4-ab0e-23690620f79a]
```
