```
LibGit2.SignatureStruct
```

Bir eylem imzası (örneğin, taahhüt edenler, etiketleyenler vb.). [`git_signature`](https://libgit2.org/libgit2/#HEAD/type/git_signature) yapısıyla eşleşir.

Alanlar şunları temsil eder:

  * `name`: Taahhüt edenin veya taahhütün yazarının tam adı.
  * `email`: Taahhüt eden/yazar ile iletişim kurulabilecek e-posta.
  * `when`: Taahhütün depo içine yazıldığı/taahhüt edildiği zamanı belirten bir [`TimeStruct`](@ref).
