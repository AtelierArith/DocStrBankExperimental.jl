```
Profile.take_heap_snapshot(filepath::String, all_one::Bool=false, streaming=false)
Profile.take_heap_snapshot(all_one::Bool=false; dir::String, streaming=false)
```

Yığın anlık görüntüsünü, Chrome Devtools Yığın Anlık Görüntüleyici tarafından beklenen JSON formatında (.heapsnapshot uzantısı) bir dosyaya (`$pid_$timestamp.heapsnapshot`) varsayılan olarak geçerli dizine (veya geçerli dizin yazılabilir değilse tempdir'e) yazın, veya verilen `dir`'e, veya verilen tam dosya yoluna, veya IO akışına.

Eğer `all_one` true ise, o zaman her nesnenin boyutunu bir olarak rapor edin, böylece kolayca sayılabilirler. Aksi takdirde, gerçek boyutu rapor edin.

Eğer `streaming` true ise, anlık görüntü verilerini dört dosyaya akıtarak, filepath'ı ön ek olarak kullanarak, tüm anlık görüntüyü bellekte tutmak zorunda kalmamak için bu seçeneği kullanacağız. Bu dosyalar daha sonra `Profile.HeapSnapshot.assemble_snapshot()` çağrılarak birleştirilebilir, bu işlem çevrimdışı yapılabilir.

NOT: Performans nedenleriyle `streaming=true` ayarını yapmanızı şiddetle tavsiye ederiz. Parçaları birleştirerek anlık görüntüyü yeniden oluşturmak, tüm anlık görüntüyü bellekte tutmayı gerektirir, bu nedenle anlık görüntü büyükse, işlenirken belleğiniz tükenebilir. Akış, anlık görüntüyü çevrimdışı olarak, iş yükünüz çalışmayı bitirdikten sonra yeniden oluşturmanıza olanak tanır. Eğer `streaming=false` (geriye dönük uyumluluk için varsayılan) ile bir anlık görüntü toplamaya çalışırsanız ve işleminiz sonlandırılırsa, bu her zaman sağladığınız dosya yoluyla aynı dizine parçaları kaydedecektir, böylece `assemble_snapshot()` aracılığıyla sonradan anlık görüntüyü yeniden oluşturabilirsiniz.
