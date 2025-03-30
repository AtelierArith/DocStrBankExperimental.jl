```
LOAD_PATH
```

`using` ve `import` ifadeleri için proje ortamları veya paket dizinleri olarak kod yüklerken dikkate alınacak yolların bir dizisidir. Ayarlandığında [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) ortam değişkenine dayalı olarak doldurulur; aksi takdirde varsayılan olarak `["@", "@v#.#", "@stdlib"]` değerini alır. `@` ile başlayan girişlerin özel anlamları vardır:

  * `@`, "geçerli aktif ortamı" ifade eder; bu ortamın başlangıç değeri, başlangıçta [`JULIA_PROJECT`](@ref JULIA_PROJECT) ortam değişkeni veya `--project` komut satırı seçeneği ile belirlenir.
  * `@stdlib`, mevcut Julia kurulumunun standart kütüphane dizininin mutlak yoluna genişler.
  * `@name`, depolar altında saklanan adlandırılmış bir ortamı ifade eder (bkz. [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH)) `environments` alt dizininde. Kullanıcının adlandırılmış ortamları `~/.julia/environments` dizininde saklanır, bu nedenle `@name`, `~/.julia/environments/name` dizinindeki ortamı ifade eder, eğer bu dizin mevcutsa ve bir `Project.toml` dosyası içeriyorsa. Eğer `name` `#` karakterleri içeriyorsa, bu karakterler Julia sürüm numarasının ana, küçük ve yaman bileşenleri ile değiştirilir. Örneğin, Julia 1.2 çalıştırıyorsanız, `@v#.#` `@v1.2` olarak genişler ve genellikle `~/.julia/environments/v1.2` dizininde bu isimde bir ortam arar.

Projeler ve paketler için aranan `LOAD_PATH`'ın tam genişletilmiş değeri, `Base.load_path()` fonksiyonu çağrılarak görülebilir.

Ayrıca bkz. [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH), [`JULIA_PROJECT`](@ref JULIA_PROJECT), [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) ve [Kod Yükleme](@ref code-loading).
