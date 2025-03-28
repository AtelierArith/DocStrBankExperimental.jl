```
Profile.take_heap_snapshot(filepath::String, all_one::Bool=false, streaming=false)
Profile.take_heap_snapshot(all_one::Bool=false; dir::String, streaming=false)
```

Schreiben Sie einen Snapshot des Heaps im JSON-Format, das vom Chrome Devtools Heap Snapshot Viewer (.heapsnapshot-Erweiterung) erwartet wird, in eine Datei (`$pid_$timestamp.heapsnapshot`) im aktuellen Verzeichnis standardmäßig (oder tempdir, wenn das aktuelle Verzeichnis nicht beschreibbar ist), oder in `dir`, wenn angegeben, oder den angegebenen vollständigen Dateipfad oder IO-Stream.

Wenn `all_one` wahr ist, berichten Sie die Größe jedes Objekts als eins, damit sie leicht gezählt werden können. Andernfalls berichten Sie die tatsächliche Größe.

Wenn `streaming` wahr ist, streamen wir die Snapshot-Daten in vier Dateien, wobei filepath als Präfix verwendet wird, um zu vermeiden, dass der gesamte Snapshot im Speicher gehalten werden muss. Diese Option sollte für jede Einstellung verwendet werden, bei der Ihr Speicher begrenzt ist. Diese Dateien können dann durch Aufrufen von Profile.HeapSnapshot.assemble_snapshot() wieder zusammengesetzt werden, was offline erfolgen kann.

HINWEIS: Wir empfehlen dringend, streaming=true aus Leistungsgründen einzustellen. Das Rekonstruieren des Snapshots aus den Teilen erfordert, dass der gesamte Snapshot im Speicher gehalten wird. Wenn der Snapshot also groß ist, können Sie beim Verarbeiten des Snapshots ohne Speicherplatz dastehen. Streaming ermöglicht es Ihnen, den Snapshot offline zu rekonstruieren, nachdem Ihre Arbeitslast abgeschlossen ist. Wenn Sie versuchen, einen Snapshot mit streaming=false (dem Standardwert, um die Abwärtskompatibilität zu gewährleisten) zu sammeln und Ihr Prozess beendet wird, beachten Sie, dass dies immer die Teile im selben Verzeichnis wie Ihren angegebenen Dateipfad speichert, sodass Sie den Snapshot nachträglich über `assemble_snapshot()` rekonstruieren können. ```
