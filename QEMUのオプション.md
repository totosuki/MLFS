今回は x86_64 の Linux Kernel 起動テスト用に使用するオプションをメインに紹介する。

基本的なコマンドは以下のような形。
```
qemu-system-x86_64 -kernel bzImage -initrd rootfs.img -nographic -append "console=ttyS0"
```

- `-kernel <PATH>` : ビルドしたカーネルイメージ
- `-initrd <PATH>` : BusyBoxで作成した initramfs
- `-append "..."` : カーネルコマンドライン引数。`console=ttyS0` でシリアル出力。`root=/dev/sda` でルートデバイス指定など。
- `-nographic` : ターミナルの端末上にQEMUの端末の出力を表示できる。
- `-m 512` : メモリ量(MB)
- `-smp 2` : CPU数
