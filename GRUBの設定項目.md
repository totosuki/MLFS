### 現在の設定
```
set timeout=5
set default=0

menuentry "My Linux" {
    echo "START LOADING LINUX KERNEL!!!!!"
    linux /vmlinuz rdinit=/init
    initrd /rootfs.img
}
```

---

- `grub-install` の `--boot-directory` のパスをルートとする。
- Linux パラメータは https://www.kernel.org/doc/html/latest/admin-guide/kernel-parameters.html にて公開されている。

---

`set timeout=5`
ユーザーが操作せずにタイムアウトする秒数。タイムアウトした場合デフォルトのブートエントリーが起動される。

`set default=0`
デフォルトのブートエントリーの指定。

`menuentry "My Linux"`
`My Linux` という名前のブートエントリーを作成している。

`echo ...`
シェルの `echo` コマンドと同等

`linux /vmlinuz rdinit=/init`
Linux Kernel イメージのファイルパスを指定している。
`rdinit` パラメータにより [[initramfs]] の起動時に実行するシェルスクリプトを指定できる。

`initrd /rootfs.img`
BusyBoxで作成した initramfs（[[rootfs]] 兼用）の cpio アーカイブ。

# 参考

> Arch Wiki
> https://wiki.archlinux.jp/index.php/GRUB