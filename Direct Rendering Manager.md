DRM（Direct Rendering Manageer）は、Linuxカーネルの中でGPUやディスプレイを管理するサブシステム。

もともと Linux では、画面描画にフレームバッファ（`CONFIG_FB`）を使用していたが、GPUの高度化に伴い、より柔軟なDRMに置き換わった。

[[実機でPCが起動しない]] では、`.config` の `CONFIG_DRM_EFIDRM` 設定を Enabled にすることで使用することしている。