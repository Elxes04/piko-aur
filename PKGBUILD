# Maintainer: Elxes04 <elxes04@example.com>
pkgname=piko
pkgver=1.1.0
pkgrel=1
pkgdesc="A minimal, customizable system information tool written in Rust — inspired by Neofetch"
arch=('x86_64' 'aarch64')
url="https://github.com/Elxes04/piko"
license=('MIT')
depends=('glibc')
makedepends=('rust' 'cargo')
source=("$pkgname-$pkgver.tar.gz::https://github.com/Elxes04/Piko/archive/main.tar.gz")
sha256sums=('SKIP')

build() {
  cd "Piko-main"
  cargo build --release --locked
}

check() {
  cd "Piko-main"
  cargo test --release --locked
}

package() {
  cd "Piko-main"
  
  # Install binary
  install -Dm755 "target/release/$pkgname" "$pkgdir/usr/bin/$pkgname"
  
  # Install configuration files
  install -Dm644 "config/default_config.toml" "$pkgdir/etc/piko/default_config.toml"
  install -Dm644 "config/pastel_config.toml" "$pkgdir/etc/piko/pastel_config.toml"
  install -Dm644 "config/dark_config.toml" "$pkgdir/etc/piko/dark_config.toml"
  install -Dm644 "config/compact_config.toml" "$pkgdir/etc/piko/compact_config.toml"
  install -Dm644 "config/border_config.toml" "$pkgdir/etc/piko/border_config.toml"
  
  # Install documentation
  install -Dm644 "README.md" "$pkgdir/usr/share/doc/$pkgname/README.md"
  install -Dm644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -Dm644 "config/COLOR_SCHEMES.md" "$pkgdir/usr/share/doc/$pkgname/COLOR_SCHEMES.md"
  
  # Install shell completion (if available)
  # install -Dm644 "target/release/build/$pkgname-*/out/$pkgname.bash" "$pkgdir/usr/share/bash-completion/completions/$pkgname"
  # install -Dm644 "target/release/build/$pkgname-*/out/_$pkgname" "$pkgdir/usr/share/zsh/site-functions/_$pkgname"
}
