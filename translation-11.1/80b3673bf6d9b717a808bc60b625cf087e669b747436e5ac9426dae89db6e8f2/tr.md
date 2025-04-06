```
eigen(A; permute::Bool=true, scale::Bool=true, sortby) -> Eigen
```

`A`'nın özdeğer ayrıştırmasını hesaplar ve özdeğerleri `F.values` içinde ve özvektörleri matris `F.vectors`'ın sütunlarında içeren bir [`Eigen`](@ref) faktörizasyon nesnesi `F` döner. Bu, `Ax =  λx` biçiminde bir özdeğer problemini çözmekle ilgilidir; burada `A` bir matris, `x` bir özvektör ve `λ` bir özdeğerdir. (`k`'nci özvektör `F.vectors[:, k]` diliminden elde edilebilir.)

Ayrıştırmayı yinelemek, `F.values` ve `F.vectors` bileşenlerini üretir.

`Eigen` nesneleri için aşağıdaki fonksiyonlar mevcuttur: [`inv`](@ref), [`det`](@ref) ve [`isposdef`](@ref).

Genel simetrik olmayan matrisler için, özvektör hesaplamasından önce matrisin nasıl dengeleneceğini belirtmek mümkündür. `permute=true` seçeneği, matrisin üst üçgen forma daha yakın hale gelmesi için permütasyon yapar ve `scale=true` seçeneği, matrisin satır ve sütunlarının norm açısından daha eşit hale gelmesi için matrisin köşegen elemanlarıyla ölçeklenmesini sağlar. Her iki seçenek için varsayılan değer `true`'dur.

Varsayılan olarak, özdeğerler ve vektörler `(real(λ),imag(λ))` açısından leksikografik olarak sıralanır. `sortby`'ye farklı bir karşılaştırma fonksiyonu `by(λ)` geçirilebilir veya özdeğerleri rastgele bir sırada bırakmak için `sortby=nothing` geçilebilir. Bazı özel matris türleri (örneğin, [`Diagonal`](@ref) veya [`SymTridiagonal`](@ref)) kendi sıralama kuralını uygulayabilir ve `sortby` anahtar kelimesini kabul etmeyebilir.

# Örnekler

```jldoctest
julia> F = eigen([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
3-element Vector{Float64}:
  1.0
  3.0
 18.0
vectors:
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> F.values
3-element Vector{Float64}:
  1.0
  3.0
 18.0

julia> F.vectors
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
