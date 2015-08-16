# $Id$
# Maintainer : Martin Wimpress <code@flexion.org>
# Contributor: GGR <gaby.greboval at yahoo dot com>

pkgname=mx
pkgver=1.4.7
pkgrel=3
pkgdesc="A widget toolkit using Clutter"
arch=('i686' 'x86_64')
url="http://www.clutter-project.org"
license=('LGPL')
depends=('clutter' 'dbus-glib' 'gtk2' 'startup-notification')
makedepends=('gobject-introspection' 'gtk-doc' 'intltool' 'libtool' 'vala')
source=("https://github.com/clutter-project/${pkgname}/archive/${pkgver}.tar.gz")
sha256sums=('8a7514ea33c1dec7251d0141e24a702e7701dc9f00348cbcf1816925b7f74dbc')

prepare() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    NOCONFIGURE=1 ./autogen.sh
    # patch to resolv GL errors
    # source : https://github.com/clutter-project/mx/pull/62
    sed -i 's/GLushort/gushort/g' mx/mx-deform-texture.c
    sed -i 's/GLfloat/gfloat/g' mx/mx-texture-frame.c
}

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    ./configure \
        --prefix=/usr
    make
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    make DESTDIR="${pkgdir}" install
}
