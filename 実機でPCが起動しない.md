# やったこと
- QEMUで同様の `bzImage` `rootfs.img` で起動できることの確認。
- `/boot/grub/grub.cfg` の linux 句に `console=tty0` を追加。
- 以下の 3 つのドライバをインストールした。

1. CONFIG_DRM_EFIDRM : UEFIのフレームバッファを画面出力して使うドライバ
2. CONFIG_DRM_FBDEV_EMULATION : 上記の [[Direct Rendering Manager]] ドライバを、従来のフレームバッファとしてアプリやコンソールから使えるようにする互換レイヤー
3. CONFIG_SYSFB_SIMPLEFB : UEFIが初期化した画面情報をカーネルに引き継ぐ仕組み

`sed` コマンドで `.config` を書き換える場合は以下の通り。
```
sed -i 's/# CONFIG_DRM_FBDEV_EMULATION is not set/CONFIG_DRM_FBDEV_EMULATION=y/' .config
sed -i 's/# CONFIG_DRM_EFIDRM is not set/CONFIG_DRM_EFIDRM=y/' .config
sed -i 's/# CONFIG_SYSFB_SIMPLEFB is not set/CONFIG_SYSFB_SIMPLEFB=y/' .config
```

```
grep -E "CONFIG_DRM_FBDEV_EMULATION=|CONFIG_DRM_EFIDRM=|CONFIG_SYSFB_SIMPLEFB=|CONFIG_FRAMEBUFFER_CONSOLE=" .config
```

で全ての設定が `y` となっていれば設定が完了されている。
ここで動作した。

# カーネルオプションの確認方法
- `make menuconfig` 内のオプションを一つづつ HELP を見る。
- `grep -r "config <CONFIG NAME>" drivers/ で該当の `Kconfig` ファイルを見つけて読む。

