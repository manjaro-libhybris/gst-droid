# Maintainer: Bardia Moshiri <fakeshell@bardia.tech>

pkgname=gst-droid
pkgver=0.20221003.0+1
pkgrel=2
_commit=af769c1f513336cf3c0deec82690f3047e42e04a
pkgdesc="Android specific GStreamer plugin"
url="https://github.com/droidian/gst-droid"
license=("GPL2" "LGPL-2.1")
arch=('i686' 'x86_64' 'armv6h' 'armv7h' 'aarch64')
depends=('nemo-gst-interfaces')
makedepends=('meson' 'git' 'nemo-gst-interfaces' 'libhybris' 'libexif' 'droidmedia' 'gst-plugins-bad-hybris')
source=("git+https://github.com/droidian/gst-droid#commit=${_commit}")
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}/${pkgname}"
  git describe --tags | sed 's/^v//;s/-/+/g;s|pureos/||g;s|droidian/||g;s|bookworm/||g'
}

build() {
  rm -rf build
  arch-meson "${srcdir}/${pkgname}" build
  ninja -C build
}

package() {
  DESTDIR="${pkgdir}" ninja -C build install
}
