ログイン中のユーザー情報を開示する `w` コマンドを実行しても値が出力されないという問題がある。
```
$ w
USER            TTY             IDLE    TIME             HOST
```

### 修正方法
`/var/log/wtmp` と `/var/run/utmp` が存在しないから。`w` コマンドは、これらのファイルを読んでログイン中のユーザーを表示する。
ちなみに、`/var` ディレクトリは「可変データ（VARiable data）」を置く場所。

そのため、`/init` スクリプトで空のファイルを事前に作成する。
```
mkdir -p /var/log /var/run
touch /var/log/wtmp
touch /var/run/utmp
```