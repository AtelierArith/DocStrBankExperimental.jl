`AbstractString` türü, Julia'daki tüm string uygulamalarının süpertipidir. Stringler, `AbstractChar` türü tarafından temsil edilen [Unicode](https://unicode.org/) kod noktalarının dizilerinin kodlamalarıdır. Julia, stringler hakkında birkaç varsayımda bulunur:

  * Stringler, sabit boyutlu "kod birimleri" açısından kodlanmıştır.

      * Kod birimleri `codeunit(s, i)` ile çıkarılabilir
      * İlk kod biriminin indeksi `1`'dir
      * Son kod biriminin indeksi `ncodeunits(s)`'dir
      * `1 ≤ i ≤ ncodeunits(s)` koşulunu sağlayan herhangi bir indeks `geçerlidir`
  * String indeksleme, bu kod birimleri açısından yapılır:

      * Karakterler, geçerli bir string indeksi `i` ile `s[i]` ile çıkarılır
      * Bir stringdeki her `AbstractChar`, bir veya daha fazla kod birimi ile kodlanmıştır
      * Bir `AbstractChar`'ın ilk kod biriminin indeksi geçerli bir indekstir
      * Bir `AbstractChar`'ın kodlaması, öncesinde veya sonrasında ne olduğundan bağımsızdır
      * String kodlamaları [kendinden senkronize](https://en.wikipedia.org/wiki/Self-synchronizing_code)dir – yani `isvalid(s, i)` O(1) zaman karmaşıklığına sahiptir

Kod birimlerini, karakterleri veya stringlerden alt dizeleri çıkaran bazı string fonksiyonları, onlara geçersiz veya sınır dışı string indeksleri verirseniz hata verir. Bu, `codeunit(s, i)` ve `s[i]`'yi içerir. String indeks aritmetiği yapan fonksiyonlar, indeksleme konusunda daha rahat bir yaklaşım benimser ve sınır içindeyken size en yakın geçerli string indeksini verir veya sınır dışındayken, stringin her iki tarafında sonsuz sayıda karakter varmış gibi davranır. Genellikle bu hayali dolgu karakterlerinin kod birimi uzunluğu `1`'dir, ancak string türleri, uygulamaları için mantıklı olan farklı "hayali" karakter boyutlarını seçebilir (örneğin, alt dizeler, indeks aritmetiğini sağladıkları altındaki stringe iletebilir). Rahat indeksleme fonksiyonları, indeks aritmetiği için tasarlanmış olanları içerir: `thisind`, `nextind` ve `prevind`. Bu model, bir karakter almak için asla kullanılmadığı sürece, sınır dışı indekslerle ara değerler olarak çalışacak şekilde indeks aritmetiğinin çalışmasına olanak tanır; bu genellikle kenar durumları etrafında kod yazma gereksinimini azaltmaya yardımcı olur.

Ayrıca [`codeunit`](@ref), [`ncodeunits`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref) bakın.
