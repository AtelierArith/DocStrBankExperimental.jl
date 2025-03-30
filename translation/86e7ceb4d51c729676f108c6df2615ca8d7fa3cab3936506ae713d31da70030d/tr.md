```
retrieve(; kwargs...) -> data, lidict
```

"Exports" profil sonuçlarını taşınabilir bir formatta döndürür, tüm geri izleme kümesini (`data`) ve `data` içindeki (oturum-spesifik) talimat işaretçilerini `LineInfo` değerlerine eşleyen bir sözlük döndürür; bu değerler dosya adı, fonksiyon adı ve satır numarasını saklar. Bu fonksiyon, profil sonuçlarını gelecekteki analizler için kaydetmenizi sağlar.
