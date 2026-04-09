BusyBoxのビルド時に生成された `_install` ディレクトリの直下に `init` ファイルを配置し、任意のシェルスクリプトを記述する。

例として、プロセスディレクトリなどを仮想ディレクトリでマウントするなどの設定を記述する場合を列挙する
```
#!/bin/sh
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devtmpfs none /dev

exec /bin/sh
```

### 注意点
- 最後に `exec /bin/sh` を書かないとシェル環境に入れない。
- `/proc`, `/sys`, `/dev` にそれぞれマウントしているため、cpio アーカイブにそれらのディレクトリを含める必要がある。
- 当たり前だが `/init` ファイルに実行権限を付けないと動かない。（1敗）