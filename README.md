# tsugumi-vm

Tsugumi の Mac アプリが使う共有 VM（Linux, aarch64）の**ベース**のビルド済みイメージを置くだけのリポジトリです。

ベースは nixpkgs のソフトウェアだけでできています（カーネル、Nix、bash、coreutils、bubblewrap など）。Tsugumi 自身（tsugumid など）は含まず、アプリが別のディスク（レイヤー）として上に重ねます。

各リリースには次の 4 つのファイルがあります。

| ファイル | 中身 |
| --- | --- |
| `vmlinux` | カーネル |
| `rootfs.erofs` | 読み取り専用のルートファイルシステム（/init と nixpkgs の closure） |
| `base-version` | Nix のストアパスの名前（`<hash>-tsugumi-vm-base-<n>`） |
| `SHA256SUMS` | 上の 3 つの SHA-256 |

タグはストアパスのハッシュ部分です。ベースの定義か nixpkgs の固定が変わったときだけ、新しいリリースになります。

含まれる各ソフトウェアのライセンスとソースは、nixpkgs の各パッケージの定義に従います。
