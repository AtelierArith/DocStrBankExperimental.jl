```
tree_hash([ predicate, ] tarball;
          [ algorithm = "git-sha1", ]
          [ skip_empty = false ]) -> hash::String

    predicate  :: Header --> Bool
    tarball    :: Union{AbstractString, AbstractCmd, IO}
    algorithm  :: AbstractString
    skip_empty :: Bool
```

Bir tarball'ın içerdiği dosya ağacı için bir ağaç hash değeri hesaplayın. Varsayılan olarak, bu, git'in ağaç hashleme algoritmasını ve SHA1 güvenli hash fonksiyonunu kullanır (mevcut git sürümleri gibi). Bu, git'in temsil edebileceği herhangi bir tarball için—yani yalnızca dosyalar, sembolik bağlantılar ve boş olmayan dizinler içeren bir tarball için—bu işlev tarafından hesaplanan hash değerinin, o dosya ağacı için git'in hesaplayacağı hash değeriyle aynı olacağı anlamına gelir. Tarball'ların, git'in depolayamayacağı boş dizinler içeren dosya ağaçlarını temsil edebileceğini unutmayın ve bu işlev, varsayılan olarak (aşağıda `skip_empty`'e bakın, bu davranışı nasıl değiştireceğiniz hakkında), bu boş dizinleri hariç tutan bir tarball'ın hash'inden farklı olacak hash'ler üretebilir. Kısacası, hash fonksiyonu, git'in temsil edebileceği tüm ağaçlarla git ile aynı fikirde, ancak git'in temsil edemediği diğer ağaçlar için hashlenebilir ağaçların alanını (tutarlı bir şekilde) genişletir.

Bir `predicate` işlevi geçildiğinde, bu işlev, `tarball` işlenirken karşılaşılan her `Header` nesnesi üzerinde çağrılır ve yalnızca `predicate(hdr)` doğruysa bir giriş hashlenir. Bu, bir arşivin yalnızca belirli kısımlarını seçerek hashlemek, `extract`'in bir hata fırlatmasına neden olan girişleri atlamak veya hashleme sürecinde neyin çıkarıldığını kaydetmek için kullanılabilir.

`Header` nesnesi, predicate işlevine geçilmeden önce, tarball'daki ham başlıktan biraz değiştirilmiştir: `path` alanı, `.` girişlerini kaldıracak şekilde normalize edilir ve birden fazla ardışık eğik çizgi, tek bir eğik çizgi ile değiştirilir. Girişin türü `:hardlink` ise, bağlantı hedef yolu aynı şekilde normalize edilir, böylece hedef girişin yolu ile eşleşir; boyut alanı, hedef yolun boyutuna (zaten görülmüş bir dosya olmalıdır) ayarlanır.

Şu anda desteklenen `algorithm` değerleri `git-sha1` (varsayılan) ve `git-sha256`'dır; bu, `git-sha1` ile aynı temel algoritmayı kullanır, ancak SHA1 hash fonksiyonunu SHA2-256 ile değiştirir; bu, git'in gelecekte kullanmaya geçeceği hash fonksiyonudur (SHA1 üzerindeki bilinen saldırılar nedeniyle). Gelecekte diğer dosya ağacı hashleme algoritmaları için destek eklenebilir.

`skip_empty` seçeneği, tarball'daki dosya veya sembolik bağlantı içermeyen dizinlerin hash'e dahil edilip edilmeyeceğini veya göz ardı edilip edilmeyeceğini kontrol eder. Genel olarak, bir tarball'ın içeriğini veya bir dosya ağacını hashliyorsanız, tüm dizinlerle ilgilenirsiniz, yalnızca boş olmayanlarla değil, bu nedenle bunların hesaplanan hash'e dahil edilmesi varsayılandır. Peki, bu işlev neden boş dizinleri atlama seçeneği sunuyor? Çünkü git, boş dizinleri depolamayı reddeder ve bunları bir repo'ya eklemeye çalıştığınızda göz ardı eder. Bu nedenle, bir git repo'suna dosyalar ekleyerek bir referans ağaç hash'i hesapladığınızda ve ardından git'ten ağaç hash'ini istediğinizde, elde ettiğiniz hash değeri, `skip_empty=true` ile `tree_hash` tarafından hesaplanan hash değeriyle eşleşecektir. Diğer bir deyişle, bu seçenek, `tree_hash`'ın boş dizinlere sahip bir ağacı nasıl hashleyeceğini taklit etmesine olanak tanır. Ancak, boş dizinler içerebilecek ağaçları hashliyorsanız (yani bir git repo'sundan gelmiyorlarsa), bunları boş dizinleri göz ardı etmeyen bir araç (bu gibi) kullanarak hashlemeniz önerilir.
