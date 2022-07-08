# Maintainer: Hoàng Văn Khải <hvksmr1996@gmail.com>

pkgname='nottetris2'
pkgver='2.0'
pkgrel='1'
pkgdesc='Tetris but with too much physics'
depends=('love07' 'bash')
arch=('x86_64')
_repo='https://github.com/Stabyourself/nottetris2'
_commit='62c05953341b74f601d7f0003529fab9764a166b'
url=$_repo
license=('MIT')
source=(
  "$_repo/archive/$_commit.zip"
  "$_repo/raw/$_commit/LICENSE.txt"
  nottetris2.desktop
)
sha1sums=(
  'SKIP'
  'SKIP'
  'SKIP'
)

package() {
  _data_dir="$pkgdir/usr/share/nottetris2"
  _exec_file="$pkgdir/usr/bin/nottetris2"
  _desktop_file="$pkgdir/usr/share/applications/nottetris2.desktop"
  _license_file="$pkgdir/usr/share/licenses/nottetris2/LICENSE.txt"

  mkdir -p "$_data_dir"
  (
    cd "$srcdir/nottetris2-$_commit"
    cp -r . "$_data_dir"
  )

  mkdir -p "$(dirname "$_exec_file")"
  (
    echo '#!/bin/bash'
    echo 'set -o errexit -o pipefail -o nounset'
    echo "cd $_data_dir"
    echo 'exec love07 .'
  ) >"$_exec_file"
  chmod +x "$_exec_file"

  install -Dm755 "$srcdir/nottetris2.desktop" "$_desktop_file"
  install -Dm644 "$srcdir/LICENSE.txt" "$_license_file"
}
