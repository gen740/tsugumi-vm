# tsugumi-vm

Tsugumi の Mac アプリが使う共有 VM（Linux, aarch64）のビルド済みイメージを置くだけのリポジトリです。

各リリースには次の 4 つのファイルがあります。

| ファイル | 中身 |
| --- | --- |
| `vmlinux` | カーネル |
| `rootfs.erofs` | 読み取り専用のルートファイルシステム（tsugumid / tsugumi-vmd と Nix の closure） |
| `vm-version` | Nix のストアパスの名前（`<hash>-tsugumi-vm-<version>`） |
| `SHA256SUMS` | 上の 3 つの SHA-256 |

タグはストアパスのハッシュ部分です。Tsugumi の `macOS/Container/build-image.sh --vm` は、`nix eval` で求めたハッシュのリリースがあればそれをダウンロードし、なければ手元でビルドします。

イメージは nixpkgs（Tsugumi の `flake.lock` で固定）からビルドしています。含まれる各ソフトウェアのライセンスとソースは nixpkgs の各パッケージの定義に従います。
