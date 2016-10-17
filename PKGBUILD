# Maintainer: Jeffrey Phillips Freeman <jeffrey.freeman@syncleus.com>

pkgname=aparapi
pkgver=1.0.0
pkgrel=2
pkgdesc="Syncleus's GPGPU API for data parallel Java using OpenCL."
url="https://github.com/Syncleus/aparapi-jni"
arch=('i686' 'x86_64')
license=('Apache')
depends=('java-environment')
makedepends=('gzip')
provides=('aparapi')
install='aparapi.install'

source=( 'aparapi.sh')
md5sums=('39b6041f8009694d208795cbfcff164e')

source+=( 'aparapi.conf')
md5sums+=('d17068edb75da65a7ef620cbd1c876d4')

source+=(https://github.com/Syncleus/aparapi-jni/releases/download/v${pkgver}/libaparapi-${pkgver}-linux.tar.gz)
md5sums+=('cc28497f3befd355e4636c333ac6b9ab')

package() {
	mkdir -p "$pkgdir"/{opt/aparapi/lib,etc/profile.d,etc/ld.so.conf.d}
	cd ${srcdir}
	install -m755 aparapi.sh "$pkgdir/etc/profile.d/"
	cd ${srcdir}
	install -m644 aparapi.conf "$pkgdir/etc/ld.so.conf.d/"

      cd libaparapi-${pkgver}
      if [ "${CARCH}" = "i686" ]; then
	install -m755 libaparapi_x86.so "$pkgdir/opt/aparapi/lib"
      elif [ "${CARCH}" = "x86_64" ]; then
	install -m755 libaparapi_x86_64.so "$pkgdir/opt/aparapi/lib"
      fi
} 
