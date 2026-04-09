[[インストール方法#GRUBのインストール]] にて、使用した `grub-install` コマンドについての詳細を説明する。

```
sudo grub-install --target=x86_64-efi --efi-directory=/mnt/boot/efi --boot-directory=/mnt/boot --removable
```

`--target=x86_64-efi`
- GRUBをどの形式でインストールするかを指定。
- 64bit の UEFI 用

---

`--efi-directory=/mnt/boot/efi`
- UEFIファームウェアがブートローダーを探しに行くディレクトリを指定。
- ここに `EFI/BOOT/BOOTX64.EFI` というファイルが配置される。
- ディレクトリはFAT32でフォーマットされた [[EFI System Partition]] をマウントした場所をしていする。

---

`--boot-directory=/mnt/boot`
- GRUBの設定ファイルなどを置く場所を指定
- ここに `grub/` ディレクトリが作成される。

---

`--removable`
- USBメモリなど取り外し可能なメディア用のオプション
- これを付けると `EFI/BOOT/BOOTX64.EFI` という標準パスにインストールされる。
- 