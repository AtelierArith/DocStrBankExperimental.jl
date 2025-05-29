```
YAML
```

YAMLを読み書きするためのパッケージです。 https://github.com/JuliaData/YAML.jl

読み取り:

  * `YAML.load` はYAMLファイルの最初のYAMLドキュメントをJuliaオブジェクトとして解析します。
  * `YAML.load_all` はYAMLファイルのすべてのYAMLドキュメントを解析します。
  * `YAML.load_file` は `YAML.load` と同じですが、ファイルから読み取ります。
  * `YAML.load_all_file` は `YAML.load_all` と同じですが、ファイルから読み取ります。

書き込み:

  * `YAML.write` はJuliaオブジェクトをYAMLファイルとして出力します。
  * `YAML.write_file` は `YAML.write` と同じですが、ファイルに書き込みます。
  * `YAML.yaml` は指定されたJuliaオブジェクトをYAML形式の文字列に変換します。
